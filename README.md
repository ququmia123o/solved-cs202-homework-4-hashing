Download Link: https://assignmentchef.com/product/solved-cs202-homework-4-hashing
<br>
You are asked to implement a class named HashTable that uses a hash table with open addressing to store the items in a data collection. To simplify the implementation, we will consider only integer items where the items themselves are used as the key values.

The items should be stored in an array whose size is given as tableSize when the HashTable object is constructed. You should use the mod operation as the primary hash function:

<h2><em>hash</em>(key) = key mod tableSize</h2>

The HashTable class should support insert, remove, and search operations, and should use a separate function named <em>f </em>as the collision resolution strategy:

<h2><em>h<sub>i</sub></em>(key) = <em>hash</em>(key)+ <em>f</em>(<em>i</em>) mod tableSize</h2>

where <em>h<sub>i </sub></em>is the array index used and <em>i </em>= 0<em>,</em>1<em>,</em>2<em>,… </em>is the iteration number for finding alternative cells in the array. Your implementation should resolve the collisions using linear probing, quadratic probing, and double hashing as follows:

<ul>

 <li>Linear probing: <em>f</em>(<em>i</em>) = <em>i</em></li>

 <li>Quadratic probing: <em>f</em>(<em>i</em>) = <em>i</em><sup>2</sup></li>

 <li>Double hashing: <em>f</em>(<em>i</em>) = <em>i </em> <em>hash</em><sub>2</sub>(key) where <em>hash</em><sub>2</sub>(key) = <em>reverse</em>(key) is the secondary hash function that reverses the digits of the key (e.g., <em>reverse</em>(1234) = 4321).</li>

</ul>

Your implementation should be in the files named HashTable.h and HashTable.cpp. You should define the following enumeration to indicate which collision resolution strategy is used:

enum CollisionStrategy { LINEAR, QUADRATIC, DOUBLE };

Your implementation of the HashTable class should have the following functions:

<ul>

 <li>HashTable::HashTable( const int tableSize, const CollisionStrategy option ); Constructor that initializes the hash table with the given size. The collision resolution strategy is given as an option that will be used in the insert, remove, and search operations.</li>

 <li>HashTable::⇠HashTable();</li>

</ul>

Destructor that cleans up any dynamic memory used.

<ul>

 <li>bool HashTable::insert( const int item );</li>

</ul>

Inserts the given item (also used as the key value) into the hash table, and returns true if insertion is successful, and false otherwise.

<ul>

 <li>bool HashTable::remove( const int item );</li>

</ul>

Removes the given item from the hash table, and returns true if removal is successful, and false otherwise.

<ul>

 <li>bool HashTable::search( const int item, int&amp; numProbes );</li>

</ul>

Searches the given item in the hash table, and returns true if search is successful (i.e., the item is found), and false otherwise. This function also returns the number of probes used during the search for this item.

<ul>

 <li>void HashTable::display();</li>

</ul>

Displays the contents of the hash table in the following format:

0: 1: 39

2:

3: 22

4: 60

5:

…

(In each line, the first value indicates the array index, followed by colon, followed by the item value stored at that index (no item value is shown if the cell is empty).)

<ul>

 <li>void HashTable::analyze( int&amp; numSuccProbes, int&amp; numUnsuccProbes ); Analyzes the current hash table in terms of the average number of probes for successful and unsuccessful searches, and returns these two values in the variables passed by reference. For analyzing the performance for successful searches, you can use the item values currently stored in the table for searching. For analyzing the performance of unsuccessful searches, you can initiate a search that starts at each array location (index), and count the number of probes needed to reach an empty location in the array for each search. Note: You are expected to implement the analysis for both successful and unsuccessful searches for both linear and quadratic probing. For double hashing, you are expected to implement the analysis only for successful searches. You can return -1 for numUnsuccProbes if the collision resolution strategy is selected as DOUBLE. (Exhaustively specifying unsuccessful searches becomes difficult for double hashing because of the use of the keys in the second hash function.)</li>

</ul>

You can define additional functions if necessary.

<h1>Question 2</h1>

Part 1: Describe briefly your design of the HashTable class and how you implement the collision resolution strategies (e.g., how to decide when to stop probing).

Note: You should carefully design the <u>stopping conditions </u>to avoid <u>infinite loops </u>where probing can cycle through the same sequence of array indices even though the hash table is not completely full. You should think about this before actually implementing the methods.

Part 2: Write a driver function (main function) that uses the HashTable class described above and simulates the table operations given in an input text file. The input file should specify table operations in separate lines in the following format:

<table width="592">

 <tbody>

  <tr>

   <td width="93">Operation</td>

   <td width="499">Meaning</td>

  </tr>

  <tr>

   <td width="93">I 1234</td>

   <td width="499">Inserts item 1234 into the hash table. Your driver function should display“1234 inserted” if insertion is successful, and “1234 not inserted” if insertion is unsuccessful.</td>

  </tr>

  <tr>

   <td width="93">R 1234</td>

   <td width="499">Removes item 1234 from the hash table. Your driver function should display “1234 removed” if removal is successful, and “1234 not removed” if removal is unsuccessful.</td>

  </tr>

  <tr>

   <td width="93">S 1234</td>

   <td width="499">Searches item 1234 in the hash table. Your driver function should display “1234 found after 5 probes” if search is successful, and “1234 not found after 8 probes” if search is unsuccessful (numbers just given as examples).</td>

  </tr>

 </tbody>

</table>

Then, prepare an example input text file, and test your HashTable class using a mixed sequence of inputs (insert, remove, search operations) given in this file. Your driver function should call the display function and the analyze function at the end as well. Include the content of your input text file and the corresponding output from the driver function in your report. You should also report the table size used.

Part 3: Compare the empirical performance values (average number of probes for successful and unsuccessful searches as given by the analyze function) and the theoretical average number of probes that can be obtained using the formulas given in the course slides (according to the collision resolution scheme selected and the load factor for the resulting hash table after executing all insert and remove operations specified in the input text file). Briefly discuss your observations.
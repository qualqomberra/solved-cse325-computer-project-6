Download Link: https://assignmentchef.com/product/solved-cse325-computer-project-6
<br>
<h1>Assignment Overview</h1>

<strong> </strong>

For this assignment, you are to design and implement a C/C++ program that uses multi-threading to simulate a simple banking system based on the Producer-Consumer paradigm.




It is worth 40 points (4% of course grade) and must be completed no later than 11:59 PM on Thursday, 2/27.




<h1>Assignment Deliverables</h1>




The deliverables for this assignment are the following files:




<strong>proj06.makefile</strong> – the makefile which produces <strong>proj06</strong> <strong>proj06.student.c</strong> – the source code file for your solution




Be sure to use the specified file names and to submit your files for grading via the CSE Handin system before the project deadline.




<h1>Assignment Specifications</h1>




<ol>

 <li>The program will create P producer threads and one consumer thread which share access to a bounded buffer of size B. The number of producers and the size of the bounded buffer will be available to the program as command-line arguments.  Valid executions of the program might appear as:</li>

</ol>




<strong>proj06 -p 3 -b 10 proj06 -b 5 -p 4 proj06 -b 20 </strong>




The number of producers P will not exceed 10 and will default to 1.  The bounded buffer will be circular and will consist of B records, where B will not exceed 20 and will default to 5.




<ol start="2">

 <li>When the program begins execution, it will read zero or more lines from the input file named “accounts.old” to initialize the set of customer accounts. Each line of that file will contain an account number (integer number) and account balance (real number).  When the program halts execution, it will write the updated set of accounts to the output file named “accounts.new”.</li>

</ol>




<ol start="3">

 <li>Each producer thread will process the transactions which are contained in the input file named “transN”, where N corresponds to the thread number (and thus is between 0 and 9). Each input file will contain zero or more lines, where each line represents a transaction.</li>

</ol>




Each line of an input file will contain an account number (integer number), transaction type (“deposit” or “withdraw”), and transaction amount (real number).  For example, the input file named “trans0” (which will be processed by thread #0) might contain the following lines:




<strong>189348 deposit 1500.00 </strong>

<strong>519783 withdraw 40.00 </strong>




Each producer thread will repeatedly read one transaction from the appropriate input file and then insert one record representing that transaction into the bounded buffer.  After all of the transactions in the appropriate input file have been processed, that producer thread will insert a special record into the bounded buffer to indicate that it is finished processing transactions and will then halt.

<ol start="4">

 <li>The consumer thread will repeatedly extract one transaction record from the bounded buffer, than process it. After all of the producer threads have halted and the bounded buffer is empty, the consumer thread will halt.</li>

</ol>




If the transaction represents a deposit into an account, the consumer thread will add the transaction amount to the account balance.




If the transaction represents a withdrawal from an account, the consumer thread will subtract the transaction amount from the account balance.




The consumer thread will log the results of each transaction by sending one line to the output file named “accounts.log”.  Each line will be no more than 80 characters in length and will contain:




<ol>

 <li>thread number where the transaction originated</li>

 <li>account number</li>

 <li>transaction type</li>

 <li>current account balance</li>

 <li>transaction amount</li>

 <li>updated account balance</li>

</ol>




Those log entries will be appropriately formatted:  items will be aligned in columns, and monetary values will be displayed as dollars and cents (for example, $50.00).




<ol start="5">

 <li>The program will perform appropriate error handling.</li>

</ol>




<h1>Assignment Notes</h1>




<ol>

 <li>As stated above, your source code file will be named “proj06.student.c”.</li>

</ol>




<ol start="2">

 <li>You must use “g++” to translate your source code file in the CSE Linux environment.</li>

</ol>




<ol start="3">

 <li>You must use the POSIX threads library for this assignment. Information about system calls and library functions which might be useful for this project may be viewed using the “man” utility.  For example:</li>

</ol>




<table width="378">

 <tbody>

  <tr>

   <td width="258"><strong>man 3 pthread_create man 3 pthread_join man 3 pthread_exit </strong></td>

   <td width="120"><strong>man 3 sem_init man 3 sem_wait man 3 sem_post </strong></td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<ol start="4">

 <li>You may assume that the lines in the input file named “accounts.old” (if it exists) are formatted correctly and contain valid account numbers and account balances.</li>

</ol>




<ol start="5">

 <li>You may assume that the lines in the input file named “transN” (if it exists) are formatted correctly and contain valid account numbers and transaction types. You may assume that the transaction amounts are positive values.</li>

</ol>




<ol start="6">

 <li>You will model the bounded buffer using an array and you will model one item in the bounded buffer using a record (C/C++ “struct”).</li>

</ol>




<ol start="7">

 <li>You may model the set of customer accounts using any data structure (including data structures from the STL).</li>

</ol>




<ol start="8">

 <li>Each critical section will be kept as small as possible and no I/O operations will be performed inside a critical section.</li>

</ol>



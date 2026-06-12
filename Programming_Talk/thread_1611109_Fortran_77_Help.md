---
title: "Fortran 77 Help"
date: 2010-11-01
forum: Programming Talk
---

### Post by icecoldshakespeare on 2010-11-01
I am completely lost. I am supposed to write a program using Fortran 77 that opens a file and opens other files under the original one and display data according to the user's file name input. Can anyone help? The original problem is:


Description: 

The Wonka Candy Company (home of the famous Gobstopper) receives the sugar they use in their candy in liquid form in railroad tank cars.  They pump the liquid sugar from the tank cars into the factory via a pipeline.  It’s very important to Mr. Wonka’s candy making process to keep the sugar flowing through the pipeline at a constant temperature and pressure. So, Mr. Wonka has a group of his Oompa-Loompas read the temperature and pressure in the pipeline from sensors placed in regular intervals along the pipeline.

Each Oompa-Loompa has a laptop in which they enter readings into a file. The file has one reading per line.  A reading can be in one of two formats: the character P followed by a real number or the character T followed by a real number.  The Oompa-Loompa saves the file using his name as the file name and takes it to Mr. Wonka.   Mr. Wonka then records each Oompa-Loompa’s name in a second file that uses to keep track of the data that has been read.

Write a FORTRAN program that reads the file that Mr. Wonka uses to record the name of each Oompa-Loompa and does the following for each Oompa-Loompa’s data file:
1.	Counts the number of pressure readings (denoted by P in the data file) made by each Ooompa-Loompa.
2.	Counts the number of temperature readings (denoted by a T in the data file) made by each Oompa-Loompa
3.	Calculates the average of all the Oompa-Loompa’s pressure readings.
4.	Calculates the average of all the Oompa-Loompa’s temperature readings.

You will need to use two nested loops to process this data. The outer loop will be responsible for reading the names from Mr. Wonka’s data file or wonka.txt. The inner loop will read the Oompa-Loompa’s data file and calculate the averages.

For a more detailed example, here’s a short program that prompts a user for the name of a text file and then prints the file, this is an example and should not be used as a template for the programming assignment:

*234567
     		 PROGRAM cat
      		CHARACTER*32 fname
		CHARACTER*80 line
     		 INTEGER eof
*     Get the file name
      		PRINT *,'Enter file name:'
     		 READ *,fname
*     Open the file, read a line and display it
*     Keep doing this until you reach the end of file
     		 OPEN (UNIT=12, FILE = fname, STATUS='OLD')
      		READ (12,*,IOSTAT=eof) line
   10   		IF (eof .GE. 0) THEN
         		 PRINT *,line
         		 READ (12,*,IOSTAT=eof) line
          		GO TO 10
      		END IF
      		END

Sample output: 
Here is some sample output of what your program should produce:

Oompa-Loompa: Ernest
Type>>>> Count>>>> Average
============================
Type: P  >>>>  Count :5 >>>> Average:45.00000
Type: T >>>> Count:3 >>>> Average:125.00000
============================

Oompa-Loompa: Verne
============================
Type: P  >>>>  Count : 7  >>>> Average  : 46.00330
Type: T >>>> Count:1  >>>> Average: 125.00330
============================

Oompa-Loompa: Ernestine
============================
Type: P  >>>>  Count : 6 >>>> Average: 45.33333
Type: T >>>> Count: 6   >>>> Average :124.25000
============================


Sample input
The file “wonka.txt” contains the following:

ernest
verne
ernestine

The file “ernest” contains the following readings:
P 45
T 125
P 45
T 125
T 125
P 45
P 45

So, what do you have to do in your program for this assignment?   Your program will need to include two INTEGER variables to be used in IOSTAT clauses in your READ statements. The first variable will be used for the file that Mr. Wonka uses to keep the names of each Oompa-Loompa while the second variable will be used to keep track of the end-of-file each time you process the Oompa-Loompa’s data file.

---

### Post by dwhitney67 on 2010-11-01
No homework!!!

---


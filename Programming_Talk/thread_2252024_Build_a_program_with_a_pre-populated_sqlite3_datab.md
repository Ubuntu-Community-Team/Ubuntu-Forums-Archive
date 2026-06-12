---
title: "Build a program with a pre-populated sqlite3 database"
date: 2014-11-08
forum: Programming Talk
---

### Post by Matthew_Harrop on 2014-11-08
I am building a terminal program in xcode to help me with Kerbal space program and I was hoping I'd be able to get your help/advice.

I want to be able to sim my launches/rendezvous and test to see if they'll work before I undertake them and that requires the program to know all the details about the planets /ships in the game. 

Now, I could write a script in the program to insert all the relevant data into a Sqlite database, where it (Along with information regarding previous burns, simulations and launches) would be contained. This seems rather self defeating as I'd basically be carrying a copy of the data twice (First in the script to put it into the database and then in the database itself) so i was wondering if it were possible to pre-populate the database BEFORE i compile the program and then use the pre-populated database in my program.

The program is written in C++ and am only using Xcode because it was already on my mac.

---

### Post by ofnuts on 2014-11-09
SQLite databases are files. Nothing prevents you from having a first program that creates the database file, and another program that uses it multiple times. You'll also find utilities that allow you to manually edit the SLQLite DB files (including a Firefox extension...), this can remove the need for the first program.

Now trying to wrap my head around the idea of simulating the flights outside of KSP itself...

---

### Post by Matthew_Harrop on 2014-11-09
My problem is getting the file to be included in the program. It doesn't seem to recognise the file that I build it with and, instead, creates it own. 

I wanted to learn about celestial mechanics, and I figure the best way to do that is to write a program where I have to manipulate the mathematics :) - Not only that but I get to learn more about a language I don't get to use very often.

Thank you for your help! It made me re-think how to include files in the project.

EDIT: [http://stackoverflow.com/questions/5287213/how-can-i-build-for-release-distribution-on-the-xcode-4](http://stackoverflow.com/questions/5287213/how-can-i-build-for-release-distribution-on-the-xcode-4) - I just wanted to include this here for future reference. Not to mention using a direct path for the db file.

---


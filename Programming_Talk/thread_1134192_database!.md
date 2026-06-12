---
title: "database!"
date: 2009-04-23
forum: Programming Talk
---

### Post by ayastona on 2009-04-23
c++

Currently i have been taking the information directly entered by a person using my program and having the information printed into a text file... i may have to make it so that i can search for the information later and so i was wondering what is the best way to handle all-text information so that if i do need to recall it i can easily find it..

right now it just seems to me that by simply placing text into the text file, i am setting myself up for disaster in the future when i have alot of information saved.. 
thanks!

---

### Post by dwhitney67 on 2009-04-23
This is the second question you have asked today concerning what seems to be a class project.  How many records to you expect to have?  If it is less than a few thousand, then the data can probably sit in memory.

If you want more capabilities, such as selecting multiple records that share a common attribute value, then go with the database.  Since you are developing in C++, consider using MySQL database and the MySQL++ API for your application.

---

### Post by ayastona on 2009-04-23
i would like to use the information and store it in a daily file.. all the information on all the clients need to be stored in a file for future reference..

i guess it doesnt matter if the program is super complicated.... ... ... ... ... ... yet...

all i need is to like enter a bunch of different data (strings, numbers, etc) and have it all saved together as a packet of information that can be recalled if needed... and that information has to be printed on a physical printer..

your help is greatly appreciated.. please guide me on how to make this..

i have started constructing the barebones for the program and have made "void" functions that basically outlines all the output on the screen for the different functions...

i would like to incorporate the program into visual c++ in the future so that the computer illeterate can not be intimidated by a black command prompt screen to work with...

---

### Post by stevescripts on 2009-04-23
You are talking about a database, in the end.

Also, you are talking about eventually having a GUI (Graphical User Interface) - note visual C++ is a development environment, not a widget set.

I dont mean to discourage you - hang in there!  Folks here will lend a helping hand and guidance.

Steve

---


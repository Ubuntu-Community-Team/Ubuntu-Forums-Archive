---
title: "Program Consuming Large Amount of Memory Crashes Eclipse"
date: 2008-06-06
forum: Programming Talk
---

### Post by DBQ on 2008-06-06
Hi everybody.  I have a java program I wrote and running in eclipse.  The program opens and processes files.  When the files were large I was getting OutOfMemoryException, which I was able to defeat with -Xmx and increasing the heap space.  However, right now with even larger files Eclipse crashes after my program is trying for a little bit to load the file.  Eclipse exits and displays a message box saying basically that the JVM crashed, and eclipse must exit.

Are there any other eclipse/java memory settings I can tweak to solve this problem? I am positive that eclipse crashes as a result of the program somehow still not getting enough memory.  Thank you all!

---

### Post by NormR2 on 2008-06-06
Could you give some more info on your program?
How large are the large files? How much RAM do you have? 
Are you trying to keep all of the data from the file(s) in memory?

Memory is not infinite, you may need to look at your logic to restrict what needs to be kept.

Another way to use up lots of memory is an infinite, recursive loop that builds a call stack that uses up all of memory.

Java has several methods that will display memory usages. Try putting some of those in your program to see how/where memory is being used.  See Runtime freeMemory() and totalMemory()

---

### Post by DBQ on 2008-06-06
My files are not very large.  One of the files is about 57MB, and I am already using the -Xmx2000m option.

---

### Post by NormR2 on 2008-06-06
And if you have 10000 of 57MB files, you'll be using a lot of memory.
Could you be a little more precise on the total size of the files you're trying to read? 
How do the values returned from freeMemory() and totalMemory() change?
Where in you program do you get the OutOfMemory error?

---


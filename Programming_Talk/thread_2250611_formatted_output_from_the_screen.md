---
title: "formatted output from the screen"
date: 2014-10-29
forum: Programming Talk
---

### Post by pauls2 on 2014-10-29
How - using ANSI C - do I save the formatted output on my screen (stdout) to a file and then print a hard copy of it on the printer?

I am using ANSI C for its portability and don't want to lose that possibility.

The stream "stdprn" was used under DOS to access the printer but is there a steam that can be used to send formatted output to the printer?

---

### Post by manngaurav on 2014-11-01
Just press PrtSc(printscreen) key when the output is on whole screen , or the inbuilt screenshot app and copy the image somewhere, by the way are you using an IDE or just the terminal and good old gedit ?

---

### Post by pauls2 on 2014-11-07
Sorry this is so late - I have been very busy and haven't had time until now to get back.

I wasn't very clear in what I wanted to do. I wanted to save a file of the information that would duplicate what I displayed on the screen so I could print it from the file.
I did manage to get it done by appending each printf() statement using fprintf() to a text file. The formatting is completely dependent on the program that reads the txt file and the printer that is used to print. 
It is never the same when using different printers or programs. The information is all there but the allignment of the table varies with the default font and the width of the tabs on the software and the printer.
It is way too late for me to list the code right now but I thought I would let you know that I did get it working. I might be able to get more consistent results across multiple printers and software using spaces instead of tabs but the nice thing is - it can be formatted by the user to fit his or her needs for printing.

---


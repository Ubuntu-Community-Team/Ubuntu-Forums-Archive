---
title: "Java PrintWriter output limitations?"
date: 2009-03-03
forum: Programming Talk
---

### Post by nateperson on 2009-03-03
I'm a fairly new Java programmer, so bare with me a bit. I was using PrintWriter to print my output to a txt file, until I realized that it wasn't always printing out everything, seeming to stop after some limit has been reached, usually between 900 and 1500 lines of text.  I rewrote my code to use FileOutputStream and PrintStream.

I was using PrintWriter by:
> PrintWriter outputFile = new PrintWriter("SomeOutput.txt");
outputFile.prinln("Hello World");

Now I'm printing out by:
> FileOutputStream outputFile = new FileOutputStream("ADiffrentOutput.txt");
		PrintStream printOutput = new PrintStream(outputFile);
printOutput.println("Hello World");

SO, my question is, what was I doing wrong, and am I doing stuff correctly now?  You see, I now have to go back and reprint out my results for the past few weeks/months(hope not) and reanalyze them, and I really don't want to have to do it a 3rd time.

Thanks

Nate

---

### Post by nateperson on 2009-03-03
Oh, I'm using: 32bit
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Server VM (build 10.0-b23, mixed mode)

on a 64bit machine.

Thanks again,

Thomas

---

### Post by digital_x on 2009-03-03
Are you explicitly closing the PrintWriter when you are done using it?  This will flush the buffer.  You can also manually call flush() on the PrintWriter instance.

---

### Post by albandy on 2009-03-03
FileWriter filestream = new FileWriter("file.txt");
 BufferedWriter out = new BufferedWriter(filestream);
 out.write("Hi, I am writing this");
 out.close();

---

### Post by kavon89 on 2009-03-03
> **digital_x said:**
> Are you explicitly closing the PrintWriter when you are done using it?  This will flush the buffer.  You can also manually call flush() on the PrintWriter instance.

Yea make sure you've got a flush() or close() after your prints, PrintWriters don't have automatic flushing unless you use the correct constructor:

> Unlike the PrintStream class, if automatic flushing is enabled it will be done only when one of the println, printf, or format methods is invoked, rather than whenever a newline character happens to be output. These methods use the platform's own notion of line separator rather than the newline character.

---

### Post by nateperson on 2009-03-03
I was doing close() at the end of my program, but all the writing to the file was done in a for loop... after at least 800 iterations, so was filling and stopping writing, before the close().  I didn't think of using the flush(). I can see it now. 

Thanks ya'll!

nate

---


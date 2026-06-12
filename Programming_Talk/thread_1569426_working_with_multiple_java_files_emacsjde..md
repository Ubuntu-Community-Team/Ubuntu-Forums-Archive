---
title: "working with multiple java files emacs/jde."
date: 2010-09-06
forum: Programming Talk
---

### Post by csguy on 2010-09-06
Hello all.

I recently converted to emacs from eclipse for coding in java.  I have emacs installed as well as jde working.
The problem is that when I want to compile a java file that uses a class in another file, the compiler cannot find the class. The two files are:

CallFlowSim.java
Queue.java

and are located in the same directory.  When I compile within emacs I get this compilation error.

 /home/chris/Documents/csc364/CallFlowSim.java
/home/chris/Documents/csc364/CallFlowSim.java:10: cannot find symbol
symbol  : class Queue
location: class CallFlowSim
 Queue calls=new Queue();

So when I compile CallFlowSim.java, it does not know what the Queue class is and a compilation error occurs.  I ran javac CallFlowSim.java in the terminal just to be sure and it compiled without error.
So how do I work with multiple java files in emacs?  

PS
I have tried to find a decent tutorial on project files and JDE with little to no luck. Any help would be appreciated.

---

### Post by GregBrannon on 2010-09-06
I found this guide that shows how to do the same Java programming tasks in Eclipse, the command line, and Emacs:

[http://www.mit.edu/~6.170/tools/editing-compiling.html#compiling-emacs]("http://www.mit.edu/~6.170/tools/editing-compiling.html#compiling-emacs")

but I don't think it answers your question.  As you've discovered yourself, you're doing the right things outside of Emacs.  Doing the right things in Emacs shouldn't require additional effort to be successful.

Are you using "packages?"  I don't know if that matters in Emacs, but it seems that keeping related files in packages might help Emacs keep related source files straight.

When you compile the source files in Emacs, do all of the appropriate *.class files result in the same folder?  If the necessary *.class files are all in the same directory, invoking the java command on the *.class file containing the main() routine should work.

Don't think I've helped, but hopefully I've given you some things to think about.

---


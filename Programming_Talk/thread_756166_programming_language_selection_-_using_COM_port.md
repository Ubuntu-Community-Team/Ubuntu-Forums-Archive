---
title: "programming language selection - using COM port"
date: 2008-04-15
forum: Programming Talk
---

### Post by tmillic on 2008-04-15
I need a little guidance in selecting an approach to using Ubuntu Server as a data logger. I've used Ubuntu Server as our file server and lamp server in our lab, but my experience with programming or creating applications is non-existent. I don't even know what the languages or called or how to implement them. What are some recommendations for a starting point and/or language (if that's applicable) for the following use of Ubuntu Server.
The data will be coming from a Li-Cor LI-840 CO2 gas analyzer over the COM serial port using XML. We intend to use an ITX-based pc for low-power consumption. The data will most likely go into a MySQL database rather than a single large file. Do C++, Python or other languages have the ability to run as an application from startup and communicate over the COM port while connecting to a mysql database? 
I'll probably try and an all recommendations in the lab before hauling the analyzer and car batteries through the Ozarks, deep into some cave. (That's why low CPU utilization/low power is a priority - batteries are heavy!).

If there is a more appropriate place to post this, I apologize.

---

### Post by dwhitney67 on 2008-04-15
With C++, the answer is surely yes.  I have no experience with Python, but I do know that it offers similar building tools.

The C++ Boost libraries have the necessary tools to digest XML data, and using MySQL++ (a C++ interface to the MySQL database), you can issue SQL queries to the database.

As far as opening the comm-port (e.g. /dev/tty01), that's also possible, however because I have not done anything similar to this in over 16 years, I have forgotten all of the details on how to set this up.  But it is doable!  Just Google for a solution.

---

### Post by supirman on 2008-04-16
If you're dealing with just ascii data formatted as XML, then this should end up being quite easy.  Other than a short piece of setup code to properly set the port parity, baud, etc, you can then treat the serial port like a normal file and read a line at a time from it.  

For the most part, you open /dev/ttyS0 (or the number of your serial port) and read() from it.  

If you're not doing anything too complicated with the data after you receive it, writing some C (or python) to dump it to a mysql database should again be rather easy.

For some info:

Canonical input processing on a serial port - to someone unfamiliar with C, this will look very complicated, but it's really not.:
[Link]("http://www.faqs.org/docs/Linux-HOWTO/Serial-Programming-HOWTO.html#AEN125").

Simple mysql example with C:
[Link]("http://www.ucl.ac.uk/is/mysql/c/")

---

### Post by pmasiar on 2008-04-16
because you do not have any programming experience, you need to learn programming first. Python is widely considered as best for beginners. Likely, it has neeed modules (mysql is there), or will have when you learn it enough to be ready to solve your task (it might take you a year or more to become confident programmer, depending on your dedication and time). 

If you don't find needed module, creating one in C and linking it to Python is easier than in other languages, because Python was designed to be extandable this way.

---

### Post by xelapond on 2008-04-16
I second python.  I do serial data logging and analysys much like you do, though i read it line by line and don't save it.  Your code will be up and running faster in python then it would be in C or C++(I hope i don't start a flamewar).  Python is also cross platform, so should you choose to switch it to a Windows or Mac box, it will still run fine.  Also, Python does not need to be compiled, so you will save tons of time not waiting for it to compile then give you an errors.  Also(I could go on forever about the advantages of Python)

Good Luck!

---

### Post by WW on 2008-04-16
+1 for Python.  For the serial port programming, the ubuntu package [python-serial](http://packages.ubuntu.com/gutsy/python-serial) provides the **serial** Python module, if you need it. (I've haven't used it, so this is not really an endorsement of the module, just an "FYI".)

---

### Post by dwhitney67 on 2008-04-16
> **xelapond said:**
> ... Also, Python does not need to be compiled, so you will save tons of time not waiting for it to compile then give you an errors.
...

I'm not looking to start a flame-war either, but this statement that you made is nonsense.  Scripted languages, if poorly written with syntax errors, will also generate warnings/errors when executed.  One will still have to correct these issues in a similar fashion if they had written s/w in C/C++ and the compiler had flagged syntax errors.

---

### Post by xelapond on 2008-04-16
> I'm not looking to start a flame-war either, but this statement that you made is nonsense. Scripted languages, if poorly written with syntax errors, will also generate warnings/errors when executed. One will still have to correct these issues in a similar fashion if they had written s/w in C/C++ and the compiler had flagged syntax errors.

That is true, but we don't need to wait anywhere from 10 minutes to 12 hours for it to give us the errors.

---

### Post by pmasiar on 2008-04-16
> **dwhitney67 said:**
> Scripted languages, if poorly written with syntax errors, will also generate warnings/errors when executed.  One will still have to correct these issues in a similar fashion if they had written s/w in C/C++ and the compiler had flagged syntax errors.

Even simple IDE, like IDLE, will warn about all syntax  errors when parsing source before running it (and they will compile sources to .pyc file, so it does not have to be parsed/compiled next time). Time saving is substantial in POV of psychology: after I made my changes, waiting even for 20 secs before running my code is PITA, and good IDEs (like Eclipse) compile all source changes in backround.

The difference you might be trying to express is difference in handling the type information: dynamically typed languages, like Python, use late binding, and check availability of a method only at runtime. Which of course might cause runtime error if given type lacks requested method. But it also simplifies programming, because any object with requested method is OK, it doe not have to be properly raised via tree of inheritance like in statically typed languages. 

Also, statically checked exceptions, like java has, are major PITA, even if they force "proper" exception handling: they make simple 'throw-away' programs hard to write.

We had this discussion many times, please refer to FAQ sticky about language wars.

---

### Post by tmillic on 2008-04-17
Thanks everybody! 
This is some great information about things I didn't know were out there. 
I'll try Python, C and C++. I do have some programming experience; limited to php, povray and the software controlling our lab's mass spectrometers. 
We have a year before we start carrying batteries through the woods for testing and fixing errors. That should be enough even with my limited programming experience. :-)
Thanks again.

---

### Post by WW on 2008-04-17
I hope you post some updates now and then.  The project sounds fascinating.

---

### Post by tmillic on 2008-04-17
No problem. It will be slow going though. This is one a a few projects we work on on the side of what we get paid to do.

---


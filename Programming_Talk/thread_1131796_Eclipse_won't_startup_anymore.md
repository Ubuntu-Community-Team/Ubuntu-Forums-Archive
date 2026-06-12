---
title: "Eclipse won't startup anymore"
date: 2009-04-21
forum: Programming Talk
---

### Post by Froodolt on 2009-04-21
Hello,

Yesterday I was working in eclipse, all fine. But after I closed eclipse down, it won't start anymore.
The only thing I've done different is that I changed a directory and moved files in my workspace outside of eclipse. 


When I try to run eclipse in terminal it says:
```
$ /home/bas/eclipse/eclipse

LOG: [0xb7dc36b0] exception thrown while VM is initializing: 

LOG: [0xb7dc36b0] NULL: java.lang.Object

LOG: [0xb7dc36b0] Aborting...

Aborted

$ 

```
Changed everything (files, directories) back after eclipse “crashed” on startup, but it still doesn't start up.

I know its an Ubuntu forum and not an eclipse help-desk out here, but I hope someone can help me out.
Anyone an idea what the problem can be?

Thanks in advance!

---

### Post by odyniec on 2009-04-21
Have you tried launching Eclipse with a different workspace location (e.g. an empty directory)? You can specify it on the command line with the -data option.

---

### Post by Froodolt on 2009-04-21
Tried it, but unfortunately it doesn't work, or am I missing something here? :(
First made the directory workspace2 in my home folder.
```
$ /home/bas/eclipse/eclipse -data /home/bas/workspace2

LOG: [0xb7e756b0] exception thrown while VM is initializing: 

LOG: [0xb7e756b0] NULL: java.lang.Object

LOG: [0xb7e756b0] Aborting...

Aborted

```

Other idea's?

---

### Post by Froodolt on 2009-04-21
Going for a reinstall of eclipse, because I have to get my assignments done. :o
Made a backup of my workspace so I must be fine.

Thanks for your try odyniec! ;)

---

### Post by jasonintheuk on 2009-05-13
I too have this problem - I am guessing that the underlying Java VM and/or java.lang.Object are no longer compatible with eclipse. 

Java IDE,  LoL:)

---

### Post by jasonintheuk on 2009-05-13
Hah! 

So the problem for me was because Firefox (come on google where is that linux chrome port) installed IcedTea support via cacoa. The net effect is that the SUN JRE was no longer default.

How to check for this:
# which java #resolves:
/usr/bin/java
# /usr/bin/java -v #resolved:
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu5) Runtime Environment (build 1.6.0_0-b12)
CACAO (build 0.99.3+hg, compiled mode)

Yuk - so in synaptic manager search for icedtea and remove the references (all cacao in my case). I note Ubuntu provides its own IcedTea (but that is for another day).

Then when fininshed, check that sun java is default again
# /usr/bin/java -v # resolves:
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)

WAHOO!!! 

Java is the devil's spawn, trying to spread its evil across the world. A great OO language, used wherever it should not be. Why learn many languages when you can just use one - inapropriately:) I'm surprised Linus hasn't rewritten the kernel in it :) <--- steeped in irony and sarchasm for those that need telling.

---

### Post by SKLP on 2009-05-13
maybe the OP has got this problem: [http://blog.nixternal.com/2009.03.09/jaunty-64-bit-and-eclipse/](http://blog.nixternal.com/2009.03.09/jaunty-64-bit-and-eclipse/)
hope this helps

---

### Post by jespdj on 2009-05-13
First, make sure you are using the right Java runtime environment. Sun Java 6 is the safest. See: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Try starting Eclipse with:
```
eclipse -clean
```
If that does not work, try deleting your ~/.eclipse directory before starting Eclipse. Note that this will delete all your settings and plug-ins that you installed with Eclipse's plug-in manager.

---

### Post by Froodolt on 2009-05-14
> **jasonintheuk said:**
> 
Yuk - so in synaptic manager search for icedtea and remove the references (all cacao in my case). I note Ubuntu provides its own IcedTea (but that is for another day).

Hmmm... you may have a point here... :frown:
Few weeks back I was doing an assignment on servlets...
My firefox didn't want to run them, so I messed a bit round with synaptic manager... :oops:

Thanks, I'll keep this in mind for future servlet adventures... ](*,)

EDIT:
Thanks jespdj,
Found the java configuration as you posted in another thread, and it worked for me.
Much better performance!

---


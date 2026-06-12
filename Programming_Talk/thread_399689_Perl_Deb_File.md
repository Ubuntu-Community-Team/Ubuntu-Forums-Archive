---
title: "Perl Deb File"
date: 2007-04-02
forum: Programming Talk
---

### Post by chamberlain2006 on 2007-04-02
Hi, I wrote a perl script that I want to make into an installable deb file for a few of my friends.  How can i do so?

---

### Post by blanky on 2007-04-02
Heh, debian packing is not a simple thing. You'll have to learn how to package deb's, and unless you're either really skilled at that or your script is really useful, it might not even be worth it. You could simply install the script to /usr/bin or wherever it is these days so they could run it easily, if that's even necessary, but for a simple perl script packaging in deb might seem like overkill.

---

### Post by harun on 2007-04-03
Unless you used some Perl modules your friend may not have, the script will be completely portable on its own and you would be better off to just give them the script.

However if you do want to go through building a .deb to learn how to do it:

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

There may be a better quick start guide out there for if you are only packaging up a Perl program. Which would mean you don't have to worry about all the make files, and the rest of the source code like in their examples.

I have seen many posts say how difficult it is to do a .deb but if you have the endurance to just read through their examples it is not technically hard, just a lot to read.

---

### Post by chamberlain2006 on 2007-04-03
The problem is that my friend is new to Linux/Ubuntu and she still doesn't know where to find the C:/ Drive, so asking her to put it into the "/usr/bin" directory and call it seems a little beyond her.  Thanks for the replies though, I just modified a simple Makefile, and we're good!

---

### Post by blanky on 2007-04-03
There is no "C:\" drive in Linux, haha. Also, instead of telling him/her to move it into /usr/bin or wherever, give her the specific command.

Like sudo mv myscript /usr/bin or something.

---

### Post by WW on 2007-04-11
You could use the program **epm** to create a .deb file.  An example is here: [http://ubuntuforums.org/showthread.php?t=406069](http://ubuntuforums.org/showthread.php?t=406069)

---


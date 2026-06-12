---
title: "a somewhat useful perl script ..."
date: 2006-06-20
forum: Programming Talk
---

### Post by slavik on 2006-06-20
the attached perl script will take a list of all installed packages (dpkg -l), then parse the reverse dependencies of all the installed packages and print all packages without any reverse dependencies.

a reverse dependency is when something else is dependant on the installed package.

example:
pkg A depends on pkg B. pkg A is pkg B's reverse dependency.

It is a good idea to redirect the script output to a file.

NOTE: download the file and change the extension to .pl (to signify that it is a perl script) then make it executable (chmod +x rdepparse.pl) and then run it.

the script will take some time to complete because of the enourmous amount of system calls it does, depending on the number of installed packages.

---

### Post by kb3hkg on 2006-06-20
that is a nice little script you have there.

---

### Post by siccness on 2006-06-20
Hey, that's a great little script. :)

---

### Post by ynef on 2006-06-21
While this is nice and possibly a lot better, you should check out deborphan[1] -- from your description and my memory, I think it does the same. It's also pretty fast, IIRC.

[1] [http://packages.ubuntu.com/dapper/admin/deborphan](http://packages.ubuntu.com/dapper/admin/deborphan)

---

### Post by slavik on 2006-06-21
The reason for the script is because I couldn't get deborphan to work ...

---


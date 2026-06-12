---
title: "Eclipse is not working"
date: 2007-11-20
forum: Programming Talk
---

### Post by terrysun on 2007-11-20
Hi, guys
      There is an error when i try run elicpse. It said "The custom VM you have chosen is not a valid executable" ? wht 's wrong ? Could anyone tell me how to fix this? Thanks!

---

### Post by Hendrixski on 2007-11-20
Are you sure that you have the correct version of the java runtime environment installed?  That's pretty much a vm.

If you installed it from eclipse.org then I guess make sure you linked to the right executable (rather than just copying it or whatever).

Also, usually googling the error message gives you a solution to it.

---

### Post by smartbei on 2007-11-20
Other have been having issues with running eclipse and other java applications these last few days, due to the fact that they are running the GNU java runtime rather than the Sun java runtime. Try this:

```

sudo aptitude install sun-java6-jre

```

That line might be off by a bit - I am not next to my Ubuntu PC to check.

---

### Post by ukripper on 2007-11-20
Guide [https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by everweb on 2010-02-24
I had the same problem and it is now fixed.

When I ran eclipse from the command line it looked like this:
$ eclipse
using specified vm: /usr/lib/jvm/java-6-sun-1.6.0.03/
and it popped up the dialog showing "The custom VM you have chosen is not valid"

When I looked in /usr/lib/jvm it had the following:
lrwxrwxrwx 1 root root   19 2009-12-03 14:39 java-6-sun -> java-6-sun-1.6.0.17
drwxr-xr-x 2 root root 4096 2009-11-27 10:24 java-6-sun-1.6.0.14
drwxr-xr-x 8 root root 4096 2009-12-03 14:39 java-6-sun-1.6.0.17

Note the absence of java-6-sun-1.6.0.03 !

It turns out that I had put my JAVA_HOME setting in /etc/profile:
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03/
export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.03/bin

I have now edited /etc/profile to read:
export JAVA_HOME=/usr/lib/jvm/java-6-sun/
export PATH=$PATH:/usr/lib/jvm/java-6-sun/bin

Then to let the system know I changed it, I typed: 
   . /etc/profile

The result:
$ eclipse
using specified vm: /usr/lib/jvm/java-6-sun/

And eclipse works.

---

### Post by GregBrannon on 2010-02-26
everweb,

Excellent post!

---

### Post by TurnOfTide on 2010-02-26
Very helpful post. New to Linux here and I haven't done anything with eclipse yet but, I would probably posted something very similar as the OP within the next day or two.

---


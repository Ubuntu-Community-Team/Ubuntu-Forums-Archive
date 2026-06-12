---
title: "howto find all non-default programs I installed?"
date: 2007-08-16
forum: Programming Talk
---

### Post by eentonig on 2007-08-16
Hi,

I want to create a list that contains the programs I installed AFTER my initial Ubuntu install.

My idea was:
1. Create a list with installed packages.
> ls /var/lib/dpkg/info |grep \.list$ | cut -d \. -f1 >> $C_installed

2. Create a list with the dependencies and recommended packages for my version
> apt-cache depends ubuntu-desktop | sed 's/Recommends: //g' | sed 's/Depends: //g' | sed 's/  //g' >> $C_depends

3. Compare these two files.

I've got two questions.

1. Am I correct in assuming that the output from my ubuntu-desktop dependencies is the list of files that were installed in the beginning? Or am I missing some meta-packages that I need to include?

2. How do I use diff to create a new list, that contains only the installed packages that are not in the second list?

---

### Post by mssever on 2007-08-16
> **eentonig said:**
> Hi,

I want to create a list that contains the programs I installed AFTER my initial Ubuntu install.

My idea was:
1. Create a list with installed packages.


2. Create a list with the dependencies and recommended packages for my version


3. Compare these two files.

I've got two questions.

1. Am I correct in assuming that the output from my ubuntu-desktop dependencies is the list of files that were installed in the beginning? Or am I missing some meta-packages that I need to include?

2. How do I use diff to create a new list, that contains only the installed packages that are not in the second list?1. You also need ubuntu-minimal and ubuntu-standard.

2. Not sure off the top of my head.

---

### Post by foxylad on 2007-08-16
Apt-get and aptitude rely on a utility called dpkg, which keeps a log in /var/log/dpkg.log. This is rotated by log rotate, but if you installed within the rotate lifetime, you could just search the log files to find out what was the original install and what you've installed since.

Otherwise apt-get must keep a database somewhere - if you could find out where, and how to access it, it would tell you everything you need to know.

---

### Post by pmasiar on 2007-08-16
OK I started quest for acculturating people quoting whole article without thinking. Why you won't just quote the part you answered?

Maybe if we all pull, we will finish [that september](http://catb.org/jargon/html/S/September-that-never-ended.html) at least in one forum? Or is it in vain?

---

### Post by slavik on 2007-08-16
> **pmasiar said:**
> OK I started quest for acculturating people quoting whole article without thinking. Why you won't just quote the part you answered?

Maybe if we all pull, we will finish [that september](http://catb.org/jargon/html/S/September-that-never-ended.html) at least in one forum? Or is it in vain?
because some people click the little arrow for fast reply and also check "Quote message in reply?"

---

### Post by pmasiar on 2007-08-16
> **slavik said:**
> because some people click the little arrow for fast reply and also check "Quote message in reply?"

How hard would be to **delete** irrelevant parts, to save all of us some time when skipping it, and leaving only the relevant part to which they respond? Deleting is fast, I do it all the time

---

### Post by slavik on 2007-08-16
> **pmasiar said:**
> How hard would be to **delete** irrelevant parts, to save all of us some time when skipping it, and leaving only the relevant part to which they respond? Deleting is fast, I do it all the time
because the message doesn't show up in the quit reply box and there are 2 less pages to load :)

btw, sorry if this is considered thread hijacking

---

### Post by pmasiar on 2007-08-16
My "quick reply" does not quote, your does?

---

### Post by eentonig on 2007-08-17
> **foxylad said:**
> Apt-get and aptitude rely on a utility called dpkg, which keeps a log in /var/log/dpkg.log. This is rotated by log rotate, but if you installed within the rotate lifetime, you could just search the log files to find out what was the original install and what you've installed since.

That wont do, because I want to use this as a base for reinstalling. But the original installation was months ago.

*** please keep your (justified) quote discussion away from this topic. ***

---

### Post by nikhilm on 2007-10-18
Any joy on this topic? I'm trying to do the same thing but I'm a total newbie to Linux, so .... :)

---

### Post by slavik on 2007-10-18
> **pmasiar said:**
> My "quick reply" does not quote, your does?
there's a checkbox ;)

---

### Post by ankursethi on 2007-10-18
Python has an apt module that comes by default in Ubuntu. I guess you could write a script to extract all installed packages, run the distro from the LiveCD and get the list of packages.

You could then run the same script on your own install and compare the two files via diff.

---

### Post by #Reistlehr- on 2007-10-19
What about programs people installed from source?

and btw, september is an amazing month, so keep it eternal!

---


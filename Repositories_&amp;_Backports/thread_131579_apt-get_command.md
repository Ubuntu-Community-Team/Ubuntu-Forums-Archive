---
title: "apt-get command"
date: 2006-02-16
forum: Repositories &amp; Backports
---

### Post by soongwoo on 2006-02-16
I'm new to Ubuntu/Kbuntu.
I appreciate who suggests the replacement for the following:

 - "rpm -qa" which lists all installed packages

In addition to that, please let me know any documents to read for using apt-get
other than "man apt-get".

Thanks
soongwoo

---

### Post by bluevoodoo1 on 2006-02-16
how about...

apt-get --help

---

### Post by 5-HT on 2006-02-16
Hi, what you're looking for should be able to be done by ```
 dpkg -l 
```; where "l" is a lowercase L.

It would be wise to pipe this to a pager though as you'll get many results. For this I'd use ```
 dpgk -l | less 
``` but you could use any pager you favor. 

*Note: you can also see a list of all installed packages via synaptic or aptitude's GUI.

In terms of reading material on apt, you can try:

i) On your system:

 a) man <command>
 b) info <command>
 c) <command> --help

Where <command> is which ever command you'd like to look up.
For apt-get: apt-get, dpkg, dselect, aptitude, etc may be things to look at (there are many more)

The best thing is to look at one page (such as apt-get's man page) and see what that document references to find other pertinent commands.

ii) Browse around the Ubuntu forums, Wiki, or Document Storage Facility.

iii) Debian's site has some great manuals/reference material

 [http://www.debian.org/doc/](http://www.debian.org/doc/)

Note that this information WILL NOT be 100% compatible with Ubuntu (however, there are many general GNU/Linux manuals there as well), so be careful what you take from it (in reality, for things like apt-get there should be  no difference between the commands on Debian and Ubuntu).

Hope that helps,

---

### Post by soongwoo on 2006-02-16
Thank you very much. It helps me a lot.

soongwoo

---


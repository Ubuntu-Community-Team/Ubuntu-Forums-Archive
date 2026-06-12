---
title: "(Perl) Programming on Ubuntu"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Sacrifice on 2008-11-17
I have a few questions. I want to be involved in some sort of programming community/project on Ubuntu in Perl, but I'm not too good at CGI or anything like that. I also can't get the gnome-terminal to run working Perl scripts; it gives no response as if it did nothing. I'm on Version 8.10 and it recognizes it as a Perl script when I view the properties. Any help would help.

---

### Post by jenkinbr on 2008-11-17
Are they executable? Try chmodding the perl script(s) using
```
chmod 1744 <name of file>
```
and then run <name of file>
[note] <name of file> should obviously be replaced with the actual file 
name.[/note]
[note] prepend sudo if you do not own the file. (permission denied)[/note]

To do this in nautilus, browse to the file, right-click it and click properties, click permissions, and check the box at the bottom marked "Allow executing file as a program"

---

### Post by Sacrifice on 2008-11-17
Thanks. Do you know anything about any new Perl projects I can join or how I could find one?

---

### Post by phidia on 2008-11-17
Maybe [this site]("http://perl-begin.org/") will be helpful?

---

### Post by Sacrifice on 2008-11-19
Thanks. I guess I'll just re-learn HTML along with CSS and CGI.

---

### Post by jenkinbr on 2008-11-19
> **Sacrifice said:**
> Thanks. I guess I'll just re-learn HTML along with CSS and CGI.
Great Idea - HTML+CSS are the language of the web, so you will definatly want to know them.  Good luck.

---


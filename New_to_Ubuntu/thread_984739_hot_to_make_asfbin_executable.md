---
title: "hot to make asfbin executable"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2008-11-16
I read a thread in this forum which instructs people on how to join .wmv files with a program called asfbin in this thread:

[http://ubuntuforums.org/showthread.php?t=804557&highlight=joining+wmv+files&page=2](http://ubuntuforums.org/showthread.php?t=804557&highlight=joining+wmv+files&page=2) post#13 

It reads: ..."If you want to join WMV files, there's asfbin, which has a Linux version. Download it here, unzip it, make it executable, and do something like this" 

CODE: 

ls vid*.wmv > vidlist
./asfbin-bin -l vidlist -o allvids.wmv

I downloaded asfbin-bin to my desktop and unzipped it. How do I make it executable?

---

### Post by handydan918 on 2008-11-16
chmod +x <filename>

---

### Post by Brian_Newbie on 2008-11-16
I receive the following response with this command:

brian@brian-laptop:~$ chmod +x asfbin-bin 
chmod: cannot access `asfbin-bin': No such file or directory
brian@brian-laptop:~$ 

Do I need to place asfbin-bin in a different location than my desktop for this command to work?

---


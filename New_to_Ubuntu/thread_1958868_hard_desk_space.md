---
title: "hard desk space"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by Ma7moud on 2012-04-15
Dear, this is my first time ever i use linux. i face problem when i install my Ubuntu throw windows 7 the space by default takes 17GB i need to maximize the space but without formatting. my hard desk has total 500GB. any one know how to do this? Thanks in advance.

---

### Post by shad686 on 2012-04-15
> **Ma7moud said:**
> Dear, this is my first time ever i use linux. i face problem when i install my Ubuntu throw windows 7 the space by default takes 17GB i need to maximize the space but without formatting. my hard desk has total 500GB. any one know how to do this? Thanks in advance.
 
Right click on computer, and click manage. Then under storage click disk management. You can partition your hd from there. Its pretty easy to figure out. Hope that helps

---

### Post by Ma7moud on 2012-04-15
what computer!! do you mean windows icon my computer because i don't find any computer icon on Ubuntu.

---

### Post by shad686 on 2012-04-15
> **Ma7moud said:**
> what computer!! do you mean windows icon my computer because i don't find any computer icon on Ubuntu.
 Oh sorry. I thought you were still in windows. I'm having trouble with ubuntu start up so i'm not sure how to do it from there. When I installed it there was a partition manager that was pretty easy to use.  Good luck finding some help

---

### Post by souravc83 on 2012-04-15
If you want to keep the windows installation, then go into windows, and follow what the above poster said.
Go to disc management, and then shrink the windows drive. If you select the windows drive, and right click, there is an option called shrink disk space (or something similar, I am saying from memory). 

If you don't want to keep windows, then first of all, back up all your data. then use the Ubuntu live CD.
There's a tool called gparted, which will help you format the whole hard disc.

---

### Post by Mark Phelps on 2012-04-16
Would be nice if folks would actually READ what the OP said ... before offering advice.

When the OP said "throw windows", they meant THROUGH Windows -- in other words, a Wubi installation!  Which also means they do NOT have any partitions set aside for Ubuntu.

To the OP: to resize your Wubi installation, do NOT use Partitioning tools -- those will not work.  Instead, read through the details below about resizing:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---


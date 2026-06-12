---
title: "formatting ubuntu and windows similar?"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by jcka005 on 2012-09-07
hello everybody..just want to ask this one..is formatting a computer with windows as OS similar to formatting a computer with ubuntu11.04 OS?? if no, then how with ubuntu? thanks! i'm sorry, i didn't really know the answer..thanks very much!:p

---

### Post by Epodx64 on 2012-09-07
uhm yes and no if you just run the installer with guided partitioning then it would be pretty much how windows install just one filesystem for everything it's just installed to / on Ubuntu 
my partition scheme looks like this though
/boot ext2 200mb
/     ext4 33Gb
swap  4gb
/home ext4 300Gb
fat32 30gb for backups
fat32 70gb for virtual machines

I use ext2 for /boot because ext2 is a non-journaling filesystem and you get a little bit better boot times.

---

### Post by pete0403 on 2012-09-07
What do you mean when you say "formatting"?  Are you talking about partitioning a drive and preparing for installation of an operating system?
 
Just a little more detail will help you get a better answer...

---

### Post by arpanaut on 2012-09-07
Here's some good reading from the community Wiki:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good rule of thumb is: Windows tools for Windows needs Linux tools for Linux needs.

---

### Post by jcka005 on 2012-09-07
> **pete0403 said:**
> What do you mean when you say "formatting"?  Are you talking about partitioning a drive and preparing for installation of an operating system?
 
Just a little more detail will help you get a better answer...

actually, formatting is not my problem..here's really the problem..we are running an IT Center inside our university..we are protecting the client computers by creating user accounts with passwords..the last OJT's made those passwords..the given passwords are working with the client computers except for one..our superior told us to format then the computer with the unkown password..that is why i am asking if formatting an ubuntu similar with windows..
ganito nalang, if anyone knows what to do with the unknown password, without formatting, i would be very happy if you guys will help me..sorry :( , but thanks for the replies..it's much appreciated..

---

### Post by PaulW2U on 2012-09-07
> **jcka005 said:**
> if anyone knows what to do with the unknown password, without formatting, 

Does [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) help?

---

### Post by krustenBrot on 2012-09-07
Maybe the old OJT knows the root password? Logging in as root you could easily modify existing accounts or create new ones.

---

### Post by jcka005 on 2012-09-07
> **PaulW2U said:**
> Does [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) help?

okay, i have read the contents of the link you have given me..i'll try it and let you now if it works..but i'm afraid i'll not be able to do it now because i am currently on my duty watching over my fellow students..they are using the computers..i'll be disturbing them if i do so..thank you sir or madam..thanks very much..

---

### Post by jcka005 on 2012-09-07
we can't reach the old OJTs since they are working now..we are trying to contact them before but they are not responding..

---

### Post by offgridguy on 2012-09-08
> **arpanaut said:**
> Here's some good reading from the community Wiki:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good rule of thumb is: Windows tools for Windows needs Linux tools for Linux needs.

Oh I like this.  Thank you

---


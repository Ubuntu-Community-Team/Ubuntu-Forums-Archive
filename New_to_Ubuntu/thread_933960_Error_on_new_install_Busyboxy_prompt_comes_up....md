---
title: "Error on new install Busyboxy prompt comes up..."
date: 2008-09-30
forum: New to Ubuntu
---

### Post by robfindlay on 2008-09-30
My brother asked me to install Ubuntu 8.x on his machine straight forward x86.  So I burn him an ISO boot up and we drop to the following: 

Busybox shell etc etc 

(initramfs) 

then SLOWLY a series of cryptic error messages centering on ATA4.00 keep coming up. 


Never had this problem before.....any thoughts? 

TIA. 


-Rob

---

### Post by wolfen69 on 2008-09-30
try installing ubuntu using the alternate cd. worked for me once.

---

### Post by robfindlay on 2008-09-30
> **wolfen69 said:**
> try installing ubuntu using the alternate cd. worked for me once.


"alternate cd"?

EDIT: NM found it, will give that a try, any other opinions? 


-Rob

---

### Post by walkingthecow on 2008-09-30
Alternate CD is a non-graphical installation CD for Ubuntu and can be downloaded from "Get Ubuntu" page. Possibly the error is due to a bad burn of the CD? You could try testing the integrity of the CD that you're using. After typing "exit" do you get a kernel panic?

---

### Post by robfindlay on 2008-09-30
> **walkingthecow said:**
> Alternate CD is a non-graphical installation CD for Ubuntu and can be downloaded from "Get Ubuntu" page. Possibly the error is due to a bad burn of the CD? You could try testing the integrity of the CD that you're using. After typing "exit" do you get a kernel panic?

Actually didn't even think to try "exit" never Ubuntu do this to me before.

---

### Post by ipatt on 2008-09-30
Hello, I have a somewhat different experience. I am running 8.04.01 (everything up to date) and when Ubuntu first comes up I am presented, in order, with a choice of Generic Kernels: 2-6-24-19, 2-6-24-16 and 2-6-22-14. The first two take a long time to load and I am finally presented with BusyBox 1.1.3, a command line and a help prompt. Help gives me a large number of commands, none of which I know how to use (yet).
 However if I choose 2-6-22-14 then I get the standard Hardy Heron graphical boot.
 Question 1) what is the difference the kernels? I am running Ubuntu on an older machine - Athlon XDP, 1.3GHz, motherboard is a PCChips M825VXX with 512MB memory, HDD is a Maxtor 30GB.
 Question 2: from the BusyBox screen can I get to the Ubuntu graphical interface? How?
 I am concerned because in the past when a new upgrade with a new kernel is released the oldest kernel is dropped from the options at the initial boot screen. Presently, I will resist future upgrades.
 Any ideas, comments?

 Thanks.

---

### Post by robfindlay on 2008-09-30
> **robfindlay said:**
> My brother asked me to install Ubuntu 8.x on his machine straight forward x86.  So I burn him an ISO boot up and we drop to the following: 

Busybox shell etc etc 

(initramfs) 

then SLOWLY a series of cryptic error messages centering on ATA4.00 keep coming up. 


Never had this problem before.....any thoughts? 

TIA. 


-Rob


Have not had a chance to try exiting yet, does anyone have any ideas about the errors? 

-R

---


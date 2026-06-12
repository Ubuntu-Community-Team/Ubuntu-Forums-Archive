---
title: "Wiping out Windows ~ Making Ubuntu drive bootable..."
date: 2014-06-25
forum: New to Ubuntu
---

### Post by amzolt on 2014-06-25
I have an Hp Pavilion dv7 with windows 7 on C: drive and Ubuntu 14.04 on D: drive...

The Ubuntu was installed at my local computer shop.

The tech created a boot that lets me choose which drive but he said the boot is written on the Windows partition.

I'd like to make the computer automatically boot from the D: drive---straight into Ubuntu.

Then, I want to wipe Windows out of existence and use the C: drive for clones and backups.

How do I make the computer boot straight to Ubuntu on the D: drive??

---

### Post by Impavidus on 2014-06-25
Instead of that rather vague statement from the tech let's get the details. Could you open a terminal and post the output from these commands?
```
sudo parted -l
mount
```Because it isn't really possible to have Ubuntu installed on the D drive. Ubuntu has to be installed on a Linux partition and Windows only knows about Windows partitions and therefore only labels Windows partitions. And the phrase "D drive" is only used by Windows.

---

### Post by amzolt on 2014-06-25
Are those two separate commands?

---

### Post by amzolt on 2014-06-25
> **Impavidus said:**
> Instead of that rather vague statement from the tech let's get the details. Could you open a terminal and post the output from these commands?
```
sudo parted -l
mount
```Because it isn't really possible to have Ubuntu installed on the D drive. Ubuntu has to be installed on a Linux partition and Windows only knows about Windows partitions and therefore only labels Windows partitions. And the phrase "D drive" is only used by Windows.

OK, I just talked to that tech and here's basically what he said:

The HP can only boot from one drive.

The one it's booting from has Windows.

I'll have switch the drives physically; then, alter the boot manager on the Linux drive to ignore the 
Windows drive.

---

### Post by ajgreeny on 2014-06-25
Yes, they are separate commands; run one after the other and report back here the output you see by copying it from terminal most easily by highlighting the output and right clicking, selecting Copy. (Ctrl+C does not work in terminal, you need Ctrl+Shift+C).

The details your tech person gave you does not really help us very much as it still doesn't tell us what is what, how many partitions you have, or exactly how your system boots; from what he has told you it sounds as if it my be using EasyBCD about which I know absolutely nothing, so can't help with that.

It may help us also if you can run Boot-Repair on your system by following the info from my signature.

---

### Post by amzolt on 2014-06-25
> **ajgreeny said:**
> Yes, they are separate commands; run one after the other and report back here the output you see by copying it from terminal most easily by highlighting the output and right clicking, selecting Copy. (Ctrl+C does not work in terminal, you need Ctrl+Shift+C).

The details your tech person gave you does not really help us very much as it still doesn't tell us what is what, how many partitions you have, or exactly how your system boots; from what he has told you it sounds as if it my be using EasyBCD about which I know absolutely nothing, so can't help with that.

It may help us also if you can run Boot-Repair on your system by following the info from my signature.

Please see my response just before your post---I'm taking it back into the shop since they installed it and know how to rearrange things :-)

---

### Post by ajgreeny on 2014-06-25
OK, I hope they manage to set it up as you want.

Please keep us posted about the outcome, and let us know what you think once it is all working properly.

---


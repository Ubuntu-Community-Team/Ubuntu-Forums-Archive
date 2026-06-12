---
title: "Saucy salamanda start up"
date: 2013-12-11
forum: New to Ubuntu
---

### Post by barrykgerdes on 2013-12-11
I have just downloaded 13.10 and made a boot disk.
I booted from the disk and saw the demo program OK
I took the option then to install. I would have liked to install it inside windows XP where I already have 12.04 running OK but that option was not available
It installed on an empty 128GB partition, apparently OK
When complete with all the updates etc ticked the program started (?) however there is only a normal back ground with no icons ore menu bars
I can get some results with a mouse rt click but that is all
What have I done wrong. 

Barry

---

### Post by UltimateCat on 2013-12-11
Hi:

You mentioned:
> It installed on an empty 128GB partition


Did you create a 'swap' partition?


You may want to post all of the partitions on your computer so we can get an idea of what went wrong (if anything) with your new 13.10 install-
To do that open your terminal and as 'root' run this command:
```
fdisk -l   (small letter L)

```

I don't think that you have done anything wrong but it sounds to me that the installation was not complete based on the fact that you only have a normal background and no icons:-
Aside from that the iso file may have been corrupt.  Did you verify the files integrity in the terminal?

---

### Post by sammiev on 2013-12-11
There is no option any more to install Ubuntu inside of Windows. You would need to run a VM or install Saucy a long side of Windows. :)

---

### Post by barrykgerdes on 2013-12-11
Thanks for the answers

Firstly I have installed Ubuntu many times before without bother. 
Previously I was asked where to install it but not this time. Probably because I already had some un-allocated space and it took the lot for a Linux partition and a swap partition
The only difference I did this time was to use a DVD as the iso was too big for a CD
The demo worked and then followed the instructions to install 
These proceeded and completed without problem and I was instructed to restart.
I have now deleted the installation and the Grub start and restored the standard Windows boot.
I download the iso again and retry some time.
My 12.04 version still works and I will try another computer and use VMware for 13.10

---


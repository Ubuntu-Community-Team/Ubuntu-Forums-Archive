---
title: "Error 21 - how to reinstall GRUB?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Neon_Knight on 2008-08-19
Okay okay okay okay. 

I'd quite like this sorted as soon as possible, I hope you people can help me.

I tried to install Ubuntu on my new hard drive, which will be called Drive G from now on.  I did so, the installation completed.   Once trying to boot however, the GRUB couldn't load because of "Error 21".  I have found out that this means "disk not found".  I thought, that's probably because, the drive I installed Ubuntu on was plugged into a PCI SATA expansion card rather than on the onboard SATA.  (I have 3 drives, two onboard, but I only have two onboard SATA connectors, so I bought this SATA PCI card which gave me some more).

So, now I've plugged Drive G into the onboard SATA, and put Drive E onto the PCI card.  Drive E doesn't boot anything, it just has a bunch of stuff I downloaded, so I don't mind if that isn't detected by the BIOS.

So now I have my Ubuntu disk on the onboard SATA, yet I'm still getting error 21.  I presume there's a reason for this, but I can't tell what that is, and I don't know what to do.   I need some way to reinstall or reset the GRUB so it realises "oh, hey, this drive actually does exist and it's located here".   

I tried

```

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# grub-install /dev/sdb6
Could not find device for /boot: Not found or not a block device.

```

sdb6 is drive G, I found this out from fdisk, the one listed as "linux".


Any help?  Please? 

I'm out of options..

---

### Post by sharks on 2008-08-19
[http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

---

### Post by Neon_Knight on 2008-08-19
> **sharks said:**
> [http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

I have read that, thanks.

I do google my problems before I come posting about them. :)

Anyway nothing there helped. 

Haven't tried supergrub, because I don't know what it is, or how to use it, and I'm hoping there's a simpler/faster solution.

---

### Post by itix on 2008-08-19
Super grub disc should sort out your problems. 
It can be downloaded [here]("http://www.supergrubdisk.org/")

______________________
Real capitalists use **Linux** because Micr&#9773;s&#9773;ft support the communist
idea of monopoly

---

### Post by samuraiCat on 2008-08-19
Have you tried going into your boot options? You can change the disk that boots first from "h0,0" to "h1,0" (or whatever the correct hard drive turns out to be). I had this same problem when I installed Ubuntu on a desktop PC with 3 drives--since one of the drives was an old IDE, it automatically tries to boot from there, giving me the Error 21 message. I had to do the "h1,0" switch, and then I logged in, went into my /boot/grub/menu.lst and changed that same information in there. I also had to comment out the two lines at the end of menu.lst that say something like "h0, h1" and "h1, h0".

I'm sorry if this is vague; I'm not in front of that machine right now, and I'm telling you this from memory.

---

### Post by croniksoft on 2008-08-19
Run "sudo cfdisk" and tell me what you get..just want to make sure you are trying to install it in the right location.

---

### Post by Neon_Knight on 2008-08-19
```

                         cfdisk (util-linux-ng 2.13.1)

                              Disk Drive: /dev/sda
                        Size: 80026361856 bytes, 80.0 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 9729

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1        Boot        Primary   NTFS             [        ]      80015.53
                            Pri/Log   Free Space                           8.23


```

---

### Post by Neon_Knight on 2008-08-19
Thanks for the replies, guys. 

I think I might just have to use this supergrub program.

I have looked in my BIOS - but it's weird, it's confusingly arranged and it can't see my PCI SATA drive at all.  I've switched them round now, so there should be something I can do there...but I'm not at all confident messing around with BIOS settings.

---

### Post by Neon_Knight on 2008-08-19
Oh, I should mention.  I'm running off of the live CD.

---

### Post by Neon_Knight on 2008-08-19
Right, well I booted into supergrub.

Am I supposed to just "know" exactly what I should be doing with it?  I'm afraid I don't know what on Earth to do.  

I posted this in the "Absolute Beginner" forum for a reason. That program is not at all obvious to use and I failed to find how I'm supposed to fix my problem with it.

I found a "fix gnu/linux" option, and I fixed sda6 with it.  And now the GRUB boots, so there was some success.  However if I choose anything apart from "Windows XP" I'm given the same Error 21 message.

Right now I'm back on XP.  Really, I need to know what to do.

---

### Post by itix on 2008-08-19
I might have an old version of the CD but mine is just designed to be booted from. It boots, leaves a message saying "super grub disc has done it!!!" and the problem is (usually) solved.

It's strange that grub can't find your linux partitions. I know there are grub haxxes that can find linux, but it was quite a while ago I used them so I'll leave that to someone who actually remember them.

___________________
Real capitalists use Linux because Micr&#9773;s&#9773;ft support the communist
idea of monopoly

---

### Post by caljohnsmith on 2008-08-19
Neon_Knight, how about booting into your Live CD and doing the following in a terminal:
```
sudo fdisk -lu
```
Please post that output, and also:
```
sudo grub
grub> find /boot/grub/stage1
grub> geometry (hd0)
grub> geometry (hd1)

```
If you can provide that info, I think it will be probably be quite easy to fix your Grub.

---

### Post by Neon_Knight on 2008-08-19
Thanks for the help guys.  

Nothing was working - so I just reinstalled Ubuntu.  Seeing as it was a brand new partition, I didn't lose any data.

Thanks for all of the help everyone!

---

### Post by itix on 2008-08-19
That's the way I used to solve my problems as well ;)
You'll learn to handle yourself eventually. I know, I'm soon going to celebrate my first year of linux usage...

Welcome to the linux society :)

(and I think I'll stop using my fake signature now as I've concluded that you are a sane and mature person who doesn't care about such things)

---

### Post by Neon_Knight on 2008-08-19
> **itix said:**
> That's the way I used to solve my problems as well ;)
You'll learn to handle yourself eventually. I know, I'm soon going to celebrate my first year of linux usage...

Welcome to the linux society :)

I'd find that terribly welcoming if I hadn't been using linux for about 3 years already... which is really quite embarrassing considering the number of times I've needed assistance.

Just, for some reason the weird problems always seem to happen to me.  :confused:

But then again I've walked others through solving their problems more than I've needed it myself.

---


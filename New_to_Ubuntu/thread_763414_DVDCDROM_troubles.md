---
title: "DVD/CDROM troubles"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by SR_ELPIRATA on 2008-04-23
Ok, here I go again... on my own...

The problem Im having is, Ubuntu allows me to use the drive as long as there has been either a CD or DVD on it when I started it up, if not, the drive wont show up nor I'll be able to open the DVD tray.

Whenever I have a CD/DVD on I can see its label but does NEVER show inside /media/CDROM nor /media/CDROM0/, its in /media alright but appears as what the CD or DVD label says.

This is a problem as whenever a program asks me to insert a CD it will never find it. Example, installed Virtualbox and after all the restarts and all, I get to check the mount CD and enable pass through but it never shows which letter would be assigned.

When I powered a VM to install the windows software it wont detect the CD, even though I can see that the CD is in it and I can browse its contents with Nautilus, its just that instead of appearing under /media/cdrom I have it at: /media/WXPVOL_EN

I've done a huge search on these forums but with no results on this or similar problems, I've also posted on them looking for help and nothing so far.

Can anyone throw some light?

DVD burner Lite On, internal IDE.
Ubuntu 7.10

ELPIRATA

---

### Post by SR_ELPIRATA on 2008-04-23
19 hours later...

Anyone?

ELP

---

### Post by SR_ELPIRATA on 2008-04-28
4 day later and no answer yet.

I've been browsing endless pages of the forums with suggestions I've even tried to implement... guess you may want to see them here... so here I go....

A helpful fella told me to check the etc/fstab and look for a line of code:

```
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Which aside of the utf-8 that he had, is basically the same.

On another thread:
[http://ubuntuforums.org/showthread.php?t=767278&highlight=%2Fetc%2Ffstab](http://ubuntuforums.org/showthread.php?t=767278&highlight=%2Fetc%2Ffstab)

someone showed the contents (specifically the part related to their DVD drive for the 'sudo lshw' command, which I did in the terminal and this is the code I got related to the DVD:

```
*-cdrom
                   description: DVD writer
                   product: LITE-ON DVDRW SOHW-1693S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: KS04
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: status=ready
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc

```

The only difference to that guy's output is on the logical name he shows also more names rather than just /media/cdrom0 or /media/cdrom1 (he had 2 drives), but I havent found yet if I can add that to my list as well.

Hummm, not sure if it will help or not, but as I said before, if there's no CD/DVD in the drive the unit will not allow me to manually open the drive (havent tried to force it yet, with the mini-hole) as you normally would to insert a CD/DVD. Anyways, when I did the aforementioned command the unit had a CD on it, now while empty if I run the command, the unit WONT APPEAR on the 'sudo lshw'. It does appear the other storage hard drive I have on that same channel, but NOT the DVD.

Ok, other weird stuff I found, but I have no idea what value this holds...

Did a right click on /media/cdrom0 (the folder) while the unit had a CD on it and it said that it had 26GB free, exactly what is left of my actual HDD that has ubuntu installed. If you go to /media/cdlabel and do right click properties, it will tell you that it is a iso9660 and that it has 588mb of used space and no free space, what you would've expected from /media/cdrom0.

I tried also deleting the line about the cdrom in fstab, and upon restarting (with a cd on it) it was back, the whole line was back on the file (Perhaps I did it wrong?) I thought that if you deleted that line the unit wouldnt work.

Well, not sure what more to post or say. I'm reading EACH page of the archived forums and reading anything Fstab or DVD/CD related, and so far nothing, (Im only on the 10th page of over 5000).

Would be nice if at least someone would point me in a direction....

ELP

---

### Post by SR_ELPIRATA on 2008-04-29
A new update...

I noticed today, as I needed to swap window drives to test something that when the DVD has no media in it... the BIOS WONT SEE IT!!!!!!!!!

This solves half of the problem, if the Bios doesnt see it... perhaps there's a malfunction on the unit. But still doesnt solve the other part, for whenever there's media in it it will never appear under /media/cdrom0

Some friend suggested installing Webmin and that there were options in which I could force the mount so that it shows, but if the BIOS doesnt see it, I doubt it will be able to force something to work when it doesnt appear to, theres stuff that not even software can solve.

ELP

---

### Post by janfsd on 2008-04-29
This is a big annoyance for me too. For mounting into /media/cdrom0:
Check 1st in your /dev folder, for something that starts with cd...
For me it was /dev/cdrom2, and check if its your drive with: hdparm -i /dev/cd...
If it is the one: get into fstab and change the line accordingly. Hope it helps. 
But I got a major problem, all the data from my cds cannot be opened, used, or whatever.

EDIT: /dev/cdrom2 it is a link to /dev/scd0 so maybe it is now called like that.

---

### Post by SR_ELPIRATA on 2008-04-30
I thought I had replied... your tip worked, its great now, I can now click on /media/cdrom and I can see the contents of the CD/DVD unit. Ironically, I hadnt noticed myself that the DVD had a different address /dev/hdc shows here but I had /dev/hdd on the fstab.

I still have the other problem, that if no CD or DVD inside it simply wont be recognized by the Bios and therefore not by Linux either. I gotta get another unit to test, so sometime this week I will strip another computer off its drive and test it on mine.

Thanks...

ELP

---


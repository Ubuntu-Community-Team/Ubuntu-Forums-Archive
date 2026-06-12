---
title: "Overwrite Ubuntu"
date: 2022-04-13
forum: New to Ubuntu
---

### Post by pussekatt on 2022-04-13
I have an old laptop with Ubuntu 20.04 installed.I tried to install Lubuntu in a dual boot system but Lubuntu goes as far as what looks like smoke rising on the screen and goes no further.I left it running in that state and timed it for about 20 minutes but nothing changed.The Lubuntu install had already been running for a while.At the start I selected "run alongside another instilation"
So,what is happening.
I want to run Lubuntu alongside Ubuntu with a view to wiping Ubuntu and running Lubuntu only,as Ubuntu is really slow on this old PC.

---

### Post by ActionParsnip on 2022-04-13
Why the dual boot? The only difference is the default DE/WM and some apps. The underlying OS is the same.....

---

### Post by grahammechanical on 2022-04-13
So, your thread title is misleading. You want help installing Lubuntu.  Some of the forum members are experienced in installing and using  Lubuntu. They might not be interested enough to read a post about  deleting Ubuntu. Based upon the information I have gained from reading  other threads, you will need to provided details of the hardware and  where you downloaded the Lubuntu ISO image from.

How large is the  hard drive? Is there enough space for the minimal storage requirements  of the two operating systems? How much space is the Ubuntu installation  taking up?

Regards

---

### Post by pussekatt on 2022-04-14
How do I get the specs of my hardware ? And what I really want to do is install Lubuntu and wipe Ubuntu,as I mentioned in the last line of my post.

---

### Post by ActionParsnip on 2022-04-14
> **pussekatt said:**
> How do I get the specs of my hardware ? And what I really want to do is install Lubuntu and wipe Ubuntu,as I mentioned in the last line of my post.
```
 
sudo lshw > /tmp/output.txt; xdg-open /tmp/output.txt 

``` 
Post the content as an update

---

### Post by Impavidus on 2022-04-14
Replacing Ubuntu with Lubuntu on low powered systems makes sense. It's cleaner than converting Ubuntu to Lubuntu (which can be done, by installing lubuntu-desktop and removing all packages that are defaults in Ubuntu but not in Lubuntu, but it's likely to leave dirt around).

I've never installed Lubuntu myself. Does the installer detect the existing Ubuntu system and offer to reinstall it? You can always use manual partitioning, select the currently used partition(s) for the same mountpoint(s) and mark the root partition to be formatted.

---

### Post by GhX6GZMB on 2022-04-14
> **Impavidus said:**
> Does the installer detect the existing Ubuntu system and offer to reinstall it?

I don't think so. I've installed Lubuntu 18.10 followed by 20.04 and there were no signs of that

---

### Post by guiverc on 2022-04-14
I don't see any release details, except for Ubuntu 20.04.

Lubuntu installer (`calamares`) provides a number of options depending on what it sees.

The Lubuntu manual  can be seen here [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html) with an actual install screen here showing only two options - [https://manual.lubuntu.me/stable/_images/partitioning.png](https://manual.lubuntu.me/stable/_images/partitioning.png) however install on a different box and you can be offered five options including "**Replace Partition**" which would replace a Ubuntu system with the Lubuntu one.

If it was me and I was offered the **Replace Partition** option, **I'd still not likely use it**, and it performs a **format**and thus it's a new install and nothing would be kept from your prior system there. If it was my machine; I'd use the **Manual Partitioning** option so you can setup exactly what you want & not picking one of the other 1-4 options you are offered.

I get the feeling you want to use the "**Install Alongside**" option which you'll be offered if your system is detected as capable of using that. Why you won' t be offered it can be many reasons, eg. your MBR/legacy/DOS partitioning scheme may not have any available primary partitions thus it's currently not possible - but that's only one reason why it's not offered.

Lubuntu uses a different installer to most *flavors*  (*`calamares` being used by the recent KDE based Ubuntu Studio releases as well*), but its options are the same as `ubiquity` used by main Ubuntu as the same install scripts run, it really just looks different on the screen (*my opinion*). It's *stronger* in some areas; but more *fragile* in others.


FYI: I'm using a 2009 dell box now, so a 10 year old laptop would actually be newer than this box, and I use boxes as old as from 2005 in QA-testing the currently Lubuntu *jammy* system too. However boxes vary and some  are more difficult (esp. laptops).

---

### Post by pussekatt on 2022-04-19
@ Action Parsnip: I copied and pasted that command you posted but It asked me for my password and then I couldent enter any text at all.

---

### Post by pussekatt on 2022-04-19
I was offered 3/5 options,including If I wanted to install Lubuntu alongside another OS.This is the option I picked but as I described above it only went as far as what looked like blue smoke ( like a screensaver )

---

### Post by ActionParsnip on 2022-04-19
When you use sudo you don't get any feedback as you type your password. Just keep typing it and hit ENTER

---

### Post by pussekatt on 2022-04-20
No,I tried again and again it asked for my password,so I pasted the text again and added my password on the end.Still no go.I also tried just hitting enter and that didnt work either.
Something is wrong somewhere,so,I think I might just wipe my HDD and do a clean install.

---

### Post by coffeecat on 2022-04-20
> **pussekatt said:**
> so I pasted the text again and added my password on the end.

No, don't do that. Text+password != password.


> **pussekatt said:**
> 
I also tried just hitting enter and that didnt work either.

That will never work if the terminal is waiting for a password.

Simply type the command ActionParsnip suggested, and then press enter. You will then be prompted for the password. Then, and only then, type in the password. You won't see it being typed in. Simple press enter once you have entered your password.

---

### Post by pussekatt on 2022-04-22
x-special/nautilus-clipboard
copy
file:///home/colin/Desktop/Lenovo_G40_Spec.PDF

There you go,got it this time.Can I run one Virtual box with this system ?

---


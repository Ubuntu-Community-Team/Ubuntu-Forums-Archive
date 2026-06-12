---
title: "unable to log on pc"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by Asadik on 2013-05-05
Hi I recently had Ubuntu on a partition, but it didn't work out so I went on windows 8 partition and deleted that partition. However, now when I restart my computer it will not load anything and gives an error of

Error: unknown filesystem.
grub rescue>


I don't know what to do and I don't know how I can log back into windows or anything. I download an ios of ubuntu and simply put it on a CD to load. I can't use the click f12 to boot either, it seems to not work. all the help is appreciated thank you. I really need this computer working again thanks

---

### Post by carl4926 on 2013-05-05
Unless you have a windows DVD, I mean a proper one.
You best solution for now is to put ubuntu back, even if only in a small partition, just use it to boot your PC to windows

---

### Post by Asadik on 2013-05-05
I understand that, but my question is how do i do that? any cd I put in nothing happens just this grub rescue

---

### Post by Asadik on 2013-05-05
I also did the ls command and it pops up with the following:

(hd0), (hd0,msdos6), (hd0,msdos5), (hd0,msdos3), (hd0,msdos1)

If I do ls (hdx,y) all of them come back as unkown filesystem

---

### Post by carl4926 on 2013-05-05
You must have booted from the CD originally to install Ubuntu in the first place
Is this a UEFI machine?

---

### Post by Asadik on 2013-05-05
Yes I did use a CD to boot ubuntu when i first installed it. I'm not sure about the UEFI, my computer is a Lenovo G575 with AMD Vision and all that good stuff if that helps at all

---

### Post by Asadik on 2013-05-05
I currently have in my possesion, the ubuntu ios cd, a linux mint ios cd, and a windows 8 ios cd. when i open the splash screen no command comes up about clicking f12 for boot menu or f2 for set up not do either buttons work when I click them

---

### Post by carl4926 on 2013-05-05
OK
This is an older laptop. So you installed win8 yourself?

Are you saying the windows DVD doesn't boot up either?

---

### Post by carl4926 on 2013-05-05
I have a G550 - very similar in many respects
I put Windows 8 on mine last week - for a project I am working on about multi-boot
[[img]http://s20.postimg.org/4d4qy85ex/2_mbr_table.jpg[/img]](http://postimg.org/image/4d4qy85ex/)
Windows 8 is in sda1

---

### Post by Asadik on 2013-05-05
yes I installed windows 8 on my own. I am unable to click any button for boot option as the bottom half of my splash screen doesn't even show and two when i do click the buttons non of them work.

---

### Post by Asadik on 2013-05-05
I have fixed the problem thank you for your help. For anyone that encounters this. I simply took my hard disk out wth my windows cd in, this forced my computer to boot the cd then I put the hard disk back in and it read it perfectly fine. Now I am re installing windows

---


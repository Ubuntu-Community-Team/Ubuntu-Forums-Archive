---
title: "Mounting Ubuntu in Windows"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Rubberlugs on 2008-07-16
Can ubuntu be somehow ran from inside a windows install, I could be wrong but I'm sure I've seen someone do it. Wasn't a dual boot, he was in windows and somehow ran it from a folder from what I could see.

---

### Post by Elfy on 2008-07-16
It's (probably) wubi - it instals in windows apparently .

It is on the livecd and I think you can download it as an .exe

---

### Post by Ryadt on 2008-07-16
He probably was using wubi.

---

### Post by dracayr on 2008-07-16
according to your title you want to mount an ext3 hd from windows; if that is the case:
fs-driver.org

In your post you say sth. about ubuntu inside windows. This is possible with Virtualbox (or similar programs)

EDIT: or wubi

dracayr

---

### Post by Rubberlugs on 2008-07-16
Thanks.

I am unable to install VMware server on a vista 64 box due to driver signing issues. Could I use this wubi, then install the VMware server inside that?

---

### Post by Elfy on 2008-07-16
I don't think that you can, what are you trying to use vmware for?

Edit - you could use virtualbox.

---

### Post by halitech on 2008-07-16
Wubi will install Ubuntu (or whatever version of linux you select) in a dual boot. If the person was running them at the same time (ie, could select a different tab in windows and be in Linux) then he was using a virtual machine.

wubi - [http://www.wubi-installer.org](http://www.wubi-installer.org)
VMWare - [http://www.vmware.com/](http://www.vmware.com/)

---

### Post by Rubberlugs on 2008-07-16
I'm doing a course on SQL and I was hoping to use VMware server to create a virtual machine with a trial edition of 2k3 then install sql express on that.

---

### Post by halitech on 2008-07-16
if ultimately you want to have a version of 2k3 then installing Ubuntu to install a virtual machine to run w2k3 and then installing sql express seems like a lot of work. Why not try virtual box if you cant get VMWare to install?

---

### Post by Rubberlugs on 2008-07-16
I thought it was a bit of a long way round myself too. After running into that whole driver signing issue late last night with VMware server I wasn't sure where to turn. I'll look into that Vrtual box, thanks.

---

### Post by halitech on 2008-07-16
not a problem :)

been awhile since I used windows to actually install anything, what exactly was it saying that was preventing you from installing VMWare server on your windows computer? Just curious is all :D

---

### Post by Rubberlugs on 2008-07-16
Its that whole unsigned drivers nonsense that's with vista now.

[http://www.vistax64.com/drivers/9351-unsigned-drivers.html](http://www.vistax64.com/drivers/9351-unsigned-drivers.html)

I used to be a mac user till I started studying microsoft certs and had to buy a PC for the my studies. I rue the day I ventured down that dark path, everything seems like a battle of wills. Machine Vs Man, you think you've solved one issue and another just pops up somewhere else.

---

### Post by halitech on 2008-07-16
so vista won't let you bypass unsigned drivers anymore? seems like a good way of getting more money out of hardware companies to verify their software to me. At least in XP you could just say yes anyway and have it install.

---

### Post by Rubberlugs on 2008-07-16
I think as well that with Microsoft having a vested interest in virtualization through products like virtual PC, it's pretty underhanded making it such a hassle to use other products like VMware. But then that is Microsoft right enough.

---

### Post by halitech on 2008-07-16
well, not like MS has ever been accused of doing what is best for the users, only for their bottom line.

---

### Post by Elfy on 2008-07-16
> **Rubberlugs said:**
> Its that whole unsigned drivers nonsense that's with vista now.

[http://www.vistax64.com/drivers/9351-unsigned-drivers.html](http://www.vistax64.com/drivers/9351-unsigned-drivers.html)

I used to be a mac user till I started studying microsoft certs and had to buy a PC for the my studies. I rue the day I ventured down that dark path, everything seems like a battle of wills. Machine Vs Man, you think you've solved one issue and another just pops up somewhere else.

This post should be in testimonials where all the windows works ootb threads live :D

---


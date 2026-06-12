---
title: "I am running Win 7 on one HD (C) and the other (E) is blank and formatted..........."
date: 2014-02-08
forum: New to Ubuntu
---

### Post by Bugscuffle on 2014-02-08
Win 7 is loaded onto my C drive and is running I guess as well as a Windows program can run. I want to install ubuntu on my E drive, the second, blank disc on my machine. Win 7 is brand new to me and I don't know the ins and outs of it at all. When I try to do a download of ububtu I get a pop up widow that asks me to "save" it. O.K. I save it and it gets saved in my "downloads" folder in Win 7. That's great EXCEPT that, from there, I can only install it onto the C drive alongside of my Win 7. I don't want to do that. There are no options, or at least I have not found a way, to install the ubuntu onto the E drive from there. Am I missing something?

---

### Post by bc.haynes on 2014-02-08
I don't believe it is possible to install it from your Win 7 drive. You need to burn the .iso file it to a DVD and make a Live DVD and run it in your DVD drive to install it to your other drive.

[[color=red]Here[/color]](https://help.ubuntu.com/community/BurningIsoHowto) is a tutorial on burning CDs or DVDs.

---

### Post by tfrue on 2014-02-08
Are you using WUBI.exe to install Ubuntu? If you are, don't do it! It's deprecated and not recommended to use for installing Ubuntu, rather partition the HDD and live boot into Ubuntu and install it that way.

---

### Post by Mark Phelps on 2014-02-09
Drive letters are a convention used by Windows; plus, they aren't actually "drives", instead, they are "partitions".

The only way to install Ubuntu to a "drive" is using Wubi -- which has been discontinued largely due to the problems associated with UEFI.

Since you can't install Ubuntu to an NTFS partition, you should remove that partition and use "something else" in the Ubuntu installer to install in the unallocated spot.

---


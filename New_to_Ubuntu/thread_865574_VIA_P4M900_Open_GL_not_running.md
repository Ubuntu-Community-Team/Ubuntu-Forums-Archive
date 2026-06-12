---
title: "VIA P4M900 Open GL not running"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by ambar_N on 2008-07-20
Hi...
I'm newbie in ubuntu, just now I install ubuntu 7.10 in my PC, but I can't enjoy the compizfusion because my 3D accelerator is not active.
How to activate 3D accelerator on my VIA P4M900 Chipset ?
I've try to download driver from Viaarena, but when I extract the downloaded file I only get the Installation instruction file.:(:(

I'm still unlucky using some advise from someone to change "vesa" to "via" in /etc/xorg.conf:confused::confused:

please help me to solve this problem, I really need it...
I'm sorry for my English,
Thanks lots....:)

---

### Post by overdrank on 2008-07-21
> **ambar_N said:**
> Hi...
I'm newbie in ubuntu, just now I install ubuntu 7.10 in my PC, but I can't enjoy the compizfusion because my 3D accelerator is not active.
How to activate 3D accelerator on my VIA P4M900 Chipset ?
I've try to download driver from Viaarena, but when I extract the downloaded file I only get the Installation instruction file.:(:(

I'm still unlucky using some advise from someone to change "vesa" to "via" in /etc/xorg.conf:confused::confused:

please help me to solve this problem, I really need it...
I'm sorry for my English,
Thanks lots....:)

Hi and welcome, I do not believe that you will be able to use compiz-fusion but you may look here
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by ambar_N on 2008-07-21
So... is that meaning impossible to me to activate openGL in my computer...?
Then, I can't running anything that need to use openGL? even Tuxracer game..? Ohh... No......](*,)](*,)](*,)

---

### Post by overdrank on 2008-07-21
> **ambar_N said:**
> So... is that meaning impossible to me to activate openGL in my computer...?
Then, I can't running anything that need to use openGL? even Tuxracer game..? Ohh... No......](*,)](*,)](*,)

I am sorry to be the bearer of bad news but you may look at adding a graphics card to the system.

---

### Post by ambar_N on 2008-07-22
Ok, can you give me some recomendation for good graphic card to working with my ubuntu...?:-k:-k
Thanks a lots...

---

### Post by doubledrop on 2008-11-12
Hi all! First:
> **overdrank said:**
> I do not believe that you will be able to use compiz-fusion...
It is simple to run compiz-fuzion on this chipset, I check it. Just edit /usr/bin/compiz and add in WHITE list via driver name (or openchrome), but in some cases its crashes (often of start/end eclipse or openoffice).
Second: You can try prebuild drivers here: [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) for yours system. Developers promise that compiz will work on ubuntu 8.10 with their driveres (you can read this in readme in alpha version of drivers).

---


---
title: "Using an iso"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by wavemaker on 2008-06-21
Gooday all. I got a disc on a magazine the other day and I downloaded an iso, put it on a disc and then tried to boot it on my computer. Well, that didnt work, so I spose there is more to it than what I did. Can one of you kind folk point me in the right direction. I am a fairly new user but I can usually follow instructions if they are clear to me. Regards, James.

---

### Post by lisati on 2008-06-21
How did you put it on disk - as a data file or did you use "burn disk image"? An ISO file is a "disk image" and usually needs to be burnt as such...

---

### Post by AndThenWhat on 2008-06-21
You cannot simply put an iso on a disc because it will not be bootable.  An ISO file is just an archive like a .zip file.  In order to use the contents, it must be unzipped.  You need a program like Nero to help you burn your ISO to a blank disc.

---

### Post by iaculallad on 2008-06-21
> **wavemaker said:**
> Gooday all. I got a disc on a magazine the other day and I downloaded an iso, put it on a disc and then tried to boot it on my computer. Well, that didnt work, so I spose there is more to it than what I did. Can one of you kind folk point me in the right direction. I am a fairly new user but I can usually follow instructions if they are clear to me. Regards, James.

Since it is an ISO file, you are not to burn it directly to your CD/DVD media  as a file but rather, burn it using the option "Burn Image" so as to extract all its file contents to your media including it's boot code. You can use NERO or any windoze burning software if you're using windoze right now.

Try reading this [Ubuntu Community HowTo]("https://wiki.ubuntu.com/BurningIsoHowto") for more information.

---

### Post by lisati on 2008-06-21
(Deleted by Lisati: post in hase, repent at leisure)

---

### Post by wavemaker on 2008-06-21
Thanks all for the input. I got that sorted, now I just have to fix the GRUB issue and I'm there. Your help is appreciated. James.

---

### Post by hyper_ch on 2008-06-21
what grub issue?

---

### Post by wavemaker on 2008-06-21
I have 2 hard drives on this machine. I keep hda  stable for my every day stuff and hdb is the one that gets all the experiments.  They have trouble talking to each other at times. So that is what I  have to fix.. Right now, even though I know that I  have Ubuntu installed on hdb, it is not showing in GRUB when I boot up. I have to do some cutting and pasting in the mbr to give me the options I want at boot.

---


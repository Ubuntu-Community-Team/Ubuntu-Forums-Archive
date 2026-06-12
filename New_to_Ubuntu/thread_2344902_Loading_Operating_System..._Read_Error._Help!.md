---
title: "Loading Operating System... Read Error. Help!"
date: 2016-11-28
forum: New to Ubuntu
---

### Post by mat.diahis on 2016-11-28
Hello, some months ago i decided to install Ubuntu 16.04 LTS alongside Windows7. Yesterday I had my first issue. When i turned ON my PC this appeared:
```
Loading operating system...
Read error
```

I tried pressing Shift at the start to pop up the Grub screen but it doesnt work. Ive also tried pressing F12 and booting from the Drive.
Luckily i still have the Linux Live Usb from where I installed Ubuntu. Im using it right now.

I ran the 'boot repair' program two times. The 2nd time it asked me to type in the Terminal some commands to purge and reinstall Grub both on Win7 and Ubuntu. Still isnt working.

The PasteBin: [http://paste2.org/1tLMOCLL](http://paste2.org/1tLMOCLL)

GParted: [ATTACH=CONFIG]272446[/ATTACH][ATTACH=CONFIG]272447[/ATTACH]

Windows is in sda2, sda3 is the extended, sda5 is Ubuntu and sda6 is the linux swap. No idea what's in sda1.

Some times (Like 1 out of 15) my PC starts normally.

Any help will be much appreciated :)

---

### Post by oldos2er on 2016-11-29
I would boot from your live USB, install [smartmontools]("https://help.ubuntu.com/community/Smartmontools") and test the drive (instructions are at the link). It sounds like it may be failing.

---

### Post by kingneutron on 2016-11-29
@oldos2er, I agree - if the drive is more than 3-5 years old it may need to be replaced. Hope original poster has backups...

--After installing smartmontools, to test the drive:
' smartctl -t long /dev/sda ' # wait for it to finish, it will print an ETA timestamp

then:

' smartctl -a /dev/sda |less ' # Review the SMART log

---

### Post by mat.diahis on 2016-12-02
@oldos2er @kingneutron Hello, i tried using the long drive test but after 12hs nothing happened...
[ATTACH=CONFIG]272505[/ATTACH]
   


This is what happends when i run the smartctl -a /dev/sda |less command
[ATTACH=CONFIG]272504[/ATTACH]

Same story with the short drive test.

Since yesterday I can access the grub screen, when i try to boot windows7 it asks me to insert a windows reparation cd... I can boot Ubuntu, but internet doesnt works, althought it recognizes my WiFi usb, weird.

Yeah..my drive is about 3 years old

---

### Post by yancek on 2016-12-02
sda1 is your windows boot partition which you can see in the GParted image you posted.  Look all the way to the right under the Flags column and you will see 'boot'.  That's standard on a windows 7 pre-installed system, a 100MB boot partition.

If you have a windows DVD or some windows tool, you could try running chkdsk on the filesystem (sda2).

---

### Post by oldos2er on 2016-12-02
> **mat.diahis said:**
> @oldos2er @kingneutron Hello, i tried using the long drive test but after 12hs nothing happened...
[ATTACH=CONFIG]272505[/ATTACH]
   


This is what happends when i run the smartctl -a /dev/sda |less command
[ATTACH=CONFIG]272504[/ATTACH]



You need to use "sudo" to view the report: ```
sudo smartctl -a /dev/sda | less
```

---

### Post by mat.diahis on 2016-12-06
@oldos2er  haha thanks :)

[ATTACH=CONFIG]272567[/ATTACH]   [ATTACH=CONFIG]272569[/ATTACH]


sorry @Yancek what do you mean with 

> If you have a windows DVD or some windows tool, you could try running chkdsk on the filesystem (sda2).

chkdsk..#-o

---


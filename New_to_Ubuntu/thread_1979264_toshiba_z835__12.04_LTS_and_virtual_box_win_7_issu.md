---
title: "toshiba z835  12.04 LTS and virtual box win 7 issue"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by idom on 2012-05-13
I want to run win 7 via virtual box over my toshiba z835. I have installed a fresh copy of 12.04 LTS.

Sequence of events
1. created a recovery media from toshiba
2. installed 12.04 as a fresh install
3. installed virtualbox 4.1 on the machine
4. now trying to use recovery media 16GB usb flash drive to use as my windows 7 booting however virtual box is not detecting usb it is not giving me option to use usb as a booting device. it just hows floppy/CD/HDD

Am I missing thing ? 


Any help is appreciated 
Regards,
idom

---

### Post by joetait on 2012-05-13
What is the image on the USB? Is it the same as one would have on a Windows install CD (I didn't even know that Windows offered USB installers if so!).

Anyway, if it is, I would think that you should be able to tell it is a HDD. However I am not 100%, so if back it up before you try.

---

### Post by idom on 2012-05-13
> **idom said:**
> I want to run win 7 via virtual box over my toshiba z835. I have installed a fresh copy of 12.04 LTS.

Sequence of events
1. created a recovery media from toshiba
2. installed 12.04 as a fresh install
3. installed virtualbox 4.1 on the machine
4. now trying to use recovery media 16GB usb flash drive to use as my windows 7 booting however virtual box is not detecting usb it is not giving me option to use usb as a booting device. it just hows floppy/CD/HDD

Am I missing thing ? 


Any help is appreciated 
Regards,
idom

screen shot is attached it clearly shows that USB is not a choice and I don't have an external cd drive. Is it possible to circumvent this problem

regards
idom

---

### Post by idom on 2012-05-13
> **joetait said:**
> What is the image on the USB? Is it the same as one would have on a Windows install CD (I didn't even know that Windows offered USB installers if so!).

Anyway, if it is, I would think that you should be able to tell it is a HDD. However I am not 100%, so if back it up before you try.

I don't exactly know what are you tryingto say however it does not look like in .iso thing. If I do ls in backupt usb following is the output 

odi@modiultrabook:~/Downloads$ ll /media/TI106339W0E/
total 444
drwx------ 7 modi modi   8192 Jan  1  1970 ./
drwxr-xr-x 3 root root   4096 May 13 15:08 ../
drwx------ 3 modi modi   8192 May 12 16:09 BIN/
drwx------ 3 modi modi   8192 May 12 16:10 BOOT/
-rw-r--r-- 1 modi modi 383786 Nov 20  2010 BOOTMGR
-rw-r--r-- 1 modi modi    187 May 12 16:07 DATA.INI
-rw-r--r-- 1 modi modi   1973 Dec 21 09:28 PLANDATA.INI
drwx------ 3 modi modi   8192 May 12 16:15 PLANFOLDER/
drwx------ 2 modi modi   8192 May 12 16:10 SOURCES/
-rw-r--r-- 1 modi modi      0 Jun 30  2009 !V6_00_03.VRP
drwx------ 3 modi modi   8192 May 12 16:08 ZZImages/

---

### Post by Mark Phelps on 2012-05-13
VB has problems detecting and mounting using USB.  Perhaps the info in the link below can help:

[http://www.howtogeek.com/howto/31726/mount-usb-devices-in-virtualbox-with-ubuntu/]("http://www.howtogeek.com/howto/31726/mount-usb-devices-in-virtualbox-with-ubuntu/")

---

### Post by idom on 2012-05-14
> **Mark Phelps said:**
> VB has problems detecting and mounting using USB.  Perhaps the info in the link below can help:

[http://www.howtogeek.com/howto/31726/mount-usb-devices-in-virtualbox-with-ubuntu/]("http://www.howtogeek.com/howto/31726/mount-usb-devices-in-virtualbox-with-ubuntu/")

thanks. I couldn't get my win 7 running on my ubutnu 12.04 LTS via VB. However I could get XP running without any problem. 


idom

---


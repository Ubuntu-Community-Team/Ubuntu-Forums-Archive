---
title: "Slow performance on my netbook"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by bobinho on 2012-09-23
Hello, I am a beginner and would like to improve my cpu performance. My netbook is very slow and I'm sure it shouldn't be this slow. Sometimes I can't see small videos and it takes forever to open firefox or a simple folder. I don't really think that ubuntu is the problem, but I don't know how to use it so I need some guidance from ubuntu users in order to diagnose and fix the problem. The reason I don't think the problem is the OS is because when I used windows 7 it was slow too. I thought changing to linux would make it a little faster. This thing used to be a lot faster, I don't know what happened.

I looked this up on sysinfo, I don't know if all of this information is relevant, but I'll copy it all:

Ubuntu 12.04 (precise)

CPU information:
Intel(R) Atom(TM) CPU N455   @ 1.66GHz

Memory information:
989 MiB
Free: 54%

Swap total: 1010MiB
Free: 63%

---

### Post by Lightstar on 2012-09-23
I have the same CPU and Memory / Ram as you on my second netbook.
Ubuntu was also slow on my netbook.  I went with Lubuntu instead, and it's much better.

I also switched to chrome / chromium instead of firefox.
Removed LibreOffice and used AbiWord.

Since netbooks are mini computers, it's best to go minimalist and use lighter applications.

---

### Post by NikTh on 2012-09-23
Hi , 

please try to login from ubuntu-2d session. It is much lighter. At login screen an login box (where you write your username&password) click the little Ubuntu Icon and select ubuntu-2d. 

I assume it will acting much better. 

Thanks

---

### Post by daslinkard on 2012-09-23
I agree with Lightstar that Lubuntu will be a smoother OS for you.

---

### Post by Galgotha on 2012-09-24
> **NikTh said:**
> Hi , 
 
please try to login from ubuntu-2d session. It is much lighter. At login screen an login box (where you write your username&password) click the little Ubuntu Icon and select ubuntu-2d. 
 
I assume it will acting much better. 
 
Thanks
 
I installed this to be auto login for wifes Netbook she hates not being able to go right thru. Is there a way to change this setting else where and reboot?
 
Also just a a note I found that the Atom N455 while a 64bit CPU has issue with the Ubuntu 64 loading up. I could us USB to boot into the OS but alone it would not so I reinstalled 32bit Ubuntu and was flying with no issues. I am beginning to wonder if the N455 interated GPU does not like 64 OS. Maybe a driver kernal issue, I didn't have time to figure it with Wife wanting it back. So resigned to 32bit on Netbook wouldn't matter anyway.
 
I am not having slow issue but I also have 2GB RAM in her system and have never seen her swap usage that high.

---

### Post by NikTh on 2012-09-24
> **Galgotha said:**
> I installed this to be auto login for wifes Netbook she hates not being able to go right thru. Is there a way to change this setting else where and reboot?

What settings ? Ubuntu-2D you mean ? You can change this with same way. OS remembers the last session and login you in with your last settings.
 
> **Galgotha said:**
> Also just a a note I found that the Atom N455 while a 64bit CPU has issue with the Ubuntu 64 loading up. I could us USB to boot into the OS but alone it would not so I reinstalled 32bit Ubuntu and was flying with no issues. I am beginning to wonder if the N455 interated GPU does not like 64 OS. Maybe a driver kernal issue, I didn't have time to figure it with Wife wanting it back. So resigned to 32bit on Netbook wouldn't matter anyway.
 
I am not having slow issue but I also have 2GB RAM in her system and have never seen her swap usage that high.

This is weird. Logically a 64 capable Cpu would run smoother with a 64 O.S 
Maybe something else is liable for this. 
How you installed Ubuntu ? With a LiveUsb or through Windows (wubi) ?

---

### Post by Galgotha on 2012-09-25
> **NikTh said:**
> What settings ? Ubuntu-2D you mean ? You can change this with same way. OS remembers the last session and login you in with your last settings.
 
 
 
This is weird. Logically a 64 capable Cpu would run smoother with a 64 O.S 
Maybe something else is liable for this. 
How you installed Ubuntu ? With a LiveUsb or through Windows (wubi) ?
 
Found how to switch to 2D, just had log out switch and log back in.
 
I was using LiveUSB so I am wondering if my installed ISO on that USB was bad.

---

### Post by Harpz on 2012-09-25
Tried running Ubuntu on my Acer Aspire One D250 netbook and it was a little slugish but usable.

Stopped using the netbook for some time but recently started again and installed Xubuntu 12.04 on it and i must say a massive improvement. 

Now use it for my XBMC skin development, I have wine, notepad++, Amazon Kindle PC App, Firefox and Thunderbird running flawlessly.

Just my 2cents :D

---

### Post by NikTh on 2012-09-25
> **Galgotha said:**
> 
I was using LiveUSB so I am wondering if my installed ISO on that USB was bad.

I guess if ISO was bad , then installation would not be completed. 

Performance issues usually generated due to low specs of hardware. 

If you saw performance difference with ubuntu-2d , this reinforces my opinion. 

Thanks

---

### Post by clanglois on 2012-09-25
I had the same problem,ubuntu was using about 70-90% ram (1GB), 95% of rooot partition 3.8GB and ran like treacle.

Lubuntu, now using 40-50% Ram [with 6 chrome windows and a terminal session open], and 1.3GB free on 3.8GB partition.

Vanilla ubuntu is just too fat for a Netbook 1G/1,6GHz

---

### Post by bobinho on 2012-09-25
Thanks for the tips, guys. I'll look into it.

---


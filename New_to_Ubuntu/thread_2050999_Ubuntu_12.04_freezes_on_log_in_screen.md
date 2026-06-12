---
title: "Ubuntu 12.04 freezes on log in screen"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by cthatch on 2012-09-01
Hey, I'm really new to Ubuntu and when I boot it up (I am dual booting windows 7 and ubuntu) I get to the log in screen and everything locks up. I can't move the mouse or type. I have tried to get to the text login but as I cannot use my keyboard when it's locked up that wont work. Any ideas?

thanks ahead of time.

---

### Post by NikTh on 2012-09-01
Hello . 

How installed Ubuntu ? via Wubi(from inside windows) 
or 
is a regular Dual boot with windows ? 

Thanks

---

### Post by cthatch on 2012-09-01
It is installed via regular dual boot with windows no wubi

---

### Post by NikTh on 2012-09-01
Hi , 
try to boot from recovery mode. If you succeed then click on root and apply below commands
```
mount -o rw,remount /
apt-get update
apt-get dist-upgrade
reboot
```Thanks

---

### Post by cthatch on 2012-09-01
I have tried to boot from recovery mode. When I click on recovery it freezes from the next screen. Mouse/keyboard and screen then lock up.

---

### Post by NikTh on 2012-09-01
Hello , 

If from the beginning , keyboard and mouse freezing , I don't think we can do much. 
We need at least the keyboard , to apply some commands. 

Can you attach another keyboard ? Is this keyboard and mouse you have , wireless ? 
What is the connection ? Wireless - usb , PS/2 ?  

Thanks

---

### Post by cthatch on 2012-09-01
My keyboard and mouse are both USB. They work up until the login screen or the screen after GRUB when clicking on recovery... I have no idea why they stop working but I can't get them to work at all.

I can get the command line to run from GRUB and my keyboard works. I cant figure out what is happening when it tries to load

Thanks

---

### Post by NikTh on 2012-09-01
Hi , 
maybe if you unplug and plug again the keyboard or/and mouse ? After the freezing i mean. 

If you can manage to give here some log files , that would be helpful. 

We want ```
dmesg >> dmesg.txt
cat /var/log/Xorg.0.log | grep -e EE -e WW >> xorgerrors.txt
```If you manage to run above commands either to terminal or console , you will have two helpful .txt files in your /home directory . dmesg.txt and xorgerrors.txt . You can open and paste the content here 

BUT 

Please put the results between ```
 brackets , so can be readable. Especially dmesg will be sufficiently large. 

[noparse][code]The Results Here
```[/noparse]

Thanks

---

### Post by cthatch on 2012-09-02
I have tried and tried again to unplug/replug in the keyboard. Doesnt work. And where do I type those commands in. Im new to linux still trying to learn my way around.

Thanks.

---

### Post by Bashing-om on 2012-09-02
cthatch;


  It is a shame you are having a rough introduction to ubuntu. We will try to get you up and going. With no more info about your system, diagnosis is spotty.

How bout reading through this tutorial:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

and we will pick up where you want/need to.

[INDENT]kindest regards <==BDQ
[/INDENT]

---

### Post by cthatch on 2012-09-02
Thanks so much for the tutorial! I was able to log in successfully. Installed my graphics drivers and I no longer have a freeze on the login screen!! However my mouse and keyboard are still unresponsive. Im using the razer black widow ultimate and the razer naga. Any ideas?

Thanks

---

### Post by Bashing-om on 2012-09-02
cthatch;

  Hey that is good news (you do good work)//

About the keyboard and mouse issue: Have you gone back to the simplest things. Plug in an ole basic usb (I stilll use ps/2 on 12.04) KB and mouse ? See if they are recognized ..


[INDENT]hth <==BDQ
 
[/INDENT]

---

### Post by NikTh on 2012-09-03
> **cthatch said:**
> However my mouse and keyboard are still unresponsive. Im using the razer black widow ultimate and the razer naga. Any ideas?

Hello , 

read here : [http://www.phoronix.com/scan.php?page=news_item&px=MTAzNzA](http://www.phoronix.com/scan.php?page=news_item&px=MTAzNzA) , maybe you figure out something.

Thanks

---

### Post by tptbd on 2012-09-03
I am new in this forum. You will get more information[ here.]("http://throughputtechnology.com")

---

### Post by cthatch on 2012-09-03
Plugged in an old mouse and keyboard and it worked fine! Seems that my keyboard and mouse aren't supported. Thanks for all the help guys!

---

### Post by Bashing-om on 2012-09-03
Not a problem, we are all in this together!

Suggestion: do some research for your desired keyboard/mouse ...Might be surprised to find a means to get them recognized.

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by cthatch on 2012-09-03
Ive been researching everywhere and apparently no one else is having a hard time fixing their keyboard/mouse. I borrowed a friends to try earlier and that usb one worked. I can sometimes plug my mouse it and it will work for like 30 seconds, but my keyboard never responds. idk whats going on.

EDIT: I am currently using the razer black widow ultimate and razer naga

Thanks for the help earlier thou!

---

### Post by NikTh on 2012-09-03
Hi , 
now you have a worked keyboard and mouse (even if are borrowed) try to test the Ubuntu 12.10 . 

Ubuntu 12.10 has the 3.5 kernel . If you keyboard and mouse work there , we can install the 3.5 kernel to your main installed (12.04) system. 

Download 12.10 from here :  [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

burn it to a Usb or CD/DVD and try it (not installation needed). 

Thanks

---

### Post by cthatch on 2012-09-04
I'll have to pick up some more blank CDs tomorrow ill let you know how it goes

Thanks:)

---


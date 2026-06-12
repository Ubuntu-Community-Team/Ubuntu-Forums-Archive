---
title: "Ubuntu first startup"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by DanRex on 2012-08-06
Hi! I'm new to the Ubuntu Forums and this is my first post so I'm not sure if this is the right category, but I hope you don't mind if it's wrong.
Now, to the subject:
I've been running Windows 7 but have made the decision to move to Ubuntu. I used Wubi for downloading and downloading went fine, after downloading, I rebooted and selected Ubuntu as the OS at startup. 
The Ubuntu loading screen showed up, and when loading was done, It was time to login. Now here's the problem.
I found it hard to move the cursor (very, very, very, laggy) and I couldn't click on anything or type in the password. After trying to type and pressing different keyboard-commands I had no other choice than shutting down (take out the power-cable).
I've tried startup two times after it, and the same thing is still happening.
What should I do? A answer would be much appreciated!

EDIT: If you need my system specs, you can find them here: [http://http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03029064&lang=en&cc=us&taskId=135&contentType=SupportFAQ&prodSeriesId=5151854&prodTypeId=12454]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03029064&lang=en&cc=us&taskId=135&contentType=SupportFAQ&prodSeriesId=5151854&prodTypeId=12454")

---

### Post by Laiquendi on 2012-08-06
If you're new then I will skip the virtual console method, simply try installing it from booting CD not from wubi :)
It's probably driver problem, if it'll still be the issue you my need to install driver via virtual console, or maybe someone will come up with better solution :)

Very nice hardware btw ;)

---

### Post by NikTh on 2012-08-06
Hi , 
I strongly recommend to remove wubi . Just remove it like you remove a regular program in Windows.
Make a LiveUsb and boot from there to see Ubuntu's behavior and support , with your hardware. 

You can easily make an Ubuntu LiveUSb with Unetbootin program --> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and you can make it from within Windows. 

Boot from Usb and click "Try Ubuntu" . Take a tour and see if everything work well. 
eg 
1)Graphics 
2)Camera (if you have)
3)Sound 
4)Internet (or/and wifi if you have).

The general idea is : "If it works well from Live session then will work just as well on a regular installation."
You can install ubuntu alongside windows (dual-boot).
If you want further help on dual-booting post back here. 

**My Opinion About Wubi: **
Wubi is a Virtual installation of Ubuntu , just to try Ubuntu from within Windows. However , wubi is a negative presentation of Ubuntu's Power. Imagine Windows run on VirtualBox. (maybe worst)
Ubuntu will be slower and problems might occur with boot etc . Because Ubuntu is not in a familiar Filesytem , but running on NTFS and because Windows control the installation. 
Just imagine an Ubuntu OS where running on NTFS and has a registry and wants defrag on hard disk ... etc. (God save us) 
If someone wants to try Ubuntu its much better from a LiveUsb (with persistent space If wants to test it for long time) rather wubi.  

Thanks

---

### Post by DanRex on 2012-08-06
Okay, Thank's for the reply's. I'll test em' hopefully I'll get Ubuntu working! :D

---

### Post by DanRex on 2012-08-07
Okay, So I tried NikTH's solution, It also looked good until I had to install... Same problem again. Couldn't click on anything, Ubuntu didn't recognize that I was typing but recognized mouse movement (laggy as before; BUT, this time, the lag stopped after lots of clicking).
I'm feeling very confused. Anyone feelin' smart that could help?
I would really, really, really start using Ubuntu!

---

### Post by NikTh on 2012-08-07
Hi , 
do you have a regular dual-boot now ? No wubi ?  
Please open a terminal(ctrl+alt+t) and give the result of 
```
sudo fdisk -l 
sudo parted -l 
cat /etc/lsb-release && uname -r
```                                  **Put the results inside ```
 tags by highlighting the output and then click on the  [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the message toolbar.**


Also try to update from terminal with these 2 commands 

[code]sudo apt-get update 

sudo apt-get dist-upgrade
```
Thanks

---

### Post by DanRex on 2012-08-08
I have UNetbootin now, so you mean I should press Ctrl+Alt+T in Windows; when? At booting?

---

### Post by Shadius on 2012-08-08
> **DanRex said:**
> I have UNetbootin now, so you mean I should press Ctrl+Alt+T in Windows; when? At booting?

No, in Ubuntu. It will open up the Terminal so you can input the commands.

---

### Post by DanRex on 2012-08-08
Okay, I'll test it right away! :)

---

### Post by DanRex on 2012-08-08
Right, from the sudo-commands I got the same answer all the time:
/bin/sh: sudo: not found

And from the cat-command I got the answer:
cat:can't open '/etc/lsb-release && uname -r

What should I do now?

---

### Post by DanRex on 2012-08-08
*little bump* I really need help!

---

### Post by NikTh on 2012-08-08
Hi , 
Sorry but I must misunderstood , I think. 

Follow these steps please. 

1)Boot in to windows and do 2 things 
a)Delete Ubuntu (wubi) installation. Go to Control Panel and remove Ubuntu like any other program in windows.
b) Make a defrag. Windows have native tool for this. 
After above , 
2) boot from Usb (Usb you made with Unetbootin) and when menu show up , press "Default" . 
Then test Ubuntu for a little (if you want) and see if is Ok with your hardware. 
3) Install Ubuntu . You will see this option on Desktop "Install Ubuntu 12.04" . Click there and Installation will start. Choose the option " Install Ubuntu alongside windows" and follow the guide (fill out  name - location - password ... etc) 
When installation finish , reboot your computer and unpug the Usb . 
You will see grub menu and you will be able to boot either windows or Ubuntu. 
I am wait the news 
Thanks

---

### Post by DanRex on 2012-08-08
Well, step 3 is something I can't do! As I already said; I can't click on anything; or type anything! It just recognizes mouse-movement!
The only place where I can type is the Terminal!

---

### Post by NikTh on 2012-08-08
> **DanRex said:**
> Well, step 3 is something I can't do! As I already said; I can't click on anything; or type anything! It just recognizes mouse-movement!
The only place where I can type is the Terminal!


Hi , 
so your problem is specific to mouse clicking. Can you test another mouse ? (do you have?) 
Is this a Usb mouse ? If yes , then check the BIOS for "Legacy Usb" support option. 


I don't know if there is a command to Install Ubuntu via terminal. 
Thanks

---

### Post by DanRex on 2012-08-08
I'll try another mouse (yup, both the keyboard and mouse are wireless).

---

### Post by DanRex on 2012-08-09
Didn't help; anyone able to help/have suggestions about what I could do?

---

### Post by NikTh on 2012-08-09
> **DanRex said:**
> I can't click on anything; or type anything! **It just recognizes mouse-movement!**
**The only place where I can type is the Terminal!**

Hi , 
I wonder.... "wireless adaptor sees well the mouse ? " 
another query "mouse has batteries? are full ? "
Thanks

---

### Post by DanRex on 2012-08-09
Well, The Wireless mouse and keyboard work perfectly on Windows; I see no reason for them to not work on Ubuntu!

---

### Post by NikTh on 2012-08-09
> **DanRex said:**
> Well, The Wireless mouse and keyboard work perfectly on Windows; I see no reason for them to not work on Ubuntu!

Hi , 
I also have a wireless mouse and keyboard combo and are working flawlessly from the first time.
So forgive my queries . I just try to understand why ! 

Did you check the BIOS for "legacy usb" support ? 
Thanks

---

### Post by DanRex on 2012-08-09
> **NikTh said:**
> Hi , 
I also have a wireless mouse and keyboard combo and are working flawlessly from the first time.
So forgive my queries . I just try to understand why ! 

Did you check the BIOS for "legacy usb" support ? 
Thanks

How do I do that? 
And Forgive me my way of explaining things; quite hard to understand? (especially when there are multiple problems!)

---

### Post by NikTh on 2012-08-09
Hi , 
when computer boots you must press a key (at mine is F12) . You will see at down page something like "Press F12(or del or something else) for setup". When you press that key , BIOS configuration page will come up . **Be careful there what to change**. Just try to find something similar to "Usb Legacy" and if is disabled , you must enable it. 

Something else . Did you try to change usb port of Usb wireless adaptop ? If not , try it. 
Thanks

---


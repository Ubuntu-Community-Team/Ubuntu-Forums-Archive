---
title: "installed from a purchased CD lubuntu and deleted windows-- still dead"
date: 2015-12-18
forum: New to Ubuntu
---

### Post by emo666 on 2015-12-18
I tried downloading from internet to windows XP pro 2006 laptop- passed memory & cache test--stopped by windows-- purchased a cd from amazon bypassing windows--did not install to computer--still no good--reran and deleted windows --now nothing.   I have gone thru this forum and it's way to technical and confusing to me.--- I was expecting the CD to be more user friendly in laymans terms.  Would like to use this computer again. What do I do to get it working.

---

### Post by ian-weisser on 2015-12-18
Basically, all you have told us is "I tried to install and failed."
That's not enough information to help you.
Sorry, but we need to know a lot more detail.

Did you 'Try Lubuntu'? Did it work?
When you tried to install, what happened? How long did it take? Did it ask you any questions? What were your answers?
What was the last thing that worked?
Did you see any error messages or warnings? What did they say?

When you boot now, what do you see? Does the system POST? Do you see a manufacturer logo? Is there any text or message at all?

---

### Post by coldraven on 2015-12-19
Hi and welcome to the forum.
A couple of questions:
What version of Lubuntu did you buy?
Did you ever get the CD to boot? You may have bought a 64 bit version, your PC may only be 32 bit. (you have to change the boot order in the PC's BIOS)

If you go here and select Lubuntu version 14.04, then scroll down to download options. I usually get the torrent link, it normally downloads very fast on my 4MB/s connection (less than half an hour)
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Also search for how to create a bootable USB stick, it saves wasting a CD and installs faster.
Edit: This is one method there are others available
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by emo666 on 2015-12-19
Thanks for your help---reran the CD and windows reappeared --rebooted and got error firefox is running cannot connect--CD recommended shutdown then hit enter . Put CD back in and rebooted now I have nothing but the pointer and a black screen.  Surprised that windows came back as I selected to omit it before and had nothing for a while.  I made sure in windows that I had internet connection before I rebooted. I elected to have the option of demo but never went there after shutting down and restart after reboot.

---

### Post by yancek on 2015-12-19
I'm not sure I understand the problem but did you change the boot priority in the BIOS to boot first from the CD?  If the CD is good, it would not boot to windows if you did this.  I don't know how you could possible get a message about firefox from the Lubuntu installer?  You might take a look at the link below which explains how to install Ubuntu which uses the same installer as Lubuntu. 

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by stalkingwolf on 2015-12-21
at a guess id say the computer is not shutting all the way down at reboot.    also sounds like a low ram problem.  but with out more info who knows.

---

### Post by emo666 on 2015-12-23
Still trying (without success) to load Lubuntu to 2006  gateway laptop with AMD turion64 chip from $12.95 CD from amazon. I get thru all the prompts and get lubuntu to work on trial--- select to load on computer from start ICON on lubuntu.   it shows 3 dots of 7 and a circle in motion that its installing.  Still no error messages--goes on for around 5 minutes then everything goes blank--and stays that way till I can't hear the player working.  Arrow is gone and nothing can be activated  --3 hours later shut down laptop -- restart and boots to windows and no sign of lubuntu  anywhere.  found something under cookies but just numbers and letters.   It gives no reason or error notification.  I elected to download software and updates while loading.

---

### Post by Bucky Ball on 2015-12-23
If it is a CD from Amazon and not an official Lubuntu CD (which I don't think they sell anymore) then anything could be happening. Anyone can burn a couple of dozen CDs and flog them on the internet. There is no quality control going on there.

Suggest you [download Lubuntu from the official source]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS#Downloading_Lubuntu_LTS"), create install media, either USB or disk which we can help you do, and boot from that and try again.

Some more research and a plan sounds like a good idea as at the moment you appear to be booting from the disk and hoping for the best without too many ideas of what is supposed to, or you are going to make, happen. No offense, just saying. A plan is the best way, pencil and paper, before going near the digital.

---

### Post by mörgæs on 2015-12-24
From a live boot with wired internet access please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

It will show us your hardware details.

---

### Post by yancek on 2015-12-24
The link below is to a very detailed tutorial on installing Ubuntu.  Should work for Lubuntu as it used the same installer.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---


---
title: "Ubuntu 11.10 is slow"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by muhtar on 2011-10-22
Hi guys,

After a lot of reading I installed Ubuntu for the first time. 11.10 Ocelot.

Now installation almost went perfect. My intention was to have a full Ubuntu install. Not a wubi. 
I popped in the cd during restart, follow the steps. Then I choose "install next to Windows", it was the first of three options. Then it rebooted I got in windows. A small window popped up like the one from wubi, but it didn't say wubi... I filled it in and pressed install, AND THEN... At the very last moment I got an error, I get this error that it couldn't find a particular file... I clicked ok, rebooted and luckely it was allright. I have a dualboot with Vista now...

Now, exploring Ubuntu what really overwhelms me is how slow it is!!! opening applications, systemsettings, .. all takes too long! Like an old Windows PC with slow internet browser! yeah you know what I mean!! Something is or went wrong.. I don't believe Ubuntu normally should act like this.. So I need you guys help!

What I already noticed is the following:
Systemsettings: Driversoption: there are 4 different lines for my graphics card, 1 for a modem (internet is already working). I have a Nvidia Geforce 9500MS. The 4 different lines have grey dots in front of them. so I try to install them. I have to do this one at a time.. So installing the first one, it requires a restart of the system. After restart there's a green dot infront of the first line. Then I install the second one, restart needed.. After restart GREY DOT infront of First one, green infornt of second. If I install the third one, all the rest is grey only third is green and so on and so on. What the deal with this!?

I felt a speed boost, graphics wise, after one of those installations...

What can I do? Do I have to install all of them or is this behaviour normal? Why could ubuntu be so slow? Could it be that not every hardware is being used because of non available Linux drivers?? 

That a lot of story for a beginner hé :).. But I really need this guys.

---

### Post by Spyderkid on 2011-10-22
Just as a notice... Ubuntu is no slower normally than windows, generally it's faster.

I'm afraid your install has somehow seriously screwed up...

try booting into recovery mode and run a hard disk check from the list of availiable options.
[COLOR="Red"]
(also i believe there is an option if you boot from a live CD/USB there is an option to "fix Ubuntu" or something along those lines[/COLOR]

---

### Post by mörgæs on 2011-10-22
Changed the title to a less dramatic one.

If Ubuntu is slow, which a lot of people report, then Xubuntu is worth trying.

---

### Post by plasmafusion on 2011-10-22
tried the 11.10 beta in a vm with 1GB of RAM and it ran fine. could have used it daily quite happily. would imagine the final release would be the same.
as morgas suggested you could try xubuntu or even lubuntu (which i use). slimmer desktop environments = snappier feel.
if you're sticking with ubuntu make sure your nvidia drivers are correctly installed see [here]("https://help.ubuntu.com/community/NvidiaManual") if you're having trouble

---

### Post by muhtar on 2011-10-23
I don't want to use Xubuntu or Lubuntu.

My laptop is a Asus A7SN, this should be way enough for Ubuntu I guess!?

@ plasmafusion
I looked at the driver installation page but that's a little over my head. I'm a Linux noob. I don't know anything about coding or commandline actions...

I'm gonna do a fix and see furhter on...

I can't believe this is so complicated!! Isn't Ubuntu also for noobs who just want a free,stable and fast OS!?! You know... like the eas of Windows..

Please help guys..

---

### Post by Linux_junkie on 2011-10-23
There could be a whole host of things slowing down your Ubuntu, without knowing much about your system (RAM; processor; graphics card etc.) we cannot really help you.   It could also have been a problem with the installation.

More information needed please.

---

### Post by muhtar on 2011-10-23
Linux junkie

these are my specs:

processor: Intel Core 2 Duo Mobile T8300
ram: 4GB
graphics card: Nvidia 9500M GS

My laptop is a ASUS A7SN

Thanks!

---

### Post by Linux_junkie on 2011-10-23
> **muhtar said:**
> Linux junkie

these are my specs:

processor: Intel Core 2 Duo Mobile T8300
ram: 4GB
graphics card: Nvidia 9500M GS

My laptop is a ASUS A7SN

Thanks!

The RAM and processor won't be a problem but the problem could be with the graphics card you.  From reading threads on these forums there seems to  be a problem with Linux and NVIDIA.  I personally would search web for latest NVIDIA driver for Ubuntu.

Found this post.   Might help you. [http://ubuntuforums.org/showthread.php?t=1192385](http://ubuntuforums.org/showthread.php?t=1192385)

---


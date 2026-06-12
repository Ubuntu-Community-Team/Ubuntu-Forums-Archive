---
title: "HOWTO: Create a custom LiveCD of your system (distributable) Ubuntu 8.04 LTS"
date: 2008-10-02
forum: Outdated Tutorials &amp; Tips
---

### Post by arkticcool on 2008-10-02
**This tutorial will explain,** in what I believe to be, the simplest way to backup your system into a distributable LiveCD/DVD, with or without your personal data. This is done using a wonderful little utility called Remastersys. This utility can back up your personal data in a custom bootable LiveCD (a .iso that can be burnt to a CD/DVD, size permitting). Or it can create a distributable copy of your entire system, exempting your personal files (useful for systechs that need to install ubuntu on multiple machines without a network).
[COLOR="Red"]
THIS HOWTO DOES NOT COME WITH ANY WARRANTY/GUARANTEE IN ANY WAR OR FORM, USE AT YOUR OWN RISK.[/COLOR]
[B]
Prereq's;[/B]

[LIST]
[*]Depending on the size of your system between 3-5 GB of extra space on you hard drive to store the .iso temporarily.
[*]Knowing how to burn .iso's. [Don't know go here]("https://help.ubuntu.com/community/BurningIsoHowto")
[*]Admin privileges.
[*]A DVD/CD burner that works.
[/LIST]

**Installation: (Remastersys)**

First you need to add Remastersys to your repository.

Open Terminal **(Applications > Accessories > Terminal)**

Type in the following;
```
sudo gedit /etc/apt/sources.list
```
Scroll to the bottom of the list that appears and add the following;
```
# Remastersys
deb http://www.remastersys.klikit-linux.com/repository remastersys/
```

Save the file in gedit, and exit. We have now added Remastersys so that it can be easily downloaded/updated.

Go back to Terminal and type in the following to update the repository;
```
sudo apt-get update
```
Now for the installation of Remastersys;
```
sudo apt-get install remastersys
```
It may state that remastersys is an untrusted source or something like that I forget, just type in y and continue. [You can find more information on it here.]("http://en.wikipedia.org/wiki/Remastersys")
[B]
Creation of customized LiveCD/DVD;[/B]

Remastersys offers a variety of options to create your copy. And all it takes is two lines of code. The first to create the .iso, the second to clean out all the temp. files Remastersys created.
[B]
Here's the syntax if your more advanced;[/B]

```
sudo remastersys backup|clean|dist [cdfs|iso] [filename.iso]
```
**For newer users here are your options;**

A complete backup of your system, which includes your system and your personal files type in the following into the Terminal;
```
sudo remastersys backup
```

If you want the .iso to have a special name simply type the following;

```
 sudo remastersys backup example.iso
```

Where example is the name you want to call the .iso.

Another option would be to create a distributable LiveCD of the entire system without having your personal files (Home etc.) on the disk.

To do this simply type in the following;
```
sudo remastersys dist
```

When this is complete you can find the .iso in /home/remastersys. Burn that to a CD if its smaller than 700mb, or a dvd if its larger than that. If you don't know how to, refer back to my prereq's, there is a link on how to do it in Ubuntu.

Once the .iso is burnt you'll want to clean up your system of the files remastersys created. Type in the following command to do so;
```
sudo remastersys clean
```

If you would like to view the codes from the Remastersys help file simply type in the following in a list of codes will pop up. It will also state what each command does;
```
sudo remastersys
```

And voilla, you've created a bootable LiveCD/DVD, with your personal files and all your configurations, or a distributable CD/DVD that you can install on any computer. In a few easy steps.

This tutorial shows one how to customize their backup with the remastersys syntax. Remastersys was created by Tony Brijeski a.k.a. Fragadelic (if you wish use the GUI which is located under **System > Adminstration > Remastersys Backup**)

---

### Post by Fragadelic on 2008-10-06
...or you could just use the "Remastersys Backup" gui from the System Menu.

The gui is now in complete sync with the backend so there should be no reason to run it from cli unless you really prefer that method.

2.0-7 also fixed a nagging bug that I hadn't even counted on - user choosing a livecd username with uppercase letters.  Both the gui and backend change the case of the livecd username to lowercase.

Thanks for taking the time to put this little howto up.

BTW, I am the Fragadelic that wrote remastersys.

---

### Post by shaon3343 on 2009-11-11
[SIZE=2]**Will it work  for Ubuntu 9.04? I'm using Ubuntu 9.04.I've created an iso of my system with this remastersys. After Burning it , when i use it as a live dvd, a login screen appears which prompt me for username and password!!! How could I find that username and password for this live dvd? Please help me.**[/SIZE]
                                             [SIZE=2]**                            shaon**[/SIZE]

---

### Post by redwaldmcmanus on 2009-11-11
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)
Appears so ;-)

---

### Post by shaon3343 on 2009-11-11
**hi,[]("http://ubuntuforums.org/member.php?u=321213")i went to the link given by [redwaldmcmanus]("http://ubuntuforums.org/member.php?u=321213") but I still cant find it. :( I've created that iso image of my system using the GUI of remastersys as described above. But the live dvd prompt me to login with my username and password!! How could I find those username and password? Please help me. :(**

---

### Post by Tclarkie on 2009-11-12
'cause its practically turning your hhd into a live cd, try your norm' linux password

---

### Post by shaon3343 on 2009-11-12
**Yes I tried with my current linux password and i also tried by keeping both the field blank but no way. any help?**

---

### Post by gadolinio on 2009-11-29
I have the same problem... Don't know what password does the livecd want... Doesn't it start a liveuser's session??

---

### Post by grndslm on 2009-12-15
You guys could try harvesting a ton of tips from my expansive Remastersys Guide:

[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)

I will be cleaning up information toward the beginning of the guide VERY soon.  Still haven't gotten myself completely organized and just ordered new disks for myself.  Weee...  a 30 GB OCZ Vertex SSD and 500 GB 2.5" portable drive with built-in USB and "padlock" for AES encryption for security! ;)  Both of those for $195 after rebates!!

AND THEN I'll be diving back into the Remastersys scene full force...

Hope you guys can get some use out of my guide.  Bump it if you get 9.10 to work, which it should definitely if you use the right repository. ;)

---


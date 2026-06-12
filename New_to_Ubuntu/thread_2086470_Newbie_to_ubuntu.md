---
title: "Newbie to ubuntu"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by judyhenry646 on 2012-11-21
How do i operate linux? I installed ubuntu from my friend but don't know how to operate? I need help to uses on daily basis.
My daily Basic requirement which i wanna use in ubuntu. 
MS office(Specially word,powerpoint and excel) or same functioning software for Ubuntu OS
Notepad
Skype
gtalk
Internet download manager
Any PDF Reader

Please Give me software names or any alternative solution and how to use those software (any help section links)

---

### Post by squakie on 2012-11-21
MS office(Specially word,powerpoint and excel) or same functioning software for Ubuntu OS

  [COLOR=DarkRed]- LibreOffice should have been installed by default

[/COLOR] Notepad

  [COLOR=DarkRed]- try gedit (or "text editor" in the unity menus)

[/COLOR] Skype

[COLOR=DarkRed]  - you can install this via "sudo apt-get install skype" or in the software center

[/COLOR] gtalk

  [COLOR=DarkRed]- don't know what this is

[/COLOR] Internet download manager

[COLOR=DarkRed]  - several are available - check the software center

[/COLOR] Any PDF Reader

[COLOR=DarkRed]  - one should have installed by default, but they are in the software center[/COLOR]

---

### Post by mastablasta on 2012-11-21
> **squakie said:**
>  
gtalk
 
[COLOR=darkred]- don't know what this is[/COLOR]

 
maybe google talk? if so then then default pidgin is one of the many options.
 
anyway to the OP open software center, find what you want, installa and you are good to go.
 
note that MS office doesn't work in linux. You may try to get certain versions working using Wine (or play on linux for nice graphcis interface...)
 
Libre office, Lotus office, Caligra Suite are available in linux.

---

### Post by DuckHook on 2012-11-21
> **judyhenry646 said:**
> How do i operate linux?

Please Give me software names or any alternative solution and how to use those software (any help section links)

A very helpful site for new users is psychocat's:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by mlentink on 2012-11-22
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

---

### Post by judyhenry646 on 2012-11-29
thanks you all and i download the ubuntupocketguide and learn it from it. great help ...it's easy to use after 1 week. Few days i really messed up but now ubuntupocketguide help me lot.

---

### Post by andrew.46 on 2012-11-29
gedit is a slightly heavy replacement for Windows Notepad, have a look at Leafpad by finding it in the Soaftware Centre or copying and pasting the following into a terminal:

```
sudo apt-get install leafpad
```

And I hope you are enjoying Ubuntu :)

---

### Post by monkeybrain2012 on 2012-11-29
Your friend should have set up all that for you and spend at least half an hour teaching you how to use it. I am very thorough when I set up Ubuntu for my friends. I install and test all the applications they need and do the necessary tweakings (if any) and then spend half an hour to an hour showing them how to use it:)

Skype,

You need to first activate the Canonical's partners repository (sudo apt-get install skype won't work otherwise)

To do that open the Software Centre and go to Edit > Software Sources > Other Software and check the box "Canonical's Partners" then reload the Software Centre you should be able to find Skype in the SC

The Software Centre is flashy but very slow and heavy on resources, I recommend you use the synaptic package manager ( to enable the Partner's repository in Synaptic go to Settings > Respositories > Other Software) Which is fast and flexible, you can install it from the Software Centre (then you will never need the SC again) or in the terminal

```
sudo apt-get install synaptic
```

There may be occasions you want to install a downloaded deb (like a Windows installer) by right clicking it (for example, gtalk)

By default if you right click a .deb  the Software Centre will try to install it but it takes a long time, so instead you would like to install gdebi 

You can install it through the Software Centre or in the terminal

```
sudo apt-get install gdebi
```

For google chat download a .deb from its website (choose 32 or 64 bit depending on your architecture)

[https://www.google.com/chat/video/download.html](https://www.google.com/chat/video/download.html)

After downloading the .deb, right click it choose Properties > Open With and make gdebi the default application to open .deb files. Then you can install it by clicking it. It will also set up a google talk repository and you can get updates regularly through the package manager.

I don't install any standalone download manager I use the DOwnThemALl addon for Firefox.

---

### Post by SeanIM on 2012-11-30
They've already given you some great links here...but from personal experience Ubuntu is very user friendly for the most part.

Just don't be afraid to click on things and explore the system.  After a few weeks you'll love it.

---


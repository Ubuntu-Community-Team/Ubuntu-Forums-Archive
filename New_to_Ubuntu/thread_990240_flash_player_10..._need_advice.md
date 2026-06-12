---
title: "flash player 10... need advice"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-11-22
i will be installing ubuntu x64 this week and i wanted to make sure flash player 10 will install with no issues ? i know there's a alpha x64 flash player but im talking about a more stable build ? will regular flash 10 install, if so how ?

---

### Post by philinux on 2008-11-22
Just install ubuntu-restricted-extras.

---

### Post by Idefix82 on 2008-11-22
I strongly recommend you the 64 alpha version. It works much better for me than the nspluginwrapper solution did, which is what you would have to use to install the 32 bit version.
Most feedback I have read is very positive and the 64 bit alpha version seems to be very stable.

---

### Post by smooth3006 on 2008-11-22
> **philinux said:**
> Just install ubuntu-restricted-extras.

will that install flash 10 on my x64 system ?

---

### Post by smooth3006 on 2008-11-22
> **Idefix82 said:**
> I strongly recommend you the 64 alpha version. It works much better for me than the nspluginwrapper solution did, which is what you would have to use to install the 32 bit version.
Most feedback I have read is very positive and the 64 bit alpha version seems to be very stable.

is there a guide on how to install ? is it in a deb form ?

---

### Post by mikewhatever on 2008-11-22
Sorry to tell you, but you can't make sure there are no issues.):P

---

### Post by smooth3006 on 2008-11-22
> **mikewhatever said:**
> Sorry to tell you, but you can't may sure there are no issues.):P

huh ?

---

### Post by TheLions on 2008-11-22
> **smooth3006 said:**
> is there a guide on how to install ? is it in a deb form ?

it easy, download it, extract it and copy it to /home/username/.mozilla/

---

### Post by NESFreak on 2008-11-22
> **smooth3006 said:**
> will that install flash 10 on my x64 system ?

flash 10 + anything else you will need for your os that couldn't be included by default. (like codecs and winrar support) And even though i can not guarantee it that it won't turn your pc in a mech-robot which goes killing-spree [http://www.southparkstudios.com/clips/153342](http://www.southparkstudios.com/clips/153342) , i can assure you it did the trick on my 64-bit intrepid install on my dell m1330.

---
lol just realised you need flash for this clip.

btw i was refering to the reply to apt-get ubuntu-restricted-extras

---

### Post by Bablefish on 2008-11-22
You can get the deb form from Adobe itself

---

### Post by smooth3006 on 2008-11-22
> **Bablefish said:**
> You can get the deb form from Adobe itself

i checked adobe, i don't see any x64 deb ?

---

### Post by malrost on 2008-11-22
It'll install alright. While it's an alpha release, I've found Adobe's 64 bit Linux version much, much better than the prior 32-bit + nspluginwrapper workarounds. It will install, I've finally been able to watch the Daily Show on 64 bit Ubuntu again, but YMMV.

More explicit directions:

Download the file here:

[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

Extract it. (Right click, extract.)

It will create an .so file. Copy the .so file to the appropriate directory (I believe it's either /usr/lib/mozilla/plugins/ or /usr/lib/firefox-addons/plugins/ ...I wasn't sure and just copied it to both.)

Restart Firefox, et voila.

You can double check the install at the Adobe flash player test page: 

[http://www.adobe.com/shockwave/welcome/]("http://www.adobe.com/shockwave/welcome/")

I'm not sure about TheLions' choice of directory --mine isn't in /home/username/.mozilla and the flash plugin works. Might be a different layout, I'm still using Hardy, not Intrepid. (And I don't see a .deb file on Adobe's page either.)

---

### Post by chhipmunk on 2008-12-01
I downloaded flash palyer 10, but i couldn't install it. It says
 E: Couldn't find package install_flash_player_10_active_x.exe
I tryed apt-get update, but nothing changed.
Can you help me?

---

### Post by fr.theo on 2008-12-01
try this sudo dpkg -i install_flash_player_10_linux.de or go to this site

[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

or download the deb file form here


[http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ) 

NOTE: make sure you select your operating system from the drop down list

in adobe ".deb for ubuntu 8.04


I have installed it works very well for me

---

### Post by fr.theo on 2008-12-01
try this thread, one of my own when i had trouble with flash player


[http://ubuntuforums.org/showthread.php?t=954349](http://ubuntuforums.org/showthread.php?t=954349)

---

### Post by chhipmunk on 2008-12-01
# sudo dpkg -i install_flash_player_10_linux.deb
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 120193 files and directories currently installed.)
Unpacking adobe-flashplugin (from install_flash_player_10_linux.deb) ...
dpkg: dependency problems prevent configuration of adobe-flashplugin:
 adobe-flashplugin depends on libcairo2 (>= 1.6.0); however:
  Version of libcairo2 on system is 1.4.10-1ubuntu4.4.
 adobe-flashplugin depends on libnss3-1d; however:
  Package libnss3-1d is not installed.
 adobe-flashplugin depends on libpango1.0-0 (>= 1.20.1); however:
  Version of libpango1.0-0 on system is 1.18.3-0ubuntu1.
dpkg: error processing adobe-flashplugin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobe-flashplugin



What does this mean?

---

### Post by chhipmunk on 2008-12-01
I installed Package libnss3-1d.

---

### Post by TheLions on 2008-12-02
you need newer versions of libcairo2 (>= 1.6.0),libpango1.0-0 (>= 1.20.1),

---

### Post by gandaran on 2008-12-02
> **chhipmunk said:**
> # sudo dpkg -i install_flash_player_10_linux.deb
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 120193 files and directories currently installed.)
Unpacking adobe-flashplugin (from install_flash_player_10_linux.deb) ...
dpkg: dependency problems prevent configuration of adobe-flashplugin:
 adobe-flashplugin depends on libcairo2 (>= 1.6.0); however:
  Version of libcairo2 on system is 1.4.10-1ubuntu4.4.
 adobe-flashplugin depends on libnss3-1d; however:
  Package libnss3-1d is not installed.
 adobe-flashplugin depends on libpango1.0-0 (>= 1.20.1); however:
  Version of libpango1.0-0 on system is 1.18.3-0ubuntu1.
dpkg: error processing adobe-flashplugin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobe-flashplugin

What does this mean?
the adobe-flashplugin package is only for ubuntu 8.04 and 8.10
which version of ubuntu you running? for older ubuntu versions you download the tar.gz package

---

### Post by Papa-san on 2008-12-02
> **mikewhatever said:**
> Sorry to tell you, but you can't make sure there are no issues.):P

The OP said "huh?" in reference to this post, so...

Ubuntu is Open Source.
You are going to experience 'issues' with the setup of your system. That is just the nature of an Open Source Operating System. Each hardware configuration is different. People like you and me do the work, not a corporation. When you run into problems, you ask (nicely) for help here, and usually get the help needed. 

I can offer a bit of advice for when you do get it set up and working the way you like it:
Turn off the auto update manager. Every once in a while, make a backup and run it manually to see if there are security issues you need to protect yourself from. If you keep it running and 'update' everything, eventually you will install an update that will break your system. 

Welcome to the Ubuntu Community!

---

### Post by markbuntu on 2008-12-02
If you install packages from beyond the repos you will run into problems at some point, guaranteed. You can also run into occasional problems with packages from proposed but personally I have not seen that in the last 6 months running both Hardy amd64 and i386.

Anyway, I just installed Intrepid amd64 a few days ago and got the ubuntu-restricted-extras package and have had zero problems with flashplayer.

I am still running flash10rc, the original not rc2, on my Hardy installs with no problems so I will keep it until it does not work anymore. Hey, if something works, why mess with it.

One thing to keep in mind here, just because something has been updated does not mean it is better for you. Best to sit back for a while and watch the forums.

---

### Post by stchman on 2008-12-02
> **smooth3006 said:**
> i will be installing ubuntu x64 this week and i wanted to make sure flash player 10 will install with no issues ? i know there's a alpha x64 flash player but im talking about a more stable build ? will regular flash 10 install, if so how ?

For Intrepid there is Flash 10 in the repos.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by crav on 2008-12-02
> **stchman said:**
> For Intrepid there is Flash 10 in the repos.

```
sudo apt-get install flashplugin-nonfree
```

```
sam@Mouse:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flashplugin
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 1 to remove and 124 not upgraded.
Need to get 0B/18.7kB of archives.
After this operation, 9933kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 96232 files and directories currently installed.)
Removing adobe-flashplugin ...
(Reading database ... 96228 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--18:55:39--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.210.70
Connecting to fpdownload.macromedia.com|72.247.210.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:55:40 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

```

---

### Post by chhipmunk on 2008-12-07
ok. thanks a lot

---

### Post by zika on 2008-12-07
64-bit flash is definitely worth using.

```
sudo apt-get --purge remove flashplugin-nonfree nspluginwrapper
wget [http://download.macromedia.com/pub/l...6_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz")
tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so ~/.mozilla/plugins/
(create plugins dir if it doesn't exist)
```Enjoy!

(If You did not install flashplugin-nonfree do not be disturbed with warning messages ... Do a "tar" command in the directory where You have downloaded compressed file.)

---


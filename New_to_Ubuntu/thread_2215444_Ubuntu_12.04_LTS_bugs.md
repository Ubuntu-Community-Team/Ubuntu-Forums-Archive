---
title: "Ubuntu 12.04 LTS bugs"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-04-06
I am having trouble with what appear to be Ubuntu 12.04 LTS bugs; and it is getting progrssively annoying. I have downloaded and installed all the latest updates. I am wondering if I can do anything about these bugs:

1) Lack of complete boot up: the boot up process stops at a blank pink screen with the mouse arrow in the middle of the screen. The arrow will move, but there are no icons, even after an hour or more. So I have to restart/reboot the PC by manually powering off, then repowering the PC with the power button.

2) The PC "freezes" by a) the mouse pointer no longer moving and (I think) icons no longer responding to clicking the mouse, b) the mouse pointer continues to move, but icons no longer responding to clicking the mouse. If I turn on the touchpad, which is generally off, it's also the same thing ( a) or b) ) with the touchpad. Sometimes the PC will respond to the "alt button" on the keyboard, sometimes not. Sometimes ctrl + alt + t brings up a terminal, sometimes not. I have to reboot to overcome the problem.

3) Lately the PC either cannot connect to the internet or stops transmitting/receiving internet bytes, even though the wired connection (according to Ubuntu 12.04 LTS) is "connected." I have to reboot to overcome the problem.

QUESTION: Is there anything I can do anything about these bugs?

Thank you,

R.

---

### Post by kurja on 2014-04-06
Something's broken in your system if it's doing that.... When having one of these freeze-ups, are you able to open a virtual console by hitting ctrl+alt+F1? (ctrl+alt+F7 reverts to your GUI). Once in virtual console, issue command ```
unity
``` to restart your desktop, see if that gives any immediate help to your problem. Issuing that command should not close any of your opened documents/applications.

---

### Post by ibjsb4 on 2014-04-06
Wow, thats pretty buggy.

Has this been going on since you installed ubuntu?

Unity has a 2D mode in 12.04, have you tried it?

What kind of equipment you got (cpu, ram, video)?

See if this will give you any errors:

```
sudo apt-get -f install

```

---

### Post by monkeybrain20122 on 2014-04-06
Well boot problem has nothing to do with Unity. Unless I am missing something 1) happens before the login screen, unity is not even loaded at that point.

---

### Post by ibjsb4 on 2014-04-06
> **monkeybrain20122 said:**
> Well boot problem has nothing to do with Unity. Unless I am missing something 1) happens before the login screen, unity is not even loaded at that point.

And your suggestion would be?

---

### Post by DogMatix on 2014-04-06
> **monkeybrain20122 said:**
> Well boot problem has nothing to do with Unity. Unless I am missing something 1) happens before the login screen, unity is not even loaded at that point.

Depending what 'pink' screen we are viewing. If we are seeing a mouse pointer have we not progressed beyond GRUB and a DE is trying to load!

---

### Post by monkeybrain20122 on 2014-04-06
> **ibjsb4 said:**
> And your suggestion would be?

Check the hardware especially the hd, which I suspect may be dying.

---

### Post by ibjsb4 on 2014-04-06
> **monkeybrain20122 said:**
> Check the hardware especially the hd, which I suspect may be dying.

Yes, this is a possibility.

---

### Post by AbleTassie on 2014-04-07
> **kurja said:**
> Something's broken in your system if it's doing that.... When having one of these freeze-ups, are you able to open a virtual console by hitting ctrl+alt+F1? (ctrl+alt+F7 reverts to your GUI). Once in virtual console, issue command ```
unity
``` to restart your desktop, see if that gives any immediate help to your problem. Issuing that command should not close any of your opened documents/applications.

I'll try that (i.e., unity). I am presently responding using the Ubuntu 12.04 LTS live CD, rather than the HD loaded version. I could not get on the internet with the HD version.

R.

---

### Post by AbleTassie on 2014-04-07
> **monkeybrain20122 said:**
> Check the hardware especially the hd, which I suspect may be dying.

The HD is brand new, I got it a couple weeks ago. The disk utility says the HD is healthy, SMART status.

---

### Post by AbleTassie on 2014-04-07
> **ibjsb4 said:**
> Wow, thats pretty buggy.

Has this been going on since you installed ubuntu?

Unity has a 2D mode in 12.04, have you tried it?

What kind of equipment you got (cpu, ram, video)?

See if this will give you any errors:

```
sudo apt-get -f install

```

[LIST]
[*]TOSHIBA Satellite L25-S1216 Detailed Product Specification
[*]Processor and Chipset
[*]Intel® Celeron® M Processor 380  
[*]1.60GHz, 1MB L2, 400MHz FSB 
[*]ATI RADEON® XPRESS 200M Chipset 
[/LIST]


RAM upgraded to 1.1 GB

HD is upgraded to new 100 GB PATA Fujitsu MHV2100AT  ATA drive

Don't know anything about unity, but will try to learn.

Thanks,

R.

---

### Post by buzzingrobot on 2014-04-07
> **RMcGinnis said:**
> [FONT=sans-serif]
[SIZE=3]Don't know anything about unity, but will try to learn.
[/SIZE][/FONT]

Unity, 2D or 3D, is the default interface on Ubuntu 12.04.  It is what you should have been seeing all along. I.e, a top panel and a column of icons on the left screen edge.  

Generically speaking (meaning there's no way to know if it's related to your current problems) have you been installing updates regularly?

When you see the the pink screen with the mouse cursor, can you use Ctrl-Alt-F1 to open a full screen terminal window? You would see a black screen with a login prompt.  (Ctrl-Alt-F7 should get you back).

---

### Post by AbleTassie on 2014-04-07
> **buzzingrobot said:**
> Unity, 2D or 3D, is the default interface on Ubuntu 12.04.  It is what you should have been seeing all along. I.e, a top panel and a column of icons on the left screen edge.  

Generically speaking (meaning there's no way to know if it's related to your current problems) have you been installing updates regularly?

When you see the the pink screen with the mouse cursor, can you use Ctrl-Alt-F1 to open a full screen terminal window? You would see a black screen with a login prompt.  (Ctrl-Alt-F7 should get you back).

OK, I get Unity if I don't get the boot failure before Unity. On booting I get the typical pink screen with the mouse arrow in the middle of the screen. If boot is successful, the icons (in the Launcher etc) in Unity will suddenly appear. With boot failure, the icons and the Launcher, Unity just never appear, even if I keep the PC on for hours. 

I have been updating regularly. I will try some of the suggestions. Currently Ubuntu on the HD is working and I am using it now. But last night I used the live CD to respond to the posts in this thread. I think there is an update due now which I'll try to install.

Thanks,

R.

Edit: Computer is now up to date.

---

### Post by AbleTassie on 2014-04-07
> **ibjsb4 said:**
> 
See if this will give you any errors:

```
sudo apt-get -f install

```

I got the read out below:

sudo apt-get -f install
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-umefont libhttp-daemon-perl libfile-listing-perl libwww-robotrules-perl
  libnet-ssleay-perl liburi-perl gir1.2-ubuntuoneui-3.0 gir1.2-atspi-2.0
  libhttp-date-perl liblwp-mediatypes-perl libfont-afm-perl libmailtools-perl
  libsocket6-perl libhtml-parser-perl python-virtkey libcapi20-3
  guile-1.8-libs unixodbc gettext libubuntuoneui-3.0-1 python-speechd
  liblouis2 libpam-winbind liblwp-protocol-https-perl python-brlapi icoutils
  python-louis libio-socket-inet6-perl gnome-games-data
  gir1.2-gnomebluetooth-1.0 libtimedate-perl libhtml-form-perl
  libhttp-negotiate-perl libhtml-format-perl libencode-locale-perl
  python-pyatspi2 libhtml-tree-perl libio-socket-ssl-perl libwww-perl winbind
  fonts-droid libhttp-cookies-perl liblouis-data libhttp-message-perl
  gnome-exe-thumbnailer libhtml-tagset-perl libnet-http-perl ttf-droid
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by AbleTassie on 2014-04-07
Something else weird: Right now I can't access applications through the DASH. I can access home, files & folders, and video, but not applications. Maybe if I reboot that will help. 

I can switch back and forth between Unity and a black terminal screen by using ctrl+alt+f1 and ctrl+alt+f7.

Thanks,

R.

---

### Post by monkeybrain20122 on 2014-04-07
> **RMcGinnis said:**
> Something else weird: Right now I can't access applications through the DASH. I can access home, files & folders, and video, but not applications. Maybe if I reboot that will help. 
.

I don't know what causes this but others have reported the same.
[http://ubuntuforums.org/showthread.php?t=2215411](http://ubuntuforums.org/showthread.php?t=2215411)

If reboot doesn't fix it, open your home directory, press ctrl + h to show hidden files (or check 'show hidden files' in the file manager's menu)
then go to .local/share and delete the folder zeitgiest then reboot and applications should show.

---

### Post by AbleTassie on 2014-04-07
Hi Monkeybrain and others,

Presently Ubuntu on the HD is working; but for how long? After reboot I was able to access applications through the DASH. I was looking for the System Monitor, so I opened it and locked it to the Launcher. So I should be able to access it all the time now. I wanted to monitor my upload and download, because one of the bugs is that my internet connection just "goes out" for some reason. When this happens the system monitor Network History just "flat lines" at zero. 

The last time I was not able to boot into Unity, I hit ctrl+alt+F1 and then ctrl+alt+F7 and "Voila" the icons and the launcher appeared, BUT the icons in the launcher did not respond to a mouse click. I also noticed there was no black bar at the top with my username and the icons with dropdown menus. So I had to reboot again.

I was just doing something on the internet and everything was going fine, then bam, the mouse and screen just froze up requiring another reboot. This is getting annoying. It's as bad as Windows. And I really like Ubuntu, the people, etc. But not sure what to do. Looks like this post will go through at least.

Thanks,

R.

---

### Post by buzzingrobot on 2014-04-07
Did these problems exist before the new drive was installed? Or, was 12.04 installed on the new drive?

---

### Post by AbleTassie on 2014-04-07
> **buzzingrobot said:**
> Did these problems exist before the new drive was installed? Or, was 12.04 installed on the new drive?

It's a good question. I don't think they did exist with the old drive, at least not to this extent. The old drive is a 40GB drive that came new with the new PC. It has 25 bad sectors, that's the reason I replaced it. But it is still functional. The number of bad sectors (25) did not increase over a period of 3-4 weeks that I monitored the drive. I suppose I could put it back in and see if it has the same problems. It is not that hard to swap out the hard drives. And the data on the drives stays intact. In fact the old drive probably still has Ubuntu 12.04 LTS on it.

BTW, I had to reboot Ubuntu & the HD since my last post, because the PC froze again, even though the PC was not being used.

R.

Edit: If it is the HD, would there be a utility that would detect the HD abnormality? I bought the new HD with a 3 year warranty.

---

### Post by mörgæs on 2014-04-07
> **RMcGinnis said:**
> 
[LIST]
[*]TOSHIBA Satellite L25-S1216 Detailed Product Specification
[*]Processor and Chipset
[*]Intel® Celeron® M Processor 380
[*]1.60GHz, 1MB L2, 400MHz FSB
[*]ATI RADEON® XPRESS 200M Chipset
[/LIST]


RAM upgraded to 1.1 GB

HD is upgraded to new 100 GB PATA Fujitsu MHV2100AT  ATA drive


This is fairly weak (but still useable) hardware. I wouldn't recommend Ubuntu.
A fresh install of X/Lubuntu 13.10 or 14.04 is a better option, also if your Ubuntu were working flawlessly.

---

### Post by ibjsb4 on 2014-04-07
> **mörgæs said:**
> This is fairly weak (but still useable) hardware. I wouldn't recommend Ubuntu.
A fresh install of X/Lubuntu 13.10 or 14.04 is a better option, also if your Ubuntu were working flawlessly.

+1

---

### Post by AbleTassie on 2014-04-07
> **ibjsb4 said:**
> +1

Thank you Morgaes and ibjsb4. I actually tried Lubuntu a little bit. It is not as elaborate as Ubuntu, but is certainly useable. So I could definitely give it a try. 

QUESTIONS: Is it still possible to use the Ubuntu One cloud back-up service (I already set up) with Lubuntu?  (I know Ubunu One is being dscontinued in a few months.)

I am presently dual booting Windows XP and Ubuntu. Is a clean install of Lubuntu easy, will it leave my Windows XP installation intact? 

(I still need the Windows XP for a while longer, but I do not use it for the internet. I know it will not be supported after tomorrow). 

Is there any kind of Lubuntu manual? One thing I really like about Ubuntu is that "?" application that allows you to ask questions and learn to use Ubuntu. Is there anything I can use to replace this "?" app for Lubuntu?

Thanks again,

R.

---

### Post by ibjsb4 on 2014-04-07
Burn a Live DVD 0f 13.10 and install just like you did ubuntu.  Durning the install you will be given the option to overwrite the ubuntu install with lubuntu.  Which will give you a dual boot xp/lubuntu set up.


[http://lubuntu.net/](http://lubuntu.net/)


[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)


I do not use UbuntuOne, someone else will have to answer that.

---

### Post by mörgæs on 2014-04-08
Lubuntu fits to a CD.
From a live boot you can delete the old Ubuntu partitions. After that it all works automatically.

---

### Post by AbleTassie on 2014-04-08
OK, thanks to everybody. I downloaded Lubuntu 13.10 via torrent today, checked the MD5Sum and the SHA256 Sum, and installed it in place of Ubuntu 12.04LTS. If I stop having the bugs reported in the original post, I'll mark the thread as [SOLVED]. So far it looks pretty good. 
I've visited the Ubuntu One website and in Lubuntu I can download  individual files, but not folders. The individual file download  capability may be enough for me.

I will post the questions below about Lubuntu in a new post, but if somebody wants to answer them, please do.

QUESTIONS: I can't find Libre Office in the Lubuntu Software center. When I used Lubuntu a few weeks ago, Libre Office apps were available in the Lubuntu Software Center for download. I wonder what happened?  

I am presently downloading the latest version of Firefox 28 as a .tar.bz2 file. The latest Firefox available on the Download center is 24. I guess I have to manually install Firefox 28 using Terminal. Any tips on how to do it?

Thanks again,

R.

---

### Post by ibjsb4 on 2014-04-08
> QUESTIONS: I can't find Libre Office in the Lubuntu Software center. When I used Lubuntu a few weeks ago, Libre Office apps were available in the Lubuntu Software Center for download. I wonder what happened?

Have you updated since you installed?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by monkeybrain20122 on 2014-04-08
Actually I don't even find the lubuntu software centre works. When searched for packages available it only showed installed packages.  Maybe I am missing something but I would just use synaptic.

Edited: Read somewhere that lsc would work properly if run an upgrade after installation of lubuntu, and then reinstall lsc. But never tried it.

---

### Post by mörgæs on 2014-04-09
In addition to the commands above I recommend ```
sudo apt-get dist-upgrade
``` and ```
sudo apt-get autoremove
```. 

Only download stuff as a very last resort. Firefox is updated automatically, and Libreoffice comes with the command ```
sudo apt-get install libreoffice
```

---

### Post by AbleTassie on 2014-04-09
> **mörgæs said:**
> In addition to the commands above I recommend ```
sudo apt-get dist-upgrade
``` and ```
sudo apt-get autoremove
```. 

Only download stuff as a very last resort. Firefox is updated automatically, and Libreoffice comes with the command ```
sudo apt-get install libreoffice
```

Thank you so much. I have executed the commands given by ibjsb4 last night (sudo apt-get update && sudo apt-get upgrade), that released a flood of activity. I went to the Lubuntu Software Center today and Libre Office Apps were now present for download. I started to download Libre Office Writer and Impress, then I looked at this thread with Morgaes caution about not donwloading. So I tried to cancel the Office & Writer Download by clicking the cancel button several times. But it would not stop downloading. So I disconnected the ethernet cable and rebooted. [B]I hope I did not cause problems by doing this. Did I?
[/B]
And I'd like to install Libre Office Writer and Impress using the Terminal as Morgaes suggests. But I really don't want everything in Libre Office, just Writer and Impress for now. 

**QUESTION(S):** The COMMAND "sudo apt-get install libreoffice" will install everything in Libre Office, won't it? I think there is even a Libre Office CAD/CAM program. Is there a way to just install the select Office components (Writer & Impress) using Terminal?

Where do you guys get these Terminal commands from?

Running "sudo apt-get dist-upgrade" (as suggesed by Morgaes) released a flurry of activity. But "sudo apt-get autoremove" came back with just:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks to everybody for their comments and help. I think the install of Lubuntu did the trick. It seems to be faster than Ubuntu 12.04 LTS and does not suffer from the bugs in Ubuntu 12.04 LTS. I am enthusiastic and will continue to be a missionary for Ubuntu/Lubuntu and the support given by all of you and tell others here (where I live in the US) about it.

R. :P

---

### Post by ibjsb4 on 2014-04-09
> And I'd like to install Libre Office Writer and Impress using the Terminal


```
sudo apt-get install libreoffice-writer
```

I'm not familiar with the Impress package

> Where do you guys get these Terminal commands from?


Maintenance commands :)

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by mörgæs on 2014-04-09
Update and dist-upgrade should be run as the first step after install. After that you can add more packages.

If you have a 100 GB harddisk why do you want to install only part of Libreoffice?

If you begin spreading the word (and please do) it might help you to read the link in my signature first.

---

### Post by AbleTassie on 2014-04-09
> **ibjsb4 said:**
> ```
sudo apt-get install libreoffice-writer
```

I'm not familiar with the Impress package

Maintenance commands :)

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Thanks ibjsb4. I also found the links below which describe full and selective Libre Office installations using Terminal commands:

[https://wiki.ubuntu.com/LibreOffice](https://wiki.ubuntu.com/LibreOffice)

[https://wiki.ubuntu.com/LibreOffice#Selective_installation](https://wiki.ubuntu.com/LibreOffice#Selective_installation)

[https://wiki.ubuntu.com/LibreOffice#Full_installation](https://wiki.ubuntu.com/LibreOffice#Full_installation)

Thanks,

R.

---

### Post by AbleTassie on 2014-04-09
> **mörgæs said:**
> Update and dist-upgrade should be run as the first step after install. After that you can add more packages.

If you have a 100 GB harddisk why do you want to install only part of Libreoffice?

If you begin spreading the word (and please do) it might help you to read the link in my signature first.

Thank you Morgaes (sorry no umlaut on my keyboard). Regarding not wanting to install the entire Libre Office, I guess I'd say that I had problems with Ubuntu 12.04 LTS because it is "too heavy" for my PC so I am trying to be frugal and only install what I need. Maybe, however, Ubuntu 12.04 LTS's "heaviness" comes from too many apps running at once, rather than apps being stored on the HD. My HD is 100 GB, about 50 GB alotted to Lubuntu, 50 GB alotted to WIndows XP. I will probably shrink down the Windows XP part, when I figure out how to do it, as I don't use Windows XP much. But in any case only about 50GB is available to Lubuntu right now.

I did start to read the links in your signature tonight. In fact I started reading them before tonight, because they were in your signature and seemed relevant. So I have learned that a person needs to be aware that older hardware may not really support the latest, fanciest version of Ubuntu like Ubuntu 12.04 LTS with Unity. But Lubuntu (and others like Bohdi Linux) may be an option. Lubuntu seems to be working well for me right now.

Thank you again, ;)

R.

---

### Post by mörgæs on 2014-04-10
The size of a package (or a collection of packages) does not indicate if it's heavy or not to run. Ubuntu is heavy because of the eye candy in Unity, the desktop environment. 

Sounds like you are on the right track. I suggest you begin experimenting with various setups and watch the performance. Worst case scenario is that you will have to waste half an hour doing a reinstall.

---

### Post by AbleTassie on 2014-04-10
> **mörgæs said:**
> The size of a package (or a collection of packages) does not indicate if it's heavy or not to run. Ubuntu is heavy because of the eye candy in Unity, the desktop environment. 

Sounds like you are on the right track. I suggest you begin experimenting with various setups and watch the performance. Worst case scenario is that you will have to waste half an hour doing a reinstall.

   Mörgaes,

Thanks to you (see umlaut above) and to everybody else including ibjsb4 and others, 

I have installed the full Libre Office and Lubuntu seems to be working well for me and is fast. I will mark this thread as SOLVED. 

A curiosity I noticed today: my Lubuntu calendar was off by a day and I could not change it. And the calendar in Windows XP was also off by a day in the same way. I was able to change the calendar in Windows XP to the correct day. And the calendar in Lubuntu was then correct after I changed the calendar in Windows XP.

Thanks again,

R.

---


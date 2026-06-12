---
title: "help in selecting ubuntu"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by zeshan2 on 2013-08-10
so before starting off let me tell you my intro.
I have been using Windows from my childhood days and I'm completely new to Linux ubuntu.
last month I took my first Dell laptop which came preinstalled with ubuntu 11.10 .
realising that I'm completely new to ubuntu,I asked the shop owner to install Windows and then would I prefer buying the laptop. he installed Windows 7 ultimate 64 bit and I bought the laptop. 
from the past 1 month I have tried Windows 8 pro and other versions of Windows 7. 

So on a personal front I have decided to stop using Windows and switch to Linux. I need your sincere suggestions -
my laptop configuration : core i3 . maximum speed 2.20 ghz, 4 gb ddr3 ram  , Intel 3000 integrated graphics.
as I said im a student I use my laptop for playing a few games,using cad (computer aided engineering drawing) softwares ,videos,music and internet and ms office.
so I want to suggest which version os ubuntu or linux mint will be good for my laptop configuration and my needs (please remember I have zero background of linux).
please also mention whether 32 or 64 bit version will be useful.. 
I have heard of wine.please give me a insight on the same.
thanks in advance

---

### Post by The Cog on 2013-08-10
You will probably get lots of people advocating different versions of Ubuntu. I think your hardware is probably able to support any of the versions. I would suggest going for a 64-bit version of whatever you choose, they feel slightly faster to me.
The different versions all have a very different look and feel, although the underlying operating system is the same. Rather the same way that XP, Vista and W8 look different but much the same underneath, except the visual differences are more extreme. All I can suggest is that you make live CD or memory stick of each version and try for a few hours. The versions you might try are Ubuntu, Xubuntu, Lubuntu, Kubuntu, Mint. 

Wine is a compatibility layer that allows you to run some (not all) windows programs under Linux. I think I've read that MS office runs in wine, but if not LibreOffice (a native linux app) has pretty good compatibility. I have no idea about your CAD software though. perhaps check with [http://www.winehq.org/](http://www.winehq.org/) .

---

### Post by zeshan2 on 2013-08-10
okay first let me tell me about the bit version.
I have used Windows 8 pro 64 bit and Windows 7 ultimate 32 bit in the past 10 days.. 
the difference I find is 32 bit version works faster in loading files and 64 bit takes a while ( I get annoyed by it) .
ok so I installed ubuntu 13.04 64 bit and during installation I selected remove Windows and install ubuntu.. ubuntu 13.04 64 bit also takes a short time before opening my files..

I don't know why ubuntu has formatted all my hard disks and installed itself.
I have lost everything which I had on my laptop :'( .
ubuntu website didn't notify me about this.
never in Windows have my files on other disk formatted.
I didn't want to multi boot because I had called Dell technical support a few days back and he told me not multi boot ubuntu and Windows on my laptop.
now what should I do

---

### Post by grahammechanical on 2013-08-10
> I don't know why ubuntu has formatted all my hard disks and installed itself.

Yes, you do. By your own admission you told the installer of Ubuntu to do this

> during installation I selected remove Windows and install ubuntu

How many hard disks are there in your laptop? Perhaps you mean partitions. Did you not see this on the web site?

[http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)

Note image number 4 under installation type. Note the option number 2 Replace Windows 7 with Ubuntu. It also says [COLOR=#ff0000]Warning:[/COLOR] This will delete all your Windows 7 programs, documents, photos, music, and any other files.

And it did.

---

### Post by ant2 on 2013-08-10
I'd go for an Ubuntu install, over windows OS any day. Your basic software requirements for software can easily be supplied in linux, videos = VLC, music = Rhythmbox, Banshee and a plethora of other options, internet = Firefox, Opera, etc. MS office = Libre Office. Your CAD requirements may be a little harder although there are cross platform options. Are you tied to a specific CAD program for educational/professional reasons? I have this issue with Adobes Creative Software, although I'm kicking and screaming all the way trying to change this.

---

### Post by zeshan2 on 2013-08-11
okay so I didn't read what was written below 'install ubuntu over Windows' and just went through. pathetic!!!! I had 3 partitions totalling 465 gb and ubuntu has converted all these partitions into a single partition. and that partition is also not viewable in the dash!! 

secondly I need autocad for my engineering drawings.. though I'm not using it currently. but in a few days I would be starting work on it. thats the only reason I'm sticking to Windows,though I hate Windows.. Windows crashes a lot in my friend's laptop and takes too much time to boot up..


next thing is about ubuntu drivers. I read ubuntu needs no drivers to be installed as it does come preinstalled drivers.
I'm not able to scroll down through my touchpad. everytime I need to pull the bar on the right side.
Bluetooth provides basic functionality whereas in Windows it used to give additional functionality like playing my phone's music,controlling my phone,etc 
and what about the bit version?? 64 bit ubuntu 13.04 is taking a while opening my files

---

### Post by mastablasta on 2013-08-11
> **zeshan2 said:**
> okay so I didn't read what was written below 'install ubuntu over Windows' and just went through. pathetic!!!! I had 3 partitions totalling 465 gb and ubuntu has converted all these partitions into a single partition. and that partition is also not viewable in the dash!! 

perhaps before diving into a completely different operating system you never used before you should read some documentation. there is a very good community made manual for ubuntu (see my signature). it will explain to you a few basics about the OS.

> 
secondly I need autocad for my engineering drawings.. though I'm not using it currently. but in a few days I would be starting work on it. thats the only reason I'm sticking to Windows,though I hate Windows.. Windows crashes a lot in my friend's laptop and takes too much time to boot up..

not usign CAD, but i do know there are some programes out there in linux. not sure if they would satisfy you. they mightnot be as good as some proprietary ones. i really dont' know.
> 
next thing is about ubuntu drivers. I read ubuntu needs no drivers to be installed as it does come preinstalled drivers.
I'm not able to scroll down through my touchpad. everytime I need to pull the bar on the right side.
Bluetooth provides basic functionality whereas in Windows it used to give additional functionality like playing my phone's music,controlling my phone,etc 
and what about the bit version?? 64 bit ubuntu 13.04 is taking a while opening my files
[/QUOTE]
again you didn't read it all. in linux drivers are often incorporated into kernel. however drivers that are locked by manufacturer -proprietary drivers (e.g GPU drivers form AMD and nvdidia, various wifi chip drivers etc.) are not included and need to be installed and tweaked separatelly. they can't be included due to legal issues. what is in kernel is usually only opensource.

these additional drivers can be installed via additional drivers application. but you might need to enable a few other repositories. it could also be that you only need to install drivers frm software repository or similar.

to give you better help on your issues i suggets opening separate threads in their respective subforums and to give as much detail as ppossible on the model of touchpad and the Bluetooth chip.if Ubuntu was on your maschine before then i am sure these should work proppely.

---

### Post by 3rdalbum on 2013-08-11
> **zeshan2 said:**
> okay so I didn't read what was written below 'install ubuntu over Windows' and just went through. pathetic!!!! I had 3 partitions totalling 465 gb and ubuntu has converted all these partitions into a single partition. and that partition is also not viewable in the dash!!

The partition that Ubuntu is installed to, will not show in the sidebar. If you open your home folder and click "File System" on the left side of the window, you'll be able to see it - but of course it won't contain any of the files that it contained when you were using Windows. Those were erased when Windows was erased.

> next thing is about ubuntu drivers. I read ubuntu needs no drivers to be installed as it does come preinstalled drivers.
I'm not able to scroll down through my touchpad. everytime I need to pull the bar on the right side.
Bluetooth provides basic functionality whereas in Windows it used to give additional functionality like playing my phone's music,controlling my phone,etc 
and what about the bit version?? 64 bit ubuntu 13.04 is taking a while opening my files

Easiest question first: 64-bit is no different to 32-bit. It just allows the computer to use bigger numbers.

The drivers in Ubuntu are different to the drivers in Windows. Some will work much the same as the Windows ones. Some will have fewer features, some will have more features. If your hardware works, you've got the correct driver.

---

### Post by ibjsb4 on 2013-08-11
@zeshan2

You can try all the flavors at once if you so desire :)

Go ahead and install ubuntu and then [in terminal:]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")

```
sudo apt-get install lxde xfce4 xfce4-goodies gnome-session-fallback
```

And you now have Lubuntu/Xubuntu/GnomeClassic/Unity desktops installed on your computer.  You can choose at boot (login) which one you want to run by clicking on the icon.

---


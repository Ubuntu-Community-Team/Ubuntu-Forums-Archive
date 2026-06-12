---
title: "Too much junk, please help 'pimp' my Ubuntu!"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by robot952 on 2014-04-18
Hey fellow nerds, can you help me organize/customize my desktop?.  I'm running Ubuntu 12.04 and have a bunch of useful 'quicklaunch' icons (I don't know what they are formally called) on the left side of the screen.  They are great & easy to use, but it has gotten very crowded.  Any suggestions on how best to organize my desktop? (Perhaps creating folders like 'games', 'browsers' etc for each sub group of icons?).

I have tried moving the icons from the left side of my screen, but the problem is after I right click and choose 'undock from launcher', the icon disapears and I can't find it or the program again!

Thx!

---

### Post by sudodus on 2014-04-18
Welcome to the Ubuntu Forums :-)

Please be aware of the community flavours of Ubuntu, with the same engine under the hood:

Kubuntu - fancy and easy to tweak or pimp
Lubuntu - ultra light-weight
Xubuntu - medium light weight

I suggest that you try these flavours live (without installing) to find out what will be best for you. Maybe you will stay with standard Ubuntu, maybe not.

---

### Post by robot952 on 2014-04-18
thanks, but the idea of uninstalling and reinstalling Linux does not sound like fun! Is there a way to 'upgrade' or modify from 12.04 to Lubuntu without losing everything (files programs etc) and starting over? 

thx

---

### Post by robot952 on 2014-04-18
By the way, I am also unable to download easily with using the Ubuntu Software Center.  I Can not find gdebi-gtk. I was trying to download Wine, using Ubuntu Software center to download won't do the trick, but I heard gdebi-gtk...

---

### Post by robot952 on 2014-04-18
is a better way to do it.  Is it missing from the distro I got? is there a way to simply download and insert it in? thx!

---

### Post by sudodus on 2014-04-18
It is possible, but not easy, if you want to purge the system from doublets (application programs that do the same thing). But if you accept these doublets in menus etc, and the space they occupy on the disk, it is OK to use these commands:

```
sudo apt-get install kubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop

```
You can prefer to only install the desktop environment, not the fully tweaked flavour of Ubuntu

```
sudo apt-get install kde-full
sudo apt-get install lxde
sudo apt-get install xfce4

```
See for example

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

But you can also start the ***Ubuntu mini.iso*** and build your own installation adding only the packages that you want. And you can have one production system (you current installed Ubuntu system) and an experiemental one. Make a dual boot or mult-boot system! This way you will not interfere with your production system while you are testing various configurations.

---

### Post by 3rdalbum on 2014-04-18
> **robot952 said:**
> Hey fellow nerds, can you help me organize/customize my desktop?.  I'm running Ubuntu 12.04 and have a bunch of useful 'quicklaunch' icons (I don't know what they are formally called) on the left side of the screen.  They are great & easy to use, but it has gotten very crowded.  Any suggestions on how best to organize my desktop? (Perhaps creating folders like 'games', 'browsers' etc for each sub group of icons?).

I have tried moving the icons from the left side of my screen, but the problem is after I right click and choose 'undock from launcher', the icon disapears and I can't find it or the program again!

Thx!

If you click the big Ubuntu button at the top of the screen, you can type what you want to search for. You can also right-click it and choose Applications, and then click "Show all installed" or click "Filter Results" and choose some categories to view. The programs are already in the categories. You do not need to keep every program on the "quicklaunch" (which is actually called the Launcher).

Unlocking an icon from the Launcher does not remove the program, it just removes it from the Launcher. You can still get to them from the Applications thing I mentioned above.

Your Ubuntu Software Center not working should be the highest priority for you. It's probably very easy to fix, but you should post a thread about it and get that sorted out. You can't do anything if your package manager isn't working.

---

### Post by sudodus on 2014-04-18
> **robot952 said:**
> By the way, I am also unable to download easily with using the Ubuntu Software Center.  I Can not find gdebi-gtk. I was trying to download Wine, using Ubuntu Software center to download won't do the trick, but I heard gdebi-gtk is a better way to do it.  Is it missing from the distro I got? is there a way to simply download and insert it in? thx!

If you have problems with the Software Center, install and try ***Synaptic*** or use terminal window commands (command line interface, CLI)

```
sudo apt-get install synaptic
```

```
sudo apt-get install wine
```

---

### Post by sudodus on 2014-04-18
In Synaptic, you may want to select the pull down menu

Settings -- Repositories

and make more Repositories available to get access to more program packages.

---

### Post by robot952 on 2014-04-18
I think it's already set. Can you show an example (for instance downloading Wine) of how exactly one uses Synaptic? (you know left click this, rijht click that etc)

Thx

---

### Post by sudodus on 2014-04-18
> **robot952 said:**
> I think it's already set. Can you show an example (for instance downloading Wine) of how exactly one uses Synaptic? (you know left click this, rijht click that etc)

Thx

See these links

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html](http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html)

and you can find more browsing the internet for ***synaptic tutorial***

---

### Post by robot952 on 2014-04-18
Maybe a youtube video?

---

### Post by robot952 on 2014-04-18
Maybe I screwed up SPM, I am going to try and reinstall from the software center and see if it helps

---

### Post by robot952 on 2014-04-18
It worked! :) Reinstalled synaptic and it is working properly. Now let's see if I can get this wine thang...

thx Sudodos

---

### Post by Mark Phelps on 2014-04-18
Before you get too excited about Wine, I should tell you that it's not a Windows subsitute; instead, it only runs some Windows apps, and even then, in many cases, not very well.

If you are interested in specific apps or games, then you need to visit the Wine website and check on the compatibility ratings of the apps or games you want to use:  [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Anything not found, or rated lower than Gold, is going to be too short of functionality to be useful on a daily basis.

---

### Post by sudodus on 2014-04-18
> **robot952 said:**
> It worked! :) Reinstalled synaptic and it is working properly. Now let's see if I can get this wine thang...

thx Sudodos

Congratulations :KS

Good luck developing your system(s) :-)

---

### Post by robot952 on 2014-04-18
Wow, I was hoping it would have functionality more like Windows XP or older :(  Anyhow, Thx for all your help!

I used the terminal. I typed:
sudo apt-get update
then
sudo apt-get install wine
 So it installed, but when I go to dash home, and rt click applications I see only 'winetricks' not 'wine'. Any idea why that is?

---

### Post by robot952 on 2014-04-18
Is there any other 'Virtual' Windows Xp type programs out there that will run in Ubuntu?

---

### Post by sudodus on 2014-04-18
> **robot952 said:**
> Wow, I was hoping it would have functionality more like Windows XP or older :(  Anyhow, Thx for all your help!

I used the terminal. I typed:
sudo apt-get update
then
sudo apt-get install wine
 So it installed, but when I go to dash home, and rt click applications I see only 'winetricks' not 'wine'. Any idea why that is?

You should be able to run a windows program, for example a self installing file, like this (from a terminal window)

```
wine self-installer.exe
```

---

### Post by sudodus on 2014-04-18
> **robot952 said:**
> Is there any other 'Virtual' Windows Xp type programs out there that will run in Ubuntu?

If you have enough horsepower and memory, say at least a 2 GHz core2duo and 2 GB RAM (better with 4 GB RAM), you can run Windows in a virtual machine for example ***VirtualBox***. This gives you a 'full' Windows experience (but slower due to virtualization). If you have Windows XP, and don't want it infected after end of life, do not connect it to the internet.

---

### Post by robot952 on 2014-04-18
Thx again! I may give it a shot and see if my PC can handle the memory demands...

---

### Post by Mark Phelps on 2014-04-18
> Wow, I was hoping it would have functionality more like Windows XP or older 

If you're talking about Wine -- don't feel bad, that's a very common  misunderstanding.  Folks think Wine is a Windows Emulator, but instead, it's a "hack" in which some Windows libraries (known as DLLs) that make Windows system calls are replaced by DLLs that make Linux system calls.  To the degree that a Windows app or game relies on those libraries, it will tend to work well.  But in recent years, MS has swiched over to using other Middleware instead of those libraries, leaving Wine in the situation where the newer the Windows app or game, the less likely it will work.

A good place to start to understand how Linux is different from Windows is the linked material: [http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by robot952 on 2014-04-18
Anyone know where to find complex configurations in ubuntu 12.04? The guy I saw had it in his launcher, but mine isn't there and I need it. BTW, how DO you get stuff placed on the launcher?

---

### Post by Navneet_Kumar on 2014-04-18
Yes upgrading or a fresh installation of 14.04 would be a good substitute....otherwise use bleachbit or ubuntu tweak tool for the above described issues..........:D

---


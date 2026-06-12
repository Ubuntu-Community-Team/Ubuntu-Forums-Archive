---
title: "HOWTO: wine + uTorrent with native Tray icon"
date: 2006-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Kimm on 2006-11-07
[CENTER]This HOWTO will describe how to install uTorrent on your Linux desktop using **wine** and how to get a more suitable tray icon using **alltray**[/CENTER]

First of all we need to add a new repo (for dapper, but works in edgy):

> 
sudo gedit /etc/apt/sources.list


Add this to the end, save and quit:

> 
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french


Now to install wine and alltray:

> 
sudo apt-get update
sudo apt-get install alltray wine


Now, download and "install" uTorrent 1.6 (or any other (standalone) version):

> 
mkdir .utorrent
cd .utorrent
wget [http://download.utorrent.com/1.6/utorrent.exe](http://download.utorrent.com/1.6/utorrent.exe) **(<-- executable**
wget [http://img400.imageshack.us/img400/5093/utorrenteh8.png](http://img400.imageshack.us/img400/5093/utorrenteh8.png) **(<-- icon)**


now, we will create a menu entry for uTorrent:

> 
sudo gedit /usr/share/applications/utorrent.desktop


You should now have an empty file, copy & paste this (and replace the highlighted areas):

> 
[Desktop Entry]
Type=Application
Version=1.0
Encoding=UTF-8
Name=uTorrent
GenericName=BitTorrent Client
Icon=/home/**<username>**/.utorrent/utorrenteh8.png
Exec=alltray --icon /home/**<username>**/.utorrent/utorrenteh8.png wine /home/**<username>**/.utorrent/utorrent.exe
Path=
Terminal=false
MimeType=
Categories=GNOME;Application;Network;


Save the file and close gedit.
To refresh gnome-panel type: killall gnome-panel

uTorrent Should now be found in the Network menu.

Snapshot:
[img]http://img523.imageshack.us/img523/1644/screenshot5tr1.png[/img]

Edit:
Remember to disable to original tray icon in preferences.

**SHARE uTORRENT SETTINGS WITH WINDOWS (Courtesy of guguma)**

I am using winXP and Ubuntu together. And I really like utorrent. I also do switch between two OS's regularly. So I needed to find a way to resume my torrents in both OS's. I finally acknowledged it. And I am writing this tutorial to the forum because Windoze related issues are not that mentioned in the ubuntu forums. I hope it will help.

First of all:

1. I did this with Ubuntu Feisty 7.04. i386 build and Windows XP pro 32-bit.

2. I used utorrent 1.7.2.

3. I like explaining things in detail in order to avoid future misunderstandings. And I will not only explain how but why I am doing things to. So be patient.

**FIRST STEP [Installing uTorrent on XP]**

1. Download utorrent 1.7.2 from

[http://download.utorrent.com/1.7.2/utorrent.exe](http://download.utorrent.com/1.7.2/utorrent.exe)

2. Execute utorrent.exe and when it prompts you to install it say NO. (If you say yes it will create some shortcuts and registry items which we do not like)

3. Place the executable to a folder of your choice say

D:\Standalones\utorrent\

4. Run utorrent once, and then exit.

5. The folder utorrent will be created at C:\Documents and

Settings\<USERNAME>\Application Data\

6. Copy the contents of this folder in the same place you placed
utorrent.exe (this will somehow change how utorrent behaves. Now it will be more standalone and will not create folders and items in distant places but write anything on the folder where the executable is contained)

7. Create another folder in the folder of the executable called 'torrents'. (We will choose the option to store torrents here this is essential for continuity because when we run utorrent from Linux we will make it look into this folder too, otherwise it will store torrents in Application Data)

8. Run utorrent again. And assign the folder locations for downloaded and finished torrents(choose a win drive because we want both XP and Linux to write the downloads and XP cannot write to the LInux Partitions).

In Options->Preferences->Downloads. And also
go to Options->Preferences->Other and choose your torrent storeage folder as the one we created at step 7.

9. Windows part is finished.

**SECOND STEP [Installing and Configuring WINE]**

Wine is a windows application layer for Linux systems. It runs windows programs.

1. Get the latest WINE. Open up the terminal and type this to add the repository's key to your system's list of trusted APT keys

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```

Then add the reposiotry by typing:

```

sudo wget http://wine.budgetdedicated.com/apt/....d/feisty.list -O
/etc/apt/sources.list.d/winehq.list

```

Then update the package database

```

sudo apt-get update

```

And install wine

```

sudo apt-get install wine

```

2. Configuring Wine

Now this is very important. Your drive where utorrent.exe is in and where your download locations are in must be recognized by Wine.
Wine uses symbolic links to assign drive letters. Wine also has a terrible habit of assigning your cdrom devices from D: to where they stop. If you have 2 cdrom devices d: and f: wil be taken. And Z: will be the root filesystem of your linux. So we will not mess with cdrom drive letters and Z:.

First let us make Wine recognize your homefolder. This is important because it can cause crashes in wine.

```

sudo ln -s /home/<USERNAME>/ ~/.wine/dosdevices/h:

```

This will make your home folder H: in Wine. Now we need to make Wine know of your other drive related with utorrent. Let
us call it T:.

```

sudo ln -s /<Where yout torrent related drive is mounted in Linux> ~/.wine/dosdevices/T:

```

Before going to the last part. Let us make sure Wine runs with XP layer. It defaults to Win2000 layer and it causes black backgrounds in utorrent.

```

sudo wine winecfg

```

This will run the configuration window. If you do not sudo it it will not
save the configuration. Change Windows2000 to XP from there then click apply then OK.

3. Wine configuration is finished

**THIRD STEP (Executing utorrent in Linux and configuring it AKA The End)**

Now type:

```

wine /<Complete path of utorrent.exe>

```

Again you will probably see the install prompt. Choose No. If you do not see the utorrent window. Look at your tray icons and rightclick on it. Then choose hide/show utorrent. (By the way we will minimize and maximize utorrent like this, otherwise it will cause problems minimizing or maximizing)When utorrent executes. Make your port configurations and so, also choose your unfinished, finished download locations and torrent storage folder. These will the same as the ones you chose in XP with the difference of T: replaced by <Your Drive Letter>:.

ADDENDUM (Writing on ntfs partitions)

If the finished and unfinished download folders are on NTFS partitions you will have to make them writeable. Here is how:

Go to Synaptic Package Manager and search for ntfs-3g. Install it. (This lets you write on NTFS partitions).

Then

```

sudo gedit /etc/fstab

```

On the configuration file replace ''ntfs'' with ''ntfs-3g'' and save the file.

And if everything works perfect. You have achieved your solution.


If you come across any problems post it here. I am still a newbie and I may not be able to assist you with complicated problems. But can lead you to an expert. The only dangerous thing to do on this post is writing on the /etc/fstab. If you are not sure what to do. Ask before applying.


Thanks and good days to all.

---

### Post by NESFreak on 2006-11-09
in what repro does alltray live?

---

### Post by Kimm on 2006-11-09
> **NESFreak said:**
> in what repro does alltray live?

Oh damn, I thought it was in the standard Ubuntu repo...

Fixed!

---

### Post by chanders on 2006-11-09
Thank you. Great work ;-)  We should get some more nice tut's like this and stand alone apps for Windoze Xpee..

---

### Post by ba5e on 2006-11-09
I find that Utorrent works fine without alltray.....just configure it in winecfg to be an XP program instead of 2K :)

I even get it to run on startup: 
wine /home/username/utorrent.exe

Easy!!! and the default, nicer utorrent icon in the icon area.

---

### Post by Migalicious on 2006-11-23
How do I set uTorrent to be the default for torrent files?

---

### Post by ba5e on 2006-11-26
All I did was right click on a already dloaded .torrent file, go to properties and open with, then add and finally 'use a custome command':

wine /path_to_utorrent/utorrent.exe

when Firefox asks me what to do with the torrent, I say dload to desktop, then because I use download statusbar addon, I just double click to open the dloaded file in Firefox, and utorrent pops up :)

---

### Post by Sammi on 2006-12-02
Not to be rude, but in my opinion this is a far better utorrent icon than the one you use in your guide: 
[IMG]http://mindloop.ru/tmp/utorrent.png[/IMG]
[http://mindloop.ru/tmp/utorrent.png](http://mindloop.ru/tmp/utorrent.png)

commands to get and install:
```
cd ~/.utorrent
wget [http://mindloop.ru/tmp/utorrent.png](http://mindloop.ru/tmp/utorrent.png)
sudo gedit /usr/share/applications/utorrent.desktop
```Now change this line:
Icon=/home/**<username>**/.utorrent/utorrenteh8.png
to
Icon=/home/**<username>**/.utorrent/utorren.png

and remember to change <username> to your real computer login username.


People are, as always, free to do as they like :-D

---

### Post by Ekstreme on 2006-12-14
I have this working... Kinda. I get a tray icon, all looks nice, but it will only show utorrent. If I try to hide it via the icon menu, nothing happens. Same if I select exit, except the alltray app seems to close. Any idea?

---

### Post by raul_ on 2007-01-07
> **ba5e said:**
> I find that Utorrent works fine without alltray.....just configure it in winecfg to be an XP program instead of 2K :)

I even get it to run on startup: 
wine /home/username/utorrent.exe

Easy!!! and the default, nicer utorrent icon in the icon area.

How do you change the default tray icon so you don't get that ugly white background?

I also can't open .torrent files directly with uTorrent. It says "failed to open /home/raul: access denied!"

any ideas?

---

### Post by CAN-CAN on 2007-01-13
I did everything right like the how-to says and I get this error:

[SIZE="5"]**Could not launch menu item**[/SIZE]
Failed to execute child process "alltray" (No such file or directory)


What's wrong?

---

### Post by Sammi on 2007-01-13
> How do you change the default tray icon so you don't get that ugly white background?

I also can't open .torrent files directly with uTorrent. It says "failed to open /home/raul: access denied!"

any ideas?
Alltray is supposed to do that. Are you sure you installed it like the howto explains?

> I did everything right like the how-to says and I get this error:

[SIZE=5]**Could not launch menu item**[/SIZE]
Failed to execute child process "alltray" (No such file or directory)


What's wrong?

Alltray isn't installed on your computer. Try to install it again:
```
sudo apt-get install alltray
```If it doesn't work, tehn I want to know if you added the repositories like it's described in the howto? This page explains how to add Edgy or Breezy repositories if you're not using dapper: [http://asher256-repository.tuxfamily.org/index.php?page=faq&#9001;=en]("http://asher256-repository.tuxfamily.org/index.php?page=faq&lang=en")

---

### Post by oveh on 2007-01-24
Thank you for the howto!

Works almost perfect here, the only problem is that utorrent is constantly flimmering. Any solution to this? something with the wine config?

```

ove@wolverine:~$ uname -a
Linux wolverine 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
ove@wolverine:~$ wine --version
wine-0.9.29
```

---

### Post by Ekstreme on 2007-01-25
I've tried this through and through. It works, loads up OK, I get a nice little utorrent icon. But that's it. When I click hide\show utorrent comes up. Click it again and nothing happens. Click Exit nothing happens except alltray dies.

Is this what others are getting?

---

### Post by YokoZar on 2007-01-25
Why are you using your repository instead of the WineHQ one?

[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by Nik_Doof on 2007-01-25
One of the main benefit of having uTorrent in the tray is being able to adjust the speed from the right click drop menu. Does alltray support the app's own menu? or does it show its own?

---

### Post by oveh on 2007-01-25
It's own. So you can't adjust the speed ...

---

### Post by aFan on 2007-02-02
When I found this post when I allready installed uTorrent client, I was actually looking for a nice icon. Thus TNX to the folks posting a viriaty of them!

However, when I installed uTorrent I did it a little diferently & I'll describe it here.

I used the insaller found on [_uTorrent site_]("http://http://www.utorrent.com/download.php")... & installed with Wine.

```
wine ~/uTorrent-1.6-install.exe
```

If you decide to do it this way, it's imporants to _uncheck_  the launch option before finishing the installation. uTorrent will install in > ~/.wine/drive_c/Program Files/uTorrent.

Than configure wine to launch the application

```
winecfg
```

Add application, than from the dropdown menu select Windows98 (works better for me) & Apply.

Now create a launcher, as decibed in the original tutorial! Below is my utorrent.desktop file, it's even shorter than the original.

> [Desktop Entry]
Version=1.6
Encoding=UTF-8
Name=uTorrent
Exec=wine .wine/drive_c/Program\ Files/uTorrent/utorrent.exe
Type=Application
Icon=/home/aFan/.wine/drive_c/Program Files/uTorrent/utorrent2.png
Categories=Application;Network;FileTransfer;P2P

Have fun!

---

### Post by Sammi on 2007-02-04
This post explains how you launch torrents in uTorrent directly from Firefox: [http://www.ubuntuforums.org/showthread.php?p=1421017](http://www.ubuntuforums.org/showthread.php?p=1421017)

---

### Post by voxel on 2007-02-10
Nice tutorial :)
uTorrent looks really slick with that tray icon.. Nice and responsive, and it can actually minimize to the tray now..

However, the menus are all coming up from under the ubuntu Applications menu instead of under where I am clicking in utorrent?

---

### Post by bocmaxima on 2007-02-17
Ok, i am having just a small problem. When I start up uTorrent I get two icons, the nice one, and the standard windows one. Either one is fine by me, so can you tell me how to get rid of either one?

Theres also the problem of torrent files not associating and opening uTorrent

---

### Post by wajking on 2007-02-24
Someone who has a svg icon to uTorrent?

---

### Post by Protoss on 2007-02-24
Is there a way to sort of combine the Open With uTorrent script, and this one? I tried just putting the alltray stuff in front of ./utorrent but it doesn't work.

---

### Post by Kiwi-Hawk on 2007-04-09
Hi 
Does anybody know if one can use a common directory foe Utorrent from both Linux and windoz so one could run either copy depending on which desktop one happened to be on

Cheers
Kiwi-Hawk

---

### Post by Petester on 2007-04-11
Does this work in edgy? I only see dapper...

---

### Post by Sammi on 2007-04-11
I used these instructions for Edgy. Don't see what in this guide could be Dapper specific.

---

### Post by brodiepearce on 2007-04-14
I followed the guide, with some slight modifications:

Instead of having utorrent installed in it's own folder in the Home directory, I have it stored in .wine/drive_c/utorrent.exe, same goes for the icon.  This shouldn't alter anything should it?  Because when I do the killall gnome-panel command, everything reappears as it was before the command.  

If I start AllTray manually from Applications and select an open uTorrent window, it puts an icon in the notification area, **as well as** the original uTorrent icon, except it has the AllTray icon image instead, and I still get the usual issues with maximising and minimising.

---

### Post by crhylove on 2007-04-27
I found some bitchin' icons on deviant art for utorrent:

[http://www.deviantart.com/deviation/26505210/](http://www.deviantart.com/deviation/26505210/)

Enjoy!  My Feisty desktop is really starting to shine!

rhY

---

### Post by andlinux21 on 2007-04-29
Thanks you for doing this HOWTO because I cant go without uTorrent

---

### Post by zedfrugnug on 2007-04-30
> **Kimm said:**
> 
Edit:
Remember to disable to original tray icon in preferences.

Don't wanna sound stupid, but how do I do this?

Everything works almost perfect; utorrent minimizes to tray, but it also shows on the taskbar.

---

### Post by YokoZar on 2007-05-01
> **zedfrugnug said:**
> Don't wanna sound stupid, but how do I do this?

Everything works almost perfect; utorrent minimizes to tray, but it also shows on the taskbar.This is a bug in Wine.  You'll find a similar problem with eMule

To get utorrent minimized to the tray, you'll need to right click the tray icon and select "hide/show utorrent"

---

### Post by pt123 on 2007-05-01
Anybody got it to work on edgy? how about fiesty?

---

### Post by emkubed on 2007-05-09
Working fine for me under Feisty in a VM.

---

### Post by tripleboot on 2007-05-26
No problems running on feisty.  Just installed utorrent to desktop (older version-1.5 beta, don't trust newer versions since Bram Cohen sold out) right click and open command-type in wine and off to the races.  Unable to move tabs on utorrent. nobiggie.

---

### Post by misfitpierce on 2007-05-26
Exactly do not get a new version of utorrent... RIAA made a deal with bittorrent and it was sold to them. Bad move trusting utorrent regardless... Transmission, Azureus, or some other client is recommended

---

### Post by pt123 on 2007-06-09
Because I had already installed Utorrent through Wine I had to use this command to get it to work with all tray:

```

alltray --icon /home/par/Settings/icons/utorrenteh8.png wine "/home/par/.wine/drive_c/Program\ Files/uTorrent/utorrent.exe"

```

But clicking on the utorrent icon in all tray didn't maximize or minimize the utorrent window.

Even when I tried different combinations of tray preferences in utorrent.

But trying  tis "how-To" I found that the stability of the utorrent window in Wine had improved, before I had to run utorrent in wine's "virtual" desktop. :D

---

### Post by LordKelvan on 2007-06-11
Hey:

I have alltray working with beryl and utorrent !!! Yay! :D  However, I've noticed that running it with alltray causes this issue with utorrent where there is a disconnect between where I see my mouse cursor and where the program thinks it is.  For example:

item1
item2
item3
item4
item5

If the above was a menu, then my cursor will be pointed at item4, but item2 will be highlighted.  When my cursor is pointing at item5, item3 is highlighted, and so on.  Does anyone know how to fix this?

On a side note, pt123:  Thanks man, you indirectly helped me with your post (I saw that there was a space in my path to utorrent.exe that wasn't being escaped properly).  As for your problem, have you tried adding the "--show" flag?

---

### Post by khristian on 2007-06-19
I got the utorrent working with wine. It opens, and sits in the tray, and starts automatically all that was already being downloaded. fine, so far.
but after I minimized it to the tray (with double-click), the window won't come back.
I didn't try the alltray thing yet, but I think the question fits here :P

---

### Post by khristian on 2007-06-19
> **Kiwi-Hawk said:**
> Hi 
Does anybody know if one can use a common directory foe Utorrent from both Linux and windoz so one could run either copy depending on which desktop one happened to be on

Cheers
Kiwi-Hawk

I use uTorrent like this. I've separated a folder in my windows-accessible partition and store all the torrents' data in there. 
If I start a torrent in Windows, I just have to log into Ubuntu, open the same .torrent file and make uTorrent save it in the same directory. But I usually force a recheck of the torrent data before continuing. So far, it works fine :)

---

### Post by Trueno22 on 2007-08-12
sweet

---

### Post by -emory- on 2007-09-28
Wow. You are my hero! I've been trying to get this to work *literally* for months :guitar: THANKS!

---

### Post by Senior Ah Me on 2010-03-19
Oh Wow

For some reason my whole post was wiped before it was published, probably a combo of a script blocker and 3:45 AM.

I take no credit for this....a fix to allow one to open ANY file with your fav wine-dozed applications...
Well the tutorial is for uTorrent, but the rest follows quite simply and logically.

In 3 Steps then:

1) sudo gedit /usr/local/bin/uTorrent

2) Copy and paste this:


#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/uTorrent
echo ""
if [ "$1" != "" ]; then
    dt=`date +%s%N`
    cp "$1" /tmp/$dt.torrent
    var="Z:\\tmp\\"$dt".torrent"
    wine "uTorrent.exe" "$var"
else
    wine "uTorrent.exe"
fi


3) Make the script executable with :  sudo chmod +x /usr/local/bin/uTorrent


Then in Firefox try to open a torrent file, choose "Open with" 
Browse to /usr/local/bin and choose the script you made...click on "Do this automatically from now on"
The same for ANY torrent file in Nautilus Dolphin or whatever.


OK...so I'm partial to Irfanview...so:

1) sudo gedit /usr/local/bin/IrfanView

2) Copy and paste this:


#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/Irfanview
echo ""
if [ "$1" != "" ]; then
    dt=`date +%s%N`
    cp "$1" /tmp/$dt.jpg
    var="Z:\\tmp\\"$dt".jpg"
    wine "i_view32" "$var"
else
    wine "i_view32.exe"
fi


3) Make the script executable with :  sudo chmod +x /usr/local/bin/IrfanView

ETC

OK the one problem is the programs in question make a copy of the file (/tmp) and reference THAT copy.
Makes it a bit annoying for when you want to save an edited version of say a picture or text file. Anyone has a fix for this, I'd be interested.


Anyways....mostly I do music, and my great dream has been to dump Windohs and have a recording DAW (Digital Audio Workstation) in Linux. While I haven't quite totally kicked the Microsoftheaded habit...I now do most of my recording in my UbuntuStudio DAW. Anyone passionate or interested in this....well I'll be glad to help, or accept some.

[IMG]http://photos-h.ak.fbcdn.net/hphotos-ak-ash1/hs500.ash1/27307_103133686385305_100000660211055_87820_3270498_n.jpg[/IMG]

[IMG]http://www.facebook.com/photo.php?pid=87821&id=100000660211055[/IMG]

Peace

---


---
title: "*Ubuntu HOWTO Guide*"
date: 2008-10-03
forum: Outdated Tutorials &amp; Tips
---

### Post by kylet450 on 2008-10-03
Welcome to my thread on linux tutorials,
those of you that dont know linux read this:

[http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)

Contents:
_________

1). Intro
2). How to install ubuntu + nvidia drivers ( graphics )
3). How to install wine ( lets you play windows games under linux eg: cs:s )
4). How to install steam + cs:s etc..
5). How to update your distro
6). How to skin your distro
7). Windows < Linux Applications
Cool. Install important Apps ( eg. Windows messanger )
9). Runescape fullscreen + JAVA installation
10).




1). Intro

OK, first of all dont lock this it is a work in progress over the next few days/weeks you will watch this grow. I know that most of you have never heard of linux before, so your going back to school and i am teaching you! cool4.gif

Choosing your linux distro

There are countless linux distros out there, you need to choose 1 or 2 to settle down on. They all do different jobs eg. Servers, Gaming, Multimedia
This guide will be based around UBUNTU linux, hence my name, but if you have ANY questions about any linux distros, feel free to ask. Ubuntu is easy to use and is good for beginners, i have been using ubuntu for 6 years and grown really fond of it. I reccomend that you pick this one for this guide.

List of popular linux distros here: [http://distrowatch.com/](http://distrowatch.com/)
Ubuntu: [http://www.ubuntu.com/](http://www.ubuntu.com/)

((INTRO IS NOT COMPLETE))


2a). Installing Ubuntu

Right go to: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and download ubuntu - if you got duel core processor or higher get i686 or x64. If you havent get x36 or i386.

Get a blank Disk and burn the .iso image to the disk BURN IT AS A BOOTABLE DISK

Now install a blank Harddrive, if you dont know how to, google it or you can go over winxp or whatever is on it.

After reboot computer and hold down the DELETE or Del key NOT BACKSPACE to get onto the bios. Set the 1st boot device to cd-rom is it isnt already. If you dont know what to do consult your manual or google it.

Put disk in, reboot comp dont press delete and boot onto ubuntu, select try ubuntu at the menu if you want to try it, if not go straight to install ubuntu
It is pretty easy to install when it says partitioning options select guilded and install. YOU WILL LOSE ALL DATA ON THAT HARD DRIVE I AM NOT RESPONSIBLE FOR ANY DAMAGE CAUSED.

I asume now that you have installed ubuntu and you want a cup of tea so go get one!
Take the disk out and reboot onto your new system!

INSTALLING graphic drivers.

On the top bar there should be something called termanial, hover over it to find it. Once you opened it type:

QUOTE
sudo apt-get install envyng


Open it applications -> System Tools -> EnvyNG
Use recomended options and install
Then in termanial type:

QUOTE
glxgears

If they run smooth you have installed nvidia drivers GRATZ!

If you got ATI card tutorial on it coming soon, stay tuned!

3). Wine - Coming 1st July

Open up termanial and type:
QUOTE
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Then:
QUOTE
sudo wget [http://wine.budgetdedicated.com/apt/source...st.d/hardy.list](http://wine.budgetdedicated.com/apt/source...st.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

After:
QUOTE
sudo apt-get update

Finally:
QUOTE
sudo apt-get install wine

Now you can run window apps in linux =)

Configuring Wine

Open up termanial and type:
QUOTE
winecfg

Go to drives and click on autodetect then applications and select windows version: XP

Congratz you got wine installed you can now run 90% of windows apps! =)

4). Installing Games
Steam, Half-Life, Half-Life 2, Counter-Strike 1.6 and Source with Wine

Download steam to the desktop.
Then open termanial and type:
QUOTE
cd Desktop
Then...
QUOTE
wine msiexec /i SteamInstall.msi

Install normally dont change install directory.
Once installed, log in and download your favourite games!
NOTE: Not all games will work but Most if not all Valve games work flawlessly
IMPORTANT: Before you play any game on steam select it, click properties and launch options and add in the box:
QUOTE
-dxlevel 70 -width * -height *
* - your monitors resoultion
The games should work fine now, if not post below.
Im not saying that non steam games dont work, most do just right click the installers and open with: wine windows emulator.

5). How to update your distro

This is easy

Open up termanial and type: sudo apt-get update
Then: sudo apt-get upgrade

DONE

6). How to customise your distro

Go to: [http://www.gnome-look.org/index.php?xcontentmode=100](http://www.gnome-look.org/index.php?xcontentmode=100) choose one, download then go System -> Prefrences -> Appearences select install and find it ( usually desktop )

7). OK heres the list that you can use instead of windows apps..

Microsoft Office <> OpenOffice
PhotoShop <> GIMP
Outlook <> Thunderbird
Internet Explorer <> Firefox
Windows Messanger <> Pidgin or kopete

I will add some more later, i wont add them all as there are 30000+ but EVERY WINDOWS APP HAS A LINUX EQUIVELLANT

Cool. APPS

Open Termanial: sudo apt-get install pidgin
Thats windows messanger

If you need anymore post below and i will add and tell you how to install

9). Java

Go on firefox and load up runescape any world it should say install missing plugins, follow that then restart, google: test java to see if it works =)

fullscreen runescape:

1. Open a linux terminal window.
2. Type the following commands:
cd /usr/bin/X11
sudo cp Xorg Xorg-backup
sudo sed -i s/XINERAMA/ZINERAMA/g Xorg
3. Then reboot your linux machine.

To disable the modification:

1. Open a linux terminal window.
2. Type the following commands:
cd /usr/bin/X11
sudo sed -i s/ZINERAMA/XINERAMA/g Xorg
3. Then reboot your linux machine



---

If you liked it join my site at: [http://gameon.site50.net/](http://gameon.site50.net/)

---

### Post by shifty_powers on 2008-10-03
although i like the effort and thought behind it, there are many like this around on the forums.

don't get me wrong, cool for putting the effort in and sharing your experience, but not sure if it is needed....

good start on it mind :D

---

### Post by kylet450 on 2008-10-03
Thanks :D

I wrote it for my old forum and gonna copy to my new ( i wrote it ) but i thought i would share it on here too.

---

### Post by bhadotia on 2008-10-03
Just scanned thriugh your guide.
Good work dude. =D>=D>=D>
That's what I like about the forums here- helpful people.

---

### Post by kylet450 on 2008-10-03
Thanks alot :) :guitar::guitar:

---

### Post by kylet450 on 2008-10-03
bump.

---

### Post by Rocket2DMn on 2008-10-03
Moved to Tutorials & Tips.

---

### Post by kylet450 on 2008-10-03
Thanks.

---

### Post by Kinetic Being on 2008-10-04
its extremly hard to decipher the positions of the sections to find what you want, and to follow along. 
Could you put more formatting into the post.

---

### Post by azhar_mz on 2008-10-04
to kylet
i have 4 problems on how to and need help
1. my company use this mp2 system database
MP2 Enterprise from DataStream system with SQL server edition version 6.0
how can i create work orders i mean use mp2 in ubuntu.
i already use ubuntu 8.04 hardy heron for 4 months. i already can hook to company's server usung the nautilus 
2. how can i print to winsdows shared printer. old printer hp laserjet 5l using LPT1: port and share name is Satar 5L
i tried samba with this printer name
\\ENG-HARUN\HP LaserJet 5L and it does not work.
i've got some info like
(5.2.3790.120(srv03_qfe.031205-1652)) from win xp printer test page but don't know how to use it in ubuntu
3. recently my company change the email server to HQ korean server. i can use Evolution before when the setup was mail.dongwha.com.my now the email server has change and i'm stuck
the email server dongwha-mh.com how can i get into exchange MH server.
4. last but not least i've lost one of my usr desktop. when i boot to ubuntu only desktop background shown and no application or any button. luckily i got other user in administrator and create new usr. my question is how can i get back the old desktop when it's the main /home when i first setup ubuntu (azidarfan-desktop) if not i just want to chg it to az-desktop if possible

please help


thank you

azhar

---


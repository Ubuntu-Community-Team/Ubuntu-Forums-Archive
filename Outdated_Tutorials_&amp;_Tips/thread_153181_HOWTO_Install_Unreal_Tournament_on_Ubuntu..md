---
title: "HOWTO: Install Unreal Tournament on Ubuntu."
date: 2006-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Emperor_ on 2006-03-31
Howto install Unreal Tournament under Ubuntu

This howto will teach howto install unreal tournament under ubuntu (Breezy, but i guess it will work on dapper too). We use the old loki installer with some fixes to get it working. 

Step 0.
First of all, be sure your video drivers are properly working (if opengl games or opengl screensaver runs smooth, your okay!)! Also, you need a Unreal Tournament cd and some basic linux knowledge.

Step 1.
Download ut-install-436.run from:
[http://www.3ddownloads.com/linuxgames/loki/patches/ut/ut-install-436.run](http://www.3ddownloads.com/linuxgames/loki/patches/ut/ut-install-436.run)

Step 2. 
Make it executable:
sudo chmod +x ut-install-436.run

Step 3.
Let's begin the install. Because ./ut-install-436 doenst run out of the box. we have to use a workaround.
use:
sudo ./ut-install-436 --keep

this will create a ut-436/ map, (eg. you downloaded ut-install-436.run on your desktop, ran it, then you should have a ut-436/ map on your desktop /home/<user>/Desktop/ut-436)

Step 4.
Let's complete the install.
Run setup.sh with the following command:
sudo ./setup.sh (if not executable already do: chmod +x setup.sh)

It will ask for the UT Cd (if you have GOTY, insert the first one)
If the installer doenst find your UT cd you can set a other mounting point with the following command:

sudo export SETUP_CDROM=/path/to/other/location

Example (if you have extracted the cd on your hard drive)
sudo export SETUP_CDROM=/media/hardrive2/Games/UT_CD

Example (if you have more then one cd drive)
sudo export SETUP_CDROM=/media/cdrom1

After the installation is complete. We are almost ready to play.

Step 5.

Another bug workaround. If you now type "ut" in the console, it will give a path error (if not, your can skip this step). To fix this try the following:

sudo export UT_DATA_PATH=UT_DATA_PATH=/path/to/ut/System  (Installers path default for unreal tournament is /usr/local/games/ut)

Step 6.

type ut in the console and you will be able to play unreal tournament properly! If not, return to step 5 and check if the path is correct.


We are done!

I will try to find a fix to install umod packages for ut, if some knows, let me know :)

Also, there will also maybe a shorter way to install this, these can be found in other threads (use the search). Atleast this should work for all. 

All feedback is welcome!

---

### Post by slider2800 on 2006-04-07
Hey. That sounds great. I'll try it at home.

But i have a question. How can i install ( if possible ) the UT Patches and the Map Packs? ( .umod )

---

### Post by Big-Wayne on 2006-04-10
[QUOTE=slider2800]Hey. That sounds great. I'll try it at home.

But i have a question. How can i install ( if possible ) the UT Patches and the Map Packs? ( .umod )[/QUOTE]
Hi,
You can try using ASU, it works pretty good. You can get it and info on it here;
[http://ut.abfackeln.com/asu.html](http://ut.abfackeln.com/asu.html)

Give it a try.

---

### Post by PriceChild on 2006-04-13
A few of these things didn't work for me...

[quote=Emperor_]
Step 3.
Let's begin the install. Because ./ut-install-436 doenst run out of the box. we have to use a workaround.
use:
sudo ./ut-install-436 --keep[/quote] I think you've changed the name of this file half way through, shouldn't it still have ".run" at the end?

[quote=Emperor_]
this will create a ut-436/ map, (eg. you downloaded ut-install-436.run on your desktop, ran it, then you should have a ut-436/ map on your desktop /home/<user>/Desktop/ut-436)[/quote] 
As well as this, using  sudo ./ut-install-436 --keep also starts the graphical installer, rendering Step 4 useless to me :S

[quote=Emperor_]
Step 5.

Another bug workaround. If you now type "ut" in the console, it will give a path error (if not, your can skip this step). To fix this try the following:

sudo export UT_DATA_PATH=UT_DATA_PATH=/path/to/ut/System  (Installers path default for unreal tournament is /usr/local/games/ut)[/quote] 
I don't understand this Step 5... i am getting the path error.

What do i need to paste into terminal? Something like 

```
$ sudo export UT_DATA_PATH=UT_DATA_PATH=/usr/local/games/ut/System

``` 
I'm a pretty big noob at most things, and This doesn't work:

```
sudo: export: command not found
``` 
Someone help please :)

Pricey

P.s. I LOVE your joke slider :D simple things :)

---

### Post by crossieh on 2006-04-14
```
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?
```

I got something like that. Heeeeeeeeeeeeeeeeeeeelp :(

EDIT: Problem solved. Google is a friend <3

Anyway, I shall proceed to my next problem:

```

LoadMap: Entry
Failed to load 'Entry': Can't find file 'Entry'
Failed to load 'Level None.MyLevel': Can't find file 'Entry'
appError called:
Failed to enter Entry: Can't find file 'Entry'
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down
```

I know it has something to do with compressed mapfiles.
Someone? please :(

---

### Post by Brando569 on 2006-04-14
awesome, ill have to try this!

---

### Post by Emperor_ on 2006-04-14
> LoadMap: Entry
Failed to load 'Entry': Can't find file 'Entry'
Failed to load 'Level None.MyLevel': Can't find file 'Entry'
appError called:
Failed to enter Entry: Can't find file 'Entry'
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down

The problem is caused by corrupted map file / texture's. Please reinstall the game, that worked for me.

---

### Post by Emperor_ on 2006-04-14
[QUOTE=PriceChild]A few of these things didn't work for me...

 I think you've changed the name of this file half way through, shouldn't it still have ".run" at the end?

 
As well as this, using  sudo ./ut-install-436 --keep also starts the graphical installer, rendering Step 4 useless to me :S



I'm a pretty big noob at most things, and This doesn't work:

```
sudo: export: command not found
``` 

well first you could make yourself a super user, to do this we have to give root a new password.
type this: 

sudo passwd root

and give a password.

now type this: su
login 
and then try the following export command:

export UT_DATA_PATH=/usr/local/games/ut/System

I will rewrite/ edit the tutorial soon to make it work. Hold on :)

---

### Post by Big-Wayne on 2006-04-14
Hi again,

Dunno if it helps but go have a look here;
[http://www.princessleia.com/UT.php]("http://www.princessleia.com/UT.php")

---

### Post by woody7 on 2006-04-14
I found that even though I had the CD's, and only 1 CD-ROM drive, I had to export SETUP_CDROM=/media/cdrom0, otherwise, the ut-install-436-GOTY.run script would just hang there.

Breezy on Dell Latitude PPL notebook, just installed Unreal Tournament GOTY.


... Woody

---

### Post by nolongerlivecd on 2006-04-15
Does this only work with Unreal Tournament for Linux CD or what?

---

### Post by SilentGreg on 2006-04-15
I finished the install. However when I type **ut** I hear the sound in the background and my screen goes completely blank. Infact, the only way I can get back to my desktop is if I SSH into my box through another box on my network and kill off the UT process. :mad: 

Any ideas? I'm running Breezy with nVidia drivers installed.

Thanks for any help!

---Greg

---

### Post by SilentGreg on 2006-04-15
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

My xorg.conf file if it helps... ](*,) 

---Greg

---

### Post by PriceChild on 2006-04-15
it's still not workign for me :(

Even after typing the command under su, no error is returned, but i still get nothing to work :(

UPDATE

[http://www.linuxquestions.org/questions/showthread.php?threadid=238010](http://www.linuxquestions.org/questions/showthread.php?threadid=238010)

showed it being used without the sudo or su which has made it not have that error!!!

Instead:

```
pricechild@thebeast:~$ ut
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Failed to load 'Entry': Can't find file 'Entry'
Failed to load 'Level None.MyLevel': Can't find file 'Entry'
appError called:
Failed to enter Entry: Can't find file 'Entry'
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down
```

---

### Post by PriceChild on 2006-04-15
Ok... found out why from here:

[http://www.linuxquestions.org/questions/showthread.php?t=62343](http://www.linuxquestions.org/questions/showthread.php?t=62343)

>  I read somewhere that you had to decompress **each** map using ucc through a terminal:
ucc decompress /install/path/to/ut/Maps/CTF-Face.unr.uz
Then it extracts them to /home/username/.loki/ut/System/ which means you have to move them to /install/path/to/ut/Maps to play.

This works perfectly :) But i cba to do each file individually....

> for i in /opt/ut/Maps/*uz ; do ../ucc decompress "$i" ; done

This is an whole post, which supposedly worked for people. However its for maps in /opt/ut Whereas mine are in /usr/local/games

Could someone please help me get this command to work for me? I know this decompress things works, as doing it to entry and city entry has allowed me to finally loads up UT.

Pricey

---

### Post by m*i*l*e*s on 2006-04-15
[QUOTE=crossieh]```
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?
```

I got something like that. Heeeeeeeeeeeeeeeeeeeelp :(

EDIT: Problem solved. Google is a friend <3

Anyway, I shall proceed to my next problem:

```

LoadMap: Entry
Failed to load 'Entry': Can't find file 'Entry'
Failed to load 'Level None.MyLevel': Can't find file 'Entry'
appError called:
Failed to enter Entry: Can't find file 'Entry'
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down
```

I know it has something to do with compressed mapfiles.
Someone? please :([/QUOTE]

** Hi, your not wrong, I got the same thing and after pokeing about found this script:-

#!/bin/sh
# Change this to YOUR install-dir of UT
#
INSTALLDIR=/usr/games/ut

cd $INSTALLDIR/System

for i in `ls ../Maps/*.unr.uz`
do
ucc decompress ../Maps/$i -nohomedir
done

rm ../Maps/*unr.uz
mv *.unr ../Maps

echo "..:: Done! ::.." 

** Dont forget to change the INSTALLDIR to you location, eg. /usr/local/games/ut  "in my case" and make it exe! eg. chmod +x 'whatever you called the script'

After a few mins of unpacking I ran ut it it sparked up no problems.

Thanks to **jdodson** for the script. :D

---

### Post by PriceChild on 2006-04-16
For those with the GOTY edition, i've found this little beauty:

[http://www.3dgamers.com/dlselect/games/unrealtourn/ut-install-436-goty.run.html](http://www.3dgamers.com/dlselect/games/unrealtourn/ut-install-436-goty.run.html)

Will let you know how i get on.

---

### Post by BLTicklemonster on 2006-11-05
Easier install, and a script for making a cache cleaner, plus a link to a umod extractor:

[http://ubuntuforums.org/showthread.php?p=1717290#post1717290](http://ubuntuforums.org/showthread.php?p=1717290#post1717290)

---

### Post by Fsngruv on 2006-11-09
I get the same message as crosseih does, but i'm having a problem reinstalling,

owenby@owenby-desktop:~$ sudo /home/owenby/Desktop/ut-install-436.run
Password:
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 436 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]
owenby@owenby-desktop:~$ sudo /home/owenby/Desktop/ut-install-436.run
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 436 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]
owenby@owenby-desktop:~$ sudo /home/owenby/Desktop/ut-install-436.run --keep
Creating directory ut-436
mkdir: cannot create directory `ut-436': File exists
/home/owenby/Desktop/ut-install-436.run: line 122: Cannot create target directory: command not found
/home/owenby/Desktop/ut-install-436.run: line 123: you should perhaps try option -target OtherDirectory: command not found

I've tried deleting the .../ut directory but it tells me access is denied, did i miss a step somewhere?

---

### Post by Fsngruv on 2006-11-12
Try this thread for all of you who are trying to decompress the maps easily, worked like a champ in dapper.  It'll just reinstall over your original install and include Disc 2  [http://ubuntuforums.org/showthread.php?t=217039](http://ubuntuforums.org/showthread.php?t=217039)

---

### Post by oceanside on 2010-03-19
I tried this and had an issue in the beginning:

```
sudo ./ut-install-436.run --keep
Creating directory ut-436
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 1237260170 2341625838
```

Figured the download was bad so I downloaded it again and got the same error. Any ideas?

---

### Post by OpressedCalamity on 2010-06-17
Fail.
/root/.setup5344: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Doesen't work.

---

### Post by pratzy on 2010-06-17
I would suggest installing VIRTUALBOX on Ubuntu and then install Windows on it. It will not only let you install your favorite game on Ubuntu but also give you complete functionality of Windows too.

---


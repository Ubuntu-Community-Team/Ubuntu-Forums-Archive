---
title: "Getting the HP tx2000z to work"
date: 2008-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by TorchlightJay on 2008-02-26
So i got a tx2000z not too long ago, ordered it the day it came out. At first I wanted to throw it out the window but now I have gotten it to work just fine with Linux after about a month of working on it. 

Here is what I had problems with:
-Audio (Headphone jack didn't work)
-Wireless
-Lightscribe
-Wacom
-Fingerprint Reader

And now all works (except wacom). 

I couldn't for the life of me get Gutsy Gibbon to work so I took a chance and tried the Alpha 5 version of Hardy Heron. Though it is an alpha, for the most part it is pretty steady. You have to do some upgrades at first but it works. You can get the iso at 
[http://cdimage.ubuntu.com/releases/hardy/alpha-5/hardy-desktop-i386.iso](http://cdimage.ubuntu.com/releases/hardy/alpha-5/hardy-desktop-i386.iso)

Now you are installed. let's get working on the sound. 

This is a really simple fix. Go to your terminal and type:
```
 sudo gedit /etc/modprobe.d/alsa-base 
```
and at the end add "options snd-hda-intel model=hp" to the bottom of the file and save it. Now type:
```
 sudo /etc/init.d/alsasound restart 
```
Now your sound should work. 

WIRELESS
Ndiswrapper is your best bet here. In synaptic and install ndiswrapper-common, ndiswrapper-utils-1.9, and cabextract. Those will help. Now I have tried a lot of drivers and this one gave me the best luck:
[http://h18000.www1.hp.com/support/files/hpcpqnk/us/download/24001.html](http://h18000.www1.hp.com/support/files/hpcpqnk/us/download/24001.html)

In the terminal navigate to the file you downloaded the file to and type:
```
 sudo cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper

```
and you will want to do a "sudo gedit /etc/modules" and add ndiswrapper to the end of it. That will make ndiswrapper open on boot. 
That's Wireless. 

Fingerprint Reader:
just use this site. Everything I tell you will be verbatim to it.
[http://www.reactivated.net/fprint/wiki/Main_Page](http://www.reactivated.net/fprint/wiki/Main_Page)
download the files, there are some dependencies you may have to get from synaptic. 

Lightscribe:
Go to these sites to install lightscribe utility and drivers. 
[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)
--You just need the system software and simple labeler --
[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)
-- third party labeler for lightscribe --

Webcam:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
That sight has all you need. 

WACOM
Bad news guys, at this time linuxwacom doesn't support our type of Tablet PCs. Let me explain. Older tablet PCs with Wacom active digitizers used to be ported to the serial port. Newer ones are ported to the usb (use "lsusb" code to see for yourself) and linuxwacom doesn't yet support tablet PCs with their wacom mapped to their USB port. 
"Option "ForceDevice" "ISDV4"
                   tells the driver to dialog  with the  tablet the  Tablet PC
                   way.  Right now we only support serial Tablet PC.  It is a 
                   special Wacom IV protocol,  called ISDV4 protocol.  This 
		   option is mandatory for Tablet PC."

However the news isn't all bad. I read the development pages and they are working on it. 

Synaptics:
```
 sudo apt-get update 
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
Once you do that upgrade after installing Alpha 5, it should start working (or at least it did for me). The newer kernel (2.6.24-10-generic) works really well. 
You can also install gsynaptics and configure it with a nice gui. 

NVIDIA
install nvidia-glx-new from synaptic, it'll work fine. 

Screen Rotation:
These tutorials helped me.
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

and also make sure xrandr is installed (Synaptic)

OKAY
So ya, that is what i did. Sorry if it's not too detailed but that is what I did in a nutshell. Everything seems to work. Feel free to ask me if you have questions or comments. If anyone has any advice regarding this, I am willing to listen. Thanks all.

---

### Post by pAt84 on 2008-03-14
Could you be more specific on the webcam? I downloaded the uvc and compiled it but I still dont get the webcam to work in skype?

Pat

---

### Post by ACLBandit on 2008-03-15
Thank you so much for this post! This computer isn't exactly being my new best friend.

However, you DID get my sound going. Which means, luckily enough, I have music while I tinker. ^^ So thank you LOTS for that.

Did you do anything else with wireless, though? That's the last thing I need before I can call this thing "acceptable," and I cannot get it to work for anything. My little wireless switch is very happily displaying its LED a neon red color, and in the (much-more-shrunken-and-formatted/reinstalled) Vista boot it's a happy blue.

Also, you said that your wacom actually *worked*? Where/how did you install the necessary utilities, and where would I pass the forced serial options ("Option "ForceDevice" "ISDV4")?

---

### Post by pAt84 on 2008-03-16
No, he did not get the Wacom to work. It is just formulated a little unclear. ;)

As for your wireless problem. Which release of Ubuntu are you using? Gutsy? Did you already try using ndiswrapper? The following guide might be what you are looking for: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

As for me I am using Gutsy and I actually had to compile the newest ndiswrapper to make it work. Let me know if the above guide helps you out. If not try to compile the newest ndiswrapper and give an update please.

Pat

---

### Post by TorchlightJay on 2008-03-17
I had to compile the newest ndiswrapper as well (1.52 if I am not mistaken). I am not using Gutsy however, I am using Hardy Heron Alpha. IT is working pretty well. I just had horrible luck with Gutsy but Hardy seems to work seemlessly (minus the wacom issue).

---

### Post by pAt84 on 2008-03-17
It worked pretty nice for me on Gutsy. I had to recompole ndiswrapper and alsa but that was basically it.

TorchlightJay, could you be more specific on the webcam? I downloaded the uvc and compiled it but I still dont get the webcam to work in skype?

---

### Post by TorchlightJay on 2008-03-17
well what I did in addition (forgot to mention it) was install webcam, webcamd and that seemed to help me a lot. I haven't tried it too often but I did have a point where it took pictures of me

---

### Post by ACLBandit on 2008-03-17
> **TorchlightJay said:**
> I had to compile the newest ndiswrapper as well (1.52 if I am not mistaken)

Wonderful-- I just used the one from the repositories, so I'll try a compile of the newest version of ndiswrapper. 

Also, sorry about the misread on your wacom. But they are working on that currently, as I think you said, so we won't have to wait long ^_^

EDIT: I compiled the newest version and installed the driver you recommended, but it didn't seem to do anything. Running "ndiswrapper -l" returns "bcmwl5: driver installed." However, if I install the bcmwl6, it says "driver installed, hardware present." Either way, it doesn't matter, sadly enough, because it doesn't turn the wireless on. No options for it under any networking tools, and my happy little switch is still an angry orange-red. 

By the way, I am on the recommended Hardy Heron alpha, although it is alpha *6*. Will that affect anything?

Any tips? :(

---

### Post by TorchlightJay on 2008-03-17
Ya, I am using alpha 6 now too. 

Are you on kernel 2.6.24-11? That one has a bug on it that keeps broadcom from working, even if you are using ndiswrapper. 

The most recent version is 2.6.24-12, do an upgrade and see what happens (of course assuming that you haven't already).

The file I listed is the one that worked for me. I searched all over the web for a variety of drivers and that one gave me the best luck. Almost all of them said that the driver was installed and hardware was present but only that one got me a bluelight. 

make sure to add ndiswrapper to your /etc/modules file. 

also do a "depmod -a" and a "modprobe ndiswrapper"

You may have to do "rmmod ndiswrapper" and then do the steps listed above to remove old ndiswrapper modules and load the newer ones.

---

### Post by pAt84 on 2008-03-17
Did you remove the old ndiswrapper before compiling the new one? Did you also remove all wireless drivers in ndiswrapper before doing that?

Just to be sure, did you run 'sudo modprobe ndiswrapper' after installing the driver?

> **TorchlightJay said:**
> well what I did in addition (forgot to mention it) was install webcam, webcamd and that seemed to help me a lot. I haven't tried it too often but I did have a point where it took pictures of me
Thanks man, that really did it.

Pat

---

### Post by ACLBandit on 2008-03-17
> **TorchlightJay said:**
> The file I listed is the one that worked for me. I searched all over the web for a variety of drivers and that one gave me the best luck. Almost all of them said that the driver was installed and hardware was present but only that one got me a bluelight. 

So I did the rmmod ndiswrapper, ran a make uninstall, and apt-get remove ndiswrapper-*.

I then reinstalled from source, and installed bcmwl5. It still stated hardware was no present, but I continued. After following the rest of the steps precisely, I rebooted and was greeted with... absolutely nothing :(

The light is still red. What  else can I try? 

(by the way, I *did* try flipping the  switch on just to make sure, but I still got nothin' :( )

---

### Post by TorchlightJay on 2008-03-17
Let's start from the beginning.

remove ndiswrapper from source and from synaptic.

install ndiswrapper from [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)
and be sure to read the README file when you get ready to install. 

Now once you are done installing, rmmod ndiswrapper.

Look for the sp34152.exe driver. (You can do a google search). Cabextract it and install bcmwl5.inf via ndiswrapper. Then you type ndiswrapper -m and "depmod -a" then "modprobe ndiswrapper". Also, add ndiswrapper to /etc/modules. That should get you working. 

Make srue you are on a decent kernel as well because 2.6.24-11 doesn't like broadcom.

---

### Post by ACLBandit on 2008-03-17
Nope, still nothing, sadly enough. 

However, I did think of something. Here is the entry for my Ubuntu in the menu.lst: 
```

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=1d05117b-67d2-473c-927e-ea5a090cb47a ro quiet splash noapic irqpoll
initrd		/boot/initrd.img-2.6.24-12-generic
quiet
```

Notice the kernel arguments I'm passing, "noapic" and "irqpoll". I have no idea why those are there. I remember adding both of them, but I have no clue why. To be honest, I don't even know what either of them do. I'm going to try booting *without* those, and see what happens. But if that sheds any light on my situation, just lemme know.

Also, if this doesn't work, who can recommend a nice, small, compatible USB wireless network adapter for my laptop while I'm elsewhere? :)

---

### Post by pAt84 on 2008-03-17
I doubt your problem is connected to the boot parameters.

If you have time you might want to try a complete reinstall and after a fresh install compiling ndiswrapper and adding the version5-driver. Chances might be that you just messed up your system too much with all the installations you did.

Do me a favor and give me what 'ndiswrapper -v' gives you. Also tell us the exact model name (I, for example, am on a tx2050eg) please. Last but not least do 'lspci' please. Do you get the following line? 
```

 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

```

Which Ubuntu version are you on? 32 or 64bit?

Pat

---

### Post by ACLBandit on 2008-03-17
Yes, I was actually considering a fresh install just to be certain, interestingly enough. I'll do that if I can't fix this. 

I am on Ubuntu Hardy Heron Alpha 6 32-bit.

This is a tx2000z.

**lscpi returns:**
```
03:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

```

This means that I don't have the exact same card as you-- I believe that I opted for the one without 'n' support, actually. Yikes.

**ndiswrapper -v**
```
 ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-12-generic/misc/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-12-generic SMP mod_unload 586 

```

---

### Post by ACLBandit on 2008-03-17
HAHA!!! Finally, I have it. I didn't have to do a fresh install-- your 'lspci' listing got me off looking for posts that were about that specific card, rather than this specific computer model. I would up on a forum archive where someone had the same issue. It was solved with a driver from dell. 

So, if you happen to have this computer and you can't get the wireless running, see what the 'lspci' command returns. If it says 
```
03:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
```
Then download this: [http://ftp.us.dell.com/network/R174291.exe]("http://ftp.us.dell.com/network/R174291.exe").

Afterwards, you'll have to run the program with wine (sorry, guys) to extract the files from the exe. After the program has run until the point where it tries to begin its install and then fails, just follow the steps provided elsewhere in this post, only for the bcmwl5 file under the "DRIVER" folder which was just created by the R174291.exe file. Make sure to remove the other drivers first.

Pat, Jay, thanks a lot for helping me through this two-day-long and rather nasty wireless ordeal ^_^

---

### Post by pAt84 on 2008-03-18
Nice.

Did one of you get the remote to work nicely? It basically works out of the box but I would like to map different buttons to different things. for instance I can not control vlc with it and there is not really a config file for lirc for it.

Pat

---

### Post by ACLBandit on 2008-03-18
I got it to do everything I wanted it to do, yeah. It basically emulates keyboard functions, so it worked out of the box.

I set my default media player under System-->Preferences--> Preferred Applications as xine-ui, and then set the button for DVD to open the default media player under the System-->Preferences-->Keyboard Shortcuts.

In the shortcuts window I also set the next/previous track buttons and the volume increase buttons. I set the Windows button on the remote to open a terminal. The weird arrow-circle button, since I didn't know what it was really for, also ejects my CD drive. 

To get the media buttons to work in Amarok, I downloaded the "Gnome Multimedia Keys" script found here:
[http://www.kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910]("http://www.kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910")
and then installed it. 

Voila! Sexy remote ^_^

---

### Post by TorchlightJay on 2008-03-19
Sounds good. Just one quick question, how did you know which buttons were which when setting it up? That is where it all fell apart for me. I am using KDE btw.

---

### Post by ACLBandit on 2008-03-19
> **TorchlightJay said:**
>  I am using KDE btw.

Yikes. I know absolutely nothing about KDE; I mean, I booted Knoppix a couple of times back when I was on Fedora and it wasn't a live-bootable OS, and Knoppix was KDE, but anything I had learned there has since been forgotten since switching to Ubuntu and always having a live-bootable GNOME system.

I do know, however, that in GNOME, under the Keyboard shortcuts menu, you just click on the action you want and then press the remote button that you want to do this action. Perhaps KDE has something similar?

Also, if you happen to use Amarok, you can set up global hotkeys from one of the menus in the program, and I do know for a fact that those settings can be edited by simply pressing the remote button you wish to use. 

I hope this helps; if not, I'm sorry.

---

### Post by TorchlightJay on 2008-03-20
Got it working. Just went straight into KDE Control Center and set the keys. Everything is cool now.

---

### Post by ACLBandit on 2008-03-20
Wonderful. Glad to hear you got it working. By the way, how do you set keys up in VLC? Its interface isn't exactly the friendliest when it comes to custom keymappings...

Also, how will I know when the wacom will work? What is the specific name of the device which will need to be supported by Linux Wacom in order to make it work?

---

### Post by TorchlightJay on 2008-03-22
linuxwacom.org is the site to keep watch on. Look up Tablet PCs on it and it will list when it allows for USB enabled Tablet PCs. That's what we are lacking.

As for VLC, you need to probably look that up on their website. I am not too sure since I never use it.

---

### Post by TomtheWombat on 2008-04-02
I will be the owner of a new tx2000z in a few days.  Hopefully the Wacom is working soon.  The Lenovo T61t has a serial touch screen/digitizer and that still isn't working in linux without patching sources and recompiling.  I guess that we are all in this together, though!

Has anybody got the native broadcom wireless driver working for this laptop?

---

### Post by ACLBandit on 2008-04-02
I wouldn't bother with the native drivers--the ndiSwrapper method is easy if you follow the steps in this post-- make sure to run lspci to ensure you have the same card as one of us, though.

---

### Post by TomtheWombat on 2008-04-13
Luckily, a patch is being worked on specifically for our laptop.  (Thank HP for rock bottom prices.)

Bugtracker:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127?](http://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127?)

Discussion:
[http://sourceforge.net/mailarchive/forum.php?thread_name=4b5e638b0804090734t490442e8jc44da60df301e580%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=4b5e638b0804090734t490442e8jc44da60df301e580%40mail.gmail.com&forum_name=linuxwacom-devel)

I haven't had the time to monkey-fart with it this weekend.  I wish you luck!

---

### Post by TomtheWombat on 2008-04-14
WARNING:  Your wacom digitizer will stop working every single time the kernel or xorg gets updated if you use this script.  Even worse, Xorg will refuse to start if newly installed libraries aren't compatible with the ones that you compiled!!

UPDATE:  I updated this post.  The new patch now includes touch screen support!!!

UPDATE: Now includes eraser support and fixes the side button.

If your cursor is laggy on the screen, then you are going to need to add noapic, noirqdebug, and irqpoll to your boot parameters.  This will also fix the other usb issues that you may be experiencing.

First you are going to need to download the latest development version of [linuxwacom]("http://linuxwacom.sf.net"):

```

wget http://internap.dl.sourceforge.net/sourceforge/linuxwacom/linuxwacom-0.7.9-11.tar.bz2

```

You will also need [Andrew's unified patch](http://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127?):

```

wget -O usbtx2000z.patch http://linuxwacom.pastebin.com/pastebin.php?dl=f3d5b9e73

```

You will need a proper development environment::

```

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev

```

Now it is time to extract, patch, compile, and install.  I personally add the configure option --prefix=/usr instead of /usr/local.  You have to manually install the kernel driver.  FYI: If kernel versions change, then things may break.

```

tar xjvf linuxwacom-0.7.9-11.tar.bz2
cd linuxwacom-0.7.9-11
patch -p1 < ../usbtx2000z.patch
./configure --enable-wacom
make
sudo make install
sudo rmmod wacom
sudo cp src/2.6.24/wacom.ko /lib/modules/2.6.24-16-generic/kernel/drivers/input/tablet/wacom.ko
sudo depmod -e
sudo modprobe wacom
sudo rm /usr/local/bin/xsetwacom

```

Now you are ready to edit your xorg.conf!  Run the following command to load it up:

```

sudo gedit /etc/X11/xorg.conf

```

Now you are going to have to add sections for the Wacom input device.

```

Section "InputDevice"
    Identifier "TabletPCStylus"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
    Option "Type" "stylus"
    Option "SendCoreEvents" "true"	
    Option "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
    Option "Button2" "3"  # make side-switch a right button
#  Option "TopX" "225"
   # Option "TopY" "122"
   # Option "BottomX" "26365"
   # Option "BottomY" "16488"
EndSection

Section "InputDevice"
	Identifier "TabletPCStylus2"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
	Option "Type" "stylus"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/input/wacom"
EndSection

Section "InputDevice"
    Identifier     "TabletPCStylus3"
    Driver         "wacom"
    Option         "ForceDevice" "ISDV4"
    Option         "Type" "eraser"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
EndSection

```

and you will need to add the devices to your server layout:

```

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Synaptics Touchpad"
        Inputdevice     "TabletPCStylus"
        Inputdevice     "TabletPCStylus2"
       Inputdevice     "TabletPCStylus3"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

There is a calibration script at [http://www.stanford.edu/~gi1242/per/opensource/hp2710p/](http://www.stanford.edu/~gi1242/per/opensource/hp2710p/).  It doesn't really work well because it calibrates all devices at once.  Therefore your touch screen gets the same calibration as your stylus.

EDITED 04/17 to use a unified patch for the digitizer AND touchscreen.
EDITED 04/20 to include eraser support and fix the side button.
EDITED 04/27 to point to the right devices in xorg.conf.

---

### Post by TorchlightJay on 2008-04-14
That's awesome. I don't know how gutsy I am to try that out but I may just do that in a few. Hopefully this will eventually get working to the way we all want it.

---

### Post by TomtheWombat on 2008-04-14
There isn't really much chance of breaking anything.  I wouldn't reccomend doing it yet unless you want to help figure things out, though.  The stylus is pretty much useless with the lag and lack of calibration.

---

### Post by TomtheWombat on 2008-04-14
In order to eliminate the lag, edit /boot/grub/menu.lst and add the parameters 'irqpoll noirqdebug' to the main kernel you boot off of right behind noapic.  This will also enable your usb2.0 ports :)

P.S.  I missed linux the past week!

---

### Post by ACLBandit on 2008-04-16
I followed your nifty steps, and I can now use my touchscreen! The cursor is EXTREMELY wonky, and that calibration script, as you said, doesn't really do anything at all. However, it's much better than it has been! Thanks a lot, and keep us posted about this! ^_^

EDIT: I lied to you just now-- after restarting the X Server (which I failed to do-- way to follow instructions!), it works just as wonderfully as it does in windows. I can't wait to start using a REAL OS for my note-taking.

However, one feature of Vista that I did like (it's pretty much the only one) was that nifty handwriting-to-text thingy. Is there something like that I could use the same way for linux?

---

### Post by ACLBandit on 2008-04-16
Also, ANOTHER wicked thing I just found (though you may have already discovered it) is that NVidia cards have 90-degree rotation options; this way, you can use your touchscreen in the "sideways mode" just like in that failure of an OS you keep on your other partition! ^_^

Make your device section look like this:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option "RandRRotation" "on"
EndSection
```

Basically, the "Option" line is all you need to add. After restarting X, you can easily enter these commands:

```
xrandr -o left
xrandr -o right
xrandr -o normal

```

and they will flip your monitor in the respective direction. I made 2 shorcuts on my taskbar that flip left and then back to normal.

Now I've just gotta figure out how to flip the wacom, because it does WEIRD STUFF in rotated screen mode

---

### Post by ACLBandit on 2008-04-17
Also, does anyone have the right-click button working? On mine, it acts like the "middle click" of regular mice.

---

### Post by TomtheWombat on 2008-04-17
I'm not sure what is going on with the middle click thing.  That is fairly odd behavior, because you don't even have to touch the screen.  Other people have reported similar issues, though.

---

### Post by TomtheWombat on 2008-04-17
Use 'cellwritier' for handwriting input.  It isn't great, but it works.  One issue is that you can't right click to change things to the correct letters.

I really miss OneNote and Office 2007 in general.  It really is the only thing that Microsoft can do right.  I should have got a tablet that was more compatible with OSX, maybe.

---

### Post by TomtheWombat on 2008-04-17
I updated my instructions with the patch for touchscreen support!  I noticed that it issues a button down command before it moves the cursor, though.  Be careful because it will start dragging things all over.

---

### Post by gjakuipers on 2008-04-17
do you have instructions how to calibrate the tx2000?

---

### Post by TomtheWombat on 2008-04-17
guess and check changing the values in the xorg.conf for right now.  Sorry about that.  :-/

My touchscreen calibration is far off, and I am not looking forward to calibrating it.

---

### Post by ACLBandit on 2008-04-18
Following wombat's instructions, my touchscreen has worked fine ever since with no calibration necessary. The right-click button is the only thing that's been weird at all.

Also, CellWriter is EXACTLY what I was looking for-- not only does it do almost exactly the same thing as the Windows thingy, it does it BETTER and more accurately. Positively AMAZING program. (Especially when you thought you were stuck with xvkbd, lols) 

Something else I noticed: the right-click button, as it is now, ALSO functions as an eraser in the CellWriter program, but nowhere else. The program's documentation says something about middle-clicking will do that, and that's what my button seems to be mapped to. 

So, basically, as soon as I can rotate 90 degrees left, I'm perfectly happy.

---

### Post by TorchlightJay on 2008-04-20
so ya, i got touchscreen to work. still needs callibration but i wi ll run that script when i can. 

any luck with getting the eraser to work?

---

### Post by ACLBandit on 2008-04-20
> **TorchlightJay said:**
> 
any luck with getting the eraser to work?

No luck here, sorry.
The eraser, though, is of less concern to me than right-clicking-- kinda necessary.

---

### Post by Johi on 2008-04-20
Hi @ all
thx wombat for the Install guid ^^
The Stylus and the Touchscreen are working =)
But i have to calibrate it and the pl script doesn't work.
Can someone of the Ubuntu Gurus post an Guid how to calibrate the stylus in the xorg.conf?

My xorg.conf
```

Section "InputDevice"
    Identifier "TabletPCStylus"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
    Option "Type" "stylus"
    Option "SendCoreEvents" "true"	
    Option "Device" "/dev/input/event6"
    Option "TopX" "0"
    Option "TopY" "0"
    Option "BottomX" "1280"
    Option "BottomY" "1024"
EndSection

Section "InputDevice"
	Identifier "TabletPCStylus2"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
	Option "Type" "stylus"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/input/event7"
EndSection

```

sry for my bad english ^^"

EDIT: another Question. Is it possible to use the Stylus but DISABLE the Touchscreen like in Windoof?

---

### Post by TomtheWombat on 2008-04-20
Johi: remove your TopX, TopY, BottomX, and BottomY lines.  There is a chance that your screen will be 'close enough' to calibration without them.  Otherwise, you need to guess values for these parameters right now.

---

### Post by TomtheWombat on 2008-04-20
I updated the instructions to include the new patch for eraser support and a line to fix your problem.  You are going to need to rerun all the commands and rebuild the kernel module.

to switch the side button you need:
    Option     "Button2" "3"  # make side-switch a right button

---

### Post by Johi on 2008-04-20
WUHU thx Wombat ^^
The stylus works finer than in Windoof =)
I will now rebuild the kernel modul to enable the eraser and the right mous button.
But i have 1 Question. The TX2000 has a Touchscreen and a stylus (Touchscreen = you can work with your finger on the screen or with anythink else) I want to use the stylus but not the touchscreen. Becouse when I draw something in gimp with the stylus and I leave my hand on the screen, the courser goes to that point where my hand is. In Vista i can disable this touchscreen and work only with the Stylus. Is this in Ubuntu also possible?

sorry for bad english ^^"

---

### Post by Johi on 2008-04-20
I rebuild the kernel modules to enable the eraser. Now the stylus works but it is not calibrated qq
Same problem qq
i have removed the TopX, TopY, BottomX, and BottomY lines. In the old version (with no eraser) it has worked fine but now it doesnt. why?

---

### Post by TorchlightJay on 2008-04-21
hey i went through the motions and have no eraser still, just the first two. I do not know if I reset the kernel properly? How do I do that? I went ahead and removed wacom.ko and uninstalled linuxwacom and what not, no dice. Any ideas?

---

### Post by TomtheWombat on 2008-04-21
> **TorchlightJay said:**
> hey i went through the motions and have no eraser still, just the first two. I do not know if I reset the kernel properly? How do I do that? I went ahead and removed wacom.ko and uninstalled linuxwacom and what not, no dice. Any ideas?

You shouldn't have to remove linuxwacom.  You only have to replace the kernel module.  Do your stylus and touch screen work?

If so, I would double check that you have all three entries in the xorg.conf and all three devices in the ServerLayout section.

---

### Post by TorchlightJay on 2008-04-21
Ya, my stylus and touchscreen work just fine. What can I test my eraser on? Maybe that will help see if I have it proper. My entries in xorg look fine.

---

### Post by ACLBandit on 2008-04-23
My touchscreen doesn't work after following your guide, but that's a good thing-- I like the stylus and hate the touchscreen. Also, I'm VERY glad to have right-click. Thanks, wombat. 

Now all I need is eraser-- should it be working after following your guide?

---

### Post by HPLinux on 2008-04-24
Hey guys, sounds like you've been making great progress on the 'Linuxification' of the HP TX2000Z ;) Well done!
I'm seriously considering getting one soon & I'm even more encouraged by your success!
So what features are still lost in the conversion? Can you compile a list of what none of you have got working yet?
Thanks for your achievements so far ... I look forward to benefiting & hopefully helping out too soon!

---

### Post by CWasko36 on 2008-04-27
Tom, thanks for your work on the Tx2000.  I just followed the instructions for the Wacom access.  After rebooting I tried using the pen.  I notice that the calibration is very off and it doesn't seem to be consistently off (sometimes it is higher than the pen, sometimes it is very far to the right).  This makes me think that it isn't a simple problem with the calibration.  Any ideas?

---

### Post by TomtheWombat on 2008-04-27
I edited my post to make some changes to the devices in the xorg.conf file.  These point to generic devices that everyone in a debian-based system should have (for now anyway.)  If your xorg.conf is pointing to the wrong devices, then the mouse driver will load up the devices and things will act very funky.  The calibration should be close enough without running a script.

If you delete /usr/local/bin/xsetwacom, then the original xsetwacom included in ubuntu will work.  Then you can change your calibration and settings on the fly!

---

### Post by CWasko36 on 2008-04-27
*Doh* I was editing my Xorg incorrectly (just adding everthing to the end).  Got it worked out and used your new scripts.  

Works beautifully now!  the only thing missing for me is screen rotation which I should work on.

---

### Post by TomtheWombat on 2008-04-27
I am using vista right now, but I can give you a short tutorial on setting up screen rotation and the command line commands to do it.  Unfortunately there don't seem to be any scripts available that you can tie to the hotkey.

I know there is a new patch in debian testing that uses the lid switch notification to flop the screen.  We won't see that until the next Ubuntu release or later, though.

---

### Post by TomtheWombat on 2008-04-27
You will need to delete the xsetwacom that my script installed.  I do this in the latest version of my post but you may want to run this command just in case:

```
sudo rm /usr/local/bin/xsetwacom
```

Then restart your terminal.  The command 'xsetwacom list dev' should show all your devices now.

If you are using Nvidia's restricted drivers, then you need to add the Option "RandRRotation" to the Screen section of your Xorg.conf

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "NoLogo" "True"
    Option         "RandRRotation"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
EndSection
```

Now at the command line to rotate the screen use

```
xrandr -o left
xrandr -o right
xrandr -o normal
xrandr -o inverted
```

In order to rotate the stylus use

```
xsetwacom set "TabletPCStylus" Rotate CW
xsetwacom set "TabletPCStylus2" Rotate CW
xsetwacom set "TabletPCStylus3" Rotate CW
```

The CW option matches with 'right,' option CCW for 'left,' option NONE for 'normal,' option HALF for 'inverted.'

---

### Post by TomtheWombat on 2008-04-27
There is a Firefox extension called [Grab and Drag]("https://addons.mozilla.org/en-US/firefox/addon/1250") that is very useful for implementing 'flick' scrolling.

I also noticed that when I use the touch screen, the device issues a mouse down command before moving the cursor.  Therefore whenever you tap the screen it will click and drag to the new position.  Does anyone else have this issue?

---

### Post by CWasko36 on 2008-04-29
> **TomtheWombat said:**
> There is a Firefox extension called [Grab and Drag]("https://addons.mozilla.org/en-US/firefox/addon/1250") that is very useful for implementing 'flick' scrolling.

I also noticed that when I use the touch screen, the device issues a mouse down command before moving the cursor.  Therefore whenever you tap the screen it will click and drag to the new position.  Does anyone else have this issue?

I don't notice that issue with my cursor.

I was able to get the screen rotation working perfectly.  I added two launch buttons on my status bar to rotate the screen and it works pretty well.

---

### Post by vinland029 on 2008-05-01
what abt the bluetooth module? i having trouble with my tx2000 and just like to findout whether any of u have solved it yet. in the other thread they have got the lightscribe working too. anyway moderator can u merge both threads? hereis link:[http://ubuntuforums.org/showthread.php?t=686363]("http://ubuntuforums.org/showthread.php?t=686363")

---

### Post by ACLBandit on 2008-05-02
I've finally got this nifty screenflipping set up with scripts that I can run with a single click. Very Nice! 

All I need is the eraser. Following your steps, Wombat, it's still not there. Not that it's *that* relevant, but I'd still like it to work. Any tips or suggestions?


And about the bluetooth, I'm sorry-- I opted out there since I have a USB Bluetooth adapter

---

### Post by maggotroot on 2008-05-02
Any ideas on how to calibrate touchscreen and wacom separetly? Because my wacom calibrated pretty accurate, but touchscreen is not))

---

### Post by paulo_raca on 2008-05-03
Thanks, guys!
I've finally been able to have my machine to work!

I just have one major issue: although the touch screen does work, when I release it, the cursor moves to the bottom-right corner of the screen.

Is that "normal"?

---

### Post by HPLinux on 2008-05-05
Still no list of what works & what doesn't yet, guys?

---

### Post by teras on 2008-05-07
I think practically everything works now, although some still with issues.

1) touch screen is not calibrated. Seems like sending movement events, instead of giving positional.

2) The mute button works, but it doesn't change color

3) fingerprint works, but there is no proper integration

4) Some buttons still do not provide usable events

---

### Post by TorchlightJay on 2008-05-07
I am glad that we've all figured this out. A month ago I was about ready to toss this thing out the window. Now, for the most part, it works as it should. There are only a few minor tweaks like the screen rotation and what not that I wish were better but I can live with it.

---

### Post by HPLinux on 2008-05-07
Thanks for the summary, Teras!

Let's try to keep an up-to-date list of what still needs more work.
Is there a central place to find the procedures developed so far, or is it just in the various posts here?

Keep up the excellent work, guys! :)

---

### Post by pAt84 on 2008-05-08
Well, you guys have hibernation working? That is not working on my tx2000z so far but I am still running 7.10.

Pat

---

### Post by mirosol on 2008-05-08
Hi.

I followed the guide on stylus/touchscreen, but nothing.. My machine is tx2020eo, but hardware should be the same.

About that mute-button.. It prevented all of the sound to get out.. I found a fix for it.

Do this:

```
gksu gedit /etc/modprobe.d/alsa-base
```

Add this to be the last line in alsa-base:

```
options snd-hda-intel model=hp
```

That worked for me.

---

### Post by ACLBandit on 2008-05-08
> **TorchlightJay said:**
> I am glad that we've all figured this out. A month ago I was about ready to toss this thing out the window. Now, for the most part, it works as it should. There are only a few minor tweaks like the screen rotation and what not that I wish were better but I can live with it.

I've got four scripts set up to do this, I keep links to each one with an icon that points to which direction the screen will be after clicking it.

To rotate it to the right: 
```
xrandr -o right
xsetwacom set "TabletPCStylus" Rotate CW

```
And to rotate left:
```

xrandr -o left
xsetwacom set "TabletPCStylus" Rotate CCW

```
To flip the screen upside-down:
```

xrandr -o inverted
xsetwacom set "TabletPCStylus" Rotate HALF

```
And to move it back upright:
```

xrandr -o normal
xsetwacom set "TabletPCStylus" Rotate NONE

```

and about that hibernation-- yeah, it *kinda* works. If you tell it to   hibernate and then wait until the mute button turns red, you can turn it off manually and then it will *usually* come back where you left it. However, since this is likely bad for the computer, I stopped doing this.

Also, if anyone can tell me how to get the eraser working, that would be great.

And that calibration script, even though it brings up the little crosshair boxes, doesn't seem to do anything-- could I perhaps be doing something incorrectly?

---

### Post by sjones411 on 2008-05-09
> **ACLBandit said:**
> I've got four scripts set up to do this, I keep links to each one with an icon that points to which direction the screen will be after clicking it.

To rotate it to the right: 
```
xrandr -o right
xsetwacom set "TabletPCStylus" Rotate CW

```
And to rotate left:
```

xrandr -o left
xsetwacom set "TabletPCStylus" Rotate CCW

```
To flip the screen upside-down:
```

xrandr -o inverted
xsetwacom set "TabletPCStylus" Rotate HALF

```
And to move it back upright:
```

xrandr -o normal
xsetwacom set "TabletPCStylus" Rotate NONE

```

and about that hibernation-- yeah, it *kinda* works. If you tell it to   hibernate and then wait until the mute button turns red, you can turn it off manually and then it will *usually* come back where you left it. However, since this is likely bad for the computer, I stopped doing this.

Also, if anyone can tell me how to get the eraser working, that would be great.

And that calibration script, even though it brings up the little crosshair boxes, doesn't seem to do anything-- could I perhaps be doing something incorrectly?

I do not actually own a TX2000z right now, but I'm going to be buying one over the weekend (and using all of the amazing information on this thread as well!).  However, I do own an old HP TC1100 tablet.  I found this article on Linuxquestions.org to be very helpful in setting up the various features of the tablet.

[http://wiki.linuxquestions.org/wiki/Tc1100](http://wiki.linuxquestions.org/wiki/Tc1100)

Of course, why am I mentioning it here in this tx2000z thread?  Well, a slew of the information there is not system specific, such as getting an on screen keyboard working at login.  In particular, the section on screen rotation was helpful, and produced this script:

```
#!/usr/bin/env bash

IFS=$'\n'
DEVS=`xsetwacom list dev | \
   sed -e 's/ *$//g' -e 's/\(.*\) .*/\1/g' -e 's/ *$//g'`
ROTATION=`xrandr --verbose --query | \
   grep 'default connected' | \
   sed -e 's/^.*(.*) \(.*\) (.*).*$/\1/'`

# Rotate all detected wacom devices to the given direction.
function rotate_devices()
{
   for DEV in $DEVS; do
      xsetwacom set $DEV rotate $1
   done
}

if [[ ! $ROTATION == "normal" ]]; then
   xrandr -o normal
   rotate_devices none
else
   xrandr -o left
   rotate_devices ccw
fi
exit 0

```

Using this script, you can bind it to one particular button or icon, and have it switch between normal and counterclockwise orientations.  I'm sure with a little tweaking someone could get it to do the TX2000z's method of rotating around to all 4 positions.  Anyways, I hope that the link and the script help someone out.

EDIT: I just realize, you'd probably have to update rotate_devices ccw to 
xsetwacom set "TabletPCStylus" Rotate CCW for this script to work.

---

### Post by ACLBandit on 2008-05-10
> **sjones411 said:**
> I do not actually own a TX2000z right now, but I'm going to be buying one over the weekend (and using all of the amazing information on this thread as well!).  However, I do own an old HP TC1100 tablet.  I found this article on Linuxquestions.org to be very helpful in setting up the various features of the tablet.

[http://wiki.linuxquestions.org/wiki/Tc1100](http://wiki.linuxquestions.org/wiki/Tc1100)

Wicked! Not only is the script much-appreciated, but the keyboard that's now on my login makes me very happy.

Also, my touchscreen seems to have finally, randomly started to work-- but that's a feature I *don't* like... How do I turn off the touchscreen completely and still leave the stylus-based touching on?

---

### Post by ir0nman on 2008-05-10
Anyone figure out a way to detect the screen being rotated yet, so that we can make the screen auto rotate when we flip it? I know they do this on the x60 and x61 thinkpads, was hoping we could do it on these too, though I don't know enough linux to find the inputs myself. if anyone wants to help and explain things to me, I'd love to help work on it.
-Rick

---

### Post by tempo500 on 2008-05-11
hi, so i got one of my own... tx2140eg. i completed your guide on hardy in 5 minutes and everything was running. but i had to switch to gutsy again cause autodesks maya had a minor redraw problem wich disapeared in gutsy. just gutsy wont compile the new wacom driver. but i used the software kernelcheck it upgraded it to 6.25. wacom compile, nvidia compile, ndiswrapper works. alsa... i dont have a clue...so besides the sound... i am using a really fast zbrush under wine. maya is running so far very nice.
i calibrated the stylus pen seperatly from the finger input. works very nice! phil

check the cursor coordinate: xidump TabletPCStylus


xsetwacom set TabletPCStylus TopY 130
xsetwacom set TabletPCStylus TopX 220
xsetwacom set TabletPCStylus BottomY 16300
xsetwacom set TabletPCStylus BottomX 26300

xsetwacom set TabletPCStylus2 TopY 01150
xsetwacom set TabletPCStylus2 TopX 01429
xsetwacom set TabletPCStylus2 BottomY 15300
xsetwacom set TabletPCStylus2 BottomX 25300

xrandr doesnt work for me...

 xrandr -o inverted
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  158 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

---

### Post by mirosol on 2008-05-11
hi again. I'm still out of luck with wacom... My machine is tx2020eo (which should be same machine, only made for scandinavian countries...), but i think that your tutorial should be suitable for my machine also.. lsusb gives this output about wacom:
Bus 001 Device 006: ID 056a:0093 Wacom Co., Ltd 
...so i think its exactly the same hardware as in tx2000z. 

I've uploaded all logs and confs, so if anyone can tell me what i'm doing wrong, please do. I'm running 64-version of 8.04.

Yours, Miro from Finland

---

### Post by TomtheWombat on 2008-05-11
> xrandr doesnt work for me...

Add the option for RandRRotation to your xorg.conf.

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "NoLogo" "True"
    Option         "RandRRotation"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
EndSection
```

---

### Post by tempo500 on 2008-05-11
hey, i have that in the xorg.conf file...

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation C51 [Geforce 6150 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "UseFBDev" "true"
    Option         "RandRRotation"
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
EndSection
```

---

### Post by TomtheWombat on 2008-05-11
What drive are you using to drive your display?  nvidia? nv?  fbdev?

BTW: THere is a screen roattion patch for the Asus R1F in debian unstable.  I'll work on patching up Ubuntu for the tx2000z with a similar patch when i get a chance later this week or next weekend...

---

### Post by ir0nman on 2008-05-13
If there's anything I can do with the patch, let me know. I assume that your talking about automatic rotation based on the lid sensor or something? Thanks for all your work so far on this laptop it's awesome!
-Rick

---

### Post by ACLBandit on 2008-05-14
I've been having an issue with the touchscreen while trying to take notes for class: as soon as the stylus is lifted, the mouse does a click-jump to wherever my fingers or hand are touching the screen. I hate the touchscreen anyway-- I love my wacom pen, though.

I thought I had figured out how to disable it, but apparently not. Does anyone know how to turn OFF the touchscreen but leave ON the wacom/wacom pen?

---

### Post by TomtheWombat on 2008-05-14
if you install xserver-xorg-dev and reinstall with my instructions then the touch screen will act normally instead of click/drag.  Not sure how to disable it yet.

---

### Post by ACLBandit on 2008-05-14
> **TomtheWombat said:**
> if you install xserver-xorg-dev and reinstall with my instructions then the touch screen will act normally instead of click/drag.  Not sure how to disable it yet.

Yeah, I did that now--it kinda makes some sense now. I still want to turn it off, though, so if anyone figures it out, let me know.

---

### Post by xraytroubadour on 2008-05-17
Hello,

First thanks to all the people on this thread for the info. Installing kubuntu on my new tx2000z was so easier. In fact, reading this thread convinced me of buying it in the first place.

So, I think I am at the same point as most of you: everything works almost perfect. One thing I was wondering: am I the only one who seem to suffer from this bug:

[http://sourceforge.net/tracker/index.php?func=detail&aid=1891713&group_id=69596&atid=525127]("http://sourceforge.net/tracker/index.php?func=detail&aid=1891713&group_id=69596&atid=525127")

On this bug tracker site, they seem to say that the problem is solved, but it definitely is not for me. Strokes in xournal look a bit blocky, and typing "xidump TabletPCStylus" shows coordinates only at the resolution of the screen.

Now, what is really weird is that I am pretty sure I didn't have this problem a few days ago. It seems to have started exactly when I recompiled the wacom driver with the xserver-xorg-dev package installed, since I also had this click-jump issue with the touchscreen. Un-installing xserver-xorg-dev and recompiling didn't revert to the previous situation though.

Thanks for any input on that issue!

Oh, and by the way, I could disable the touchscreen just by putting the Sendcoreevents option to "false" in my xorg.conf...

---

### Post by tempo500 on 2008-05-17
hi,
i am running the nvidia drivers... thanks for your help

```
Section "Device"
    Identifier     "nVidia Corporation C51 [Geforce 6150 Go]"
    Driver         "nvidia"
EndSection
```

---

### Post by M42 on 2008-05-19
> **xraytroubadour said:**
> 
On this bug tracker site, they seem to say that the problem is solved, but it definitely is not for me. Strokes in xournal look a bit blocky, and typing "xidump TabletPCStylus" shows coordinates only at the resolution of the screen.

Oh, and by the way, I could disable the touchscreen just by putting the Sendcoreevents option to "false" in my xorg.conf...

Hello xraytroubadour,  
I'm getting the coordinates for x > 25k and y > 15k based on the output from xidump TabletPCStylus but I can see some blocking in xjournal if I look closely using the fine pen.  Wish I could be more help.  

Which SendCoreEvents did you turn off in xorg.conf to turn off the touchscreen?

---

### Post by xraytroubadour on 2008-05-19
> **M42 said:**
> Hello xraytroubadour,  
I'm getting the coordinates for x > 25k and y > 15k based on the output from xidump TabletPCStylus but I can see some blocking in xjournal if I look closely using the fine pen.  Wish I could be more help.

Which SendCoreEvents did you turn off in xorg.conf to turn off the touchscreen?

Yeah, something is not normal with my setup - I may very well have tweaked too many things - especially in the xorg.conf. 

The "SendCoreEvent" option I set to false is the one for TabletPCStlyus2. I must warn you that it may not be the solution because the touchscreen randomly started to work again in some occasions. I need to check how this is correlated to suspending to ram. I am so happy I can suspend my laptop (I never was able to do it on the one I had before) that I may be overdoing it a little...

Oh, and just in case someone is interested, I wrote a small script to rotate the screen, that I placed in my ~/bin:

```
#!/bin/bash

if [ -z `xrandr | grep -o "800x1280"` ]; then
   # Landscape mode - change to portrait
   xrandr -o right
   xsetwacom set "TabletPCStylus" Rotate CW
   xsetwacom set "TabletPCStylus2" Rotate CW
   xsetwacom set "TabletPCStylus3" Rotate CW
else
   # Portrait mode - change to landscape
   xrandr -o normal
   xsetwacom set "TabletPCStylus" Rotate NONE
   xsetwacom set "TabletPCStylus2" Rotate NONE
   xsetwacom set "TabletPCStylus3" Rotate NONE
fi
```
(some may prefer CCW and left instead of CW and right. I am left-handed and the pen string is in the way when I rotate it the other way)

I then configured KDE to execute the script when I hit the button with the little arrow going in a circle on the bottom right corner of the screen (I don't know what it is supposed to mean).

---

### Post by xraytroubadour on 2008-05-19
Hello again,

Ok, I barely understand what I just did, but for now my low-resolution problem seems to be solved. Even though I may be the only one having the problem, I'll document it here now (I hate seing threads that finish with "Hey I found the solution", and then nothing).

Doing a diff on the config.log in the linuxwacom-0.7.9.11 directory for the cases with and without xserver-xorg-dev showed a "quirk" called "tablet-rescale". In the file config.status (that was generated with "./configure --enable-wacom" and xserver-xorg-dev installed), I looked for the lines that contained TABLET_SCALING. There were two of those, and I just discarded them. Then followed the usual compilation. I guess me believing that removing xserver-xorg-dev did not solve the problem was just caused by forgetting to "make clean"... I still wanted to have xserver-xorg-dev installed since it solved the jump/click issue.

Anyway, as I said I have no clue what this all mean. I'll also stop here since I am probably mostly talking to myself. (I wonder why nobody else got this issue, though...)

---

### Post by correaa on 2008-05-20
Regarding the issue of disabling the touchscreen (while keeping stylus). 

I don't know exactly what the options in xorg.conf do, but the following lines disables the touchscreen. I guess the key part is the last section but I don't know way. Maybe this gives a clue to someone else on activating the eraser tip for certain programs (e.g. gimp or xournal). If you have any improvement please pots it:

disabled touchscreen:
---------------------

Section "InputDevice"
    Identifier "TabletPCStylus"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
    Option "Type" "stylus"
    Option "SendCoreEvents" "true"	
    Option "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
    Option "Button2" "3"  # make side-switch a right button
    #  Option "TopX" "225"
    # Option "TopY" "122"
    # Option "BottomX" "26365"
    # Option "BottomY" "16488"
EndSection

Section "InputDevice"
    Identifier "TabletPCStylus2"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
    Option "Type" "cursor"
    Option "SendCoreEvents" "true"
    Option "Device" "/dev/input/wacom"
EndSection

Section "InputDevice"
    Identifier     "TabletPCStylus3"
    Driver         "wacom"
    Option         "Button1"      "1"	#this line is important
    Option         "Button2"      "1"	#this line is important
    Option         "ForceDevice" "ISDV4"
    Option         "Type" "eraser"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "touch"
    Option        "Device"        "/dev/input/by-id/usb-Tablet_ISD-V4-mouse"
    Option        "Type"          "touch"
    Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
    Option "SendCoreEvents" "true"
#    Option "TopX" "225"
#    Option "TopY" "122"
#    Option "BottomX" "26365"
#    Option "BottomY" "16488"
EndSection

---

### Post by lordoflima on 2008-05-22
This is my quickly typed bash script for rotating the screen. Just put it into any file, set chmod +x and set a k-menu-entry with the rotation-icon (next to DVD) as hotkey. Works fine, but I'd liked the other button more, for consistency.



```
#!/bin/bash

if [ "`cat /tmp/screen_rotation 2>/dev/null`" = "right" ]; then
        rm /tmp/screen_rotation
        XRAND="normal"
        SETWACOM="NONE"
        ROTATED="1"
fi;

if [ "`cat /tmp/screen_rotation 2>/dev/null`" = "inverted" ] && [ "$ROTATED" != "1" ]; then
        echo "right" > /tmp/screen_rotation
        XRAND="right"
        SETWACOM="CW"
        ROTATED="1"
fi;

if [ "`cat /tmp/screen_rotation 2>/dev/null`" = "left" ] && [ "$ROTATED" != "1" ]; then
        echo "inverted" > /tmp/screen_rotation
        XRAND="inverted"
        SETWACOM="HALF"
        ROTATED="1"
fi;

if [ "`cat /tmp/screen_rotation 2>/dev/null`" = "" ] && [ "$ROTATED" != "1" ]; then
        echo "left" > /tmp/screen_rotation
        XRAND="left"
        SETWACOM="CCW"
        ROTATED="1"
fi;

if [ "$ROTATED" = "1" ]; then
        xrandr -o $XRAND
        xsetwacom set "TabletPCStylus" Rotate $SETWACOM
        xsetwacom set "TabletPCStylus2" Rotate $SETWACOM
        xsetwacom set "TabletPCStylus3" Rotate $SETWACOM
fi;


```



Does anybody got the standby working?

---

### Post by ACLBandit on 2008-05-23
Correa, no go-- the .conf doesn't kill m touch5creen:(

However, Lordoflima, your script is my new Best Friend.

---

### Post by correaa on 2008-05-23
it worked for a while for me, and then the stupid uncalibrated touchscreen came back. Sorry.

> **ACLBandit said:**
> Correa, no go-- the .conf doesn't kill m touch5creen:(

However, Lordoflima, your script is my new Best Friend.

---

### Post by theverant on 2008-05-24
Thanks for all the hard work guys.  I just bought this lappy today and have most everything working.  I think I killed xorg, though.  Ubuntu now starts in low res mode - ew!  Any help in fixing would be very much appreciated.  

](*,)

Best,
Theverant

---

### Post by M42 on 2008-05-24
I had this happen when I was adjusting some of the screen parameters in the kde's sytem setting.  If you look at xorg.conf you will probably find some line that have some low res parameters, i.e. 640X480, I just edited those out and when I restart X it was back to high res mode.  It is probably a good idea to keep a copy of a working xorg.conf just in case your changes don't work.

Good luck.

---

### Post by pAt84 on 2008-05-24
In case somebody uses avant window navigator (AWN), make sure you place a 'killall avant-window-navigator' in front of the rotation and a 'avant-window-navigator' after it. This will make it restart everytime and the icons will be right aligned again (didnt work for me). Also, you might wanne add a 'sleep 2' between the commands to let the system wait two seconds before it rotates the screen and starts AWN. I noticed that the x-server can get incredibly slow if you dont do that.

One question guys, which might seem stupid: How do I in Ubuntu (gnome) connect my rotation-script with the button on the tablet pc?

Pat

---

### Post by sjones411 on 2008-05-24
I'm having trouble getting the wacom tablet features working.  I followed all the instructions to the T, but when I typed in sudo rmmod wacom I get:

ERROR: Module wacom does not exist in /proc/modules

You guys have any suggestions?  By the way, if you read this ACLBandit, how did you get the pen working without the touch screen?  I do a lot of graphic art stuff, so I don't want my palm to screw up my stuff.  Anyways, thanks in advance!

---

### Post by pAt84 on 2008-05-25
Just go on with the guide and ignore the error.

Pat

---

### Post by tempo500 on 2008-05-25
looks like this applies to gutsy... my harddrive was parking all the time which can reduce the lifetime of your hd....
[http://ubuntuforums.org/showthread.php?t=795327]("http://ubuntuforums.org/showthread.php?t=795327")

---

### Post by sjones411 on 2008-05-25
> **pAt84 said:**
> Just go on with the guide and ignore the error.

Pat

I did continued on with the guide, and even after fixing my Xorg I still don't have tablet or touchscreen support.  I'm not sure what I'm doing wrong.  Any suggestions?

My Xorg: [http://www.box.net/shared/67z1jgtss4](http://www.box.net/shared/67z1jgtss4)

---

### Post by pAt84 on 2008-05-25
Apart from that error nothing bad happened? Are you on Hardy? Which specific model do you have? Please do a 'lsusb' on the console.

Also I had the kernel sources and linux-headers downloaded before I ran the guide. But I doubt that will make any difference.

Pat

---

### Post by sjones411 on 2008-05-25
> **pAt84 said:**
> Apart from that error nothing bad happened? Are you on Hardy? Which specific model do you have? Please do a 'lsusb' on the console.

Also I had the kernel sources and linux-headers downloaded before I ran the guide. But I doubt that will make any difference.

Pat


```
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 056a:0093 Wacom Co., Ltd 
Bus 001 Device 005: ID 08ff:1600 AuthenTec, Inc. 
Bus 001 Device 004: ID 04f2:b015 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 0000:0000  
```

There's my lsusb.  I'm running on the latest version of 8.04.  I'm on the TX2000 CTO modle which was purchased last week.  Thanks for all the help Pat!

---

### Post by pAt84 on 2008-05-25
Well yeah, thing is that I myself do not really know what I am doing. ;)

Did you actually run the guide on a fresh installation of hardy? That is what I did and it worked like a charm. I also got the same error telling me that the module is not there.

Edit: And as for you lsusb? What is going on there? Here is mine:
```

Bus 002 Device 004: ID 056a:0093 Wacom Co., Ltd 
Bus 002 Device 003: ID 064e:a110 Suyin Corp. 
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 001 Device 001: ID 0000:0000 

```

The last one is my mouse. Your AuthenTec-thingy is probably the fingerprint reader. I don't have one for some reason. But what is the general 'Hewlett-Packard' and 'Chicony Electronics Co., Ltd'? Mouse? Keyboard? While your wacom lies on Bus 1 mine lies on Bus 2. Someone else with the tx2000z should print his/her lsusb output. Maybe your issue likes there although I doubt it. 

Pat

---

### Post by sjones411 on 2008-05-25
> **pAt84 said:**
> Well yeah, thing is that I myself do not really know what I am doing. ;)

Did you actually run the guide on a fresh installation of hardy? That is what I did and it worked like a charm. I also got the same error telling me that the module is not there.

Edit: And as for you lsusb? What is going on there? Here is mine:
```

Bus 002 Device 004: ID 056a:0093 Wacom Co., Ltd 
Bus 002 Device 003: ID 064e:a110 Suyin Corp. 
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 001 Device 001: ID 0000:0000 

```

The last one is my mouse. Your AuthenTec-thingy is probably the fingerprint reader. I don't have one for some reason. But what is the general 'Hewlett-Packard' and 'Chicony Electronics Co., Ltd'? Mouse? Keyboard? While your wacom lies on Bus 1 mine lies on Bus 2. Someone else with the tx2000z should print his/her lsusb output. Maybe your issue likes there although I doubt it. 

Pat

Hmm...  Maybe my Xorg isn't pointing to the right device then, and the driver's installed fine?  Sigh...  It looks like HP likes to fiddle with their hardware then, so most of these older tutorials won't exactly work for me.

---

### Post by ACLBandit on 2008-05-26
So today's updates killed my wacom, thus making me quite sad. I tried following the tutorial on the new kernel, but to no avail (even changing the kernel number from 16 to 17, of course). 

I also tried booting back in 16 and re-doing the wacom install, but once again was met with quite a bit of nothing.

Any insight, guys?

---

### Post by sjones411 on 2008-05-26
> **ACLBandit said:**
> So today's updates killed my wacom, thus making me quite sad. I tried following the tutorial on the new kernel, but to no avail (even changing the kernel number from 16 to 17, of course). 

I also tried booting back in 16 and re-doing the wacom install, but once again was met with quite a bit of nothing.

Any insight, guys?

Ah, it's good to know that I'm not the only one who's been having trouble ._.;;  I hope that someone figures out what the issue is soon.

---

### Post by M42 on 2008-05-26
> **ACLBandit said:**
> So today's updates killed my wacom, thus making me quite sad. I tried following the tutorial on the new kernel, but to no avail (even changing the kernel number from 16 to 17, of course). 

I also tried booting back in 16 and re-doing the wacom install, but once again was met with quite a bit of nothing.

Any insight, guys?

I just downloaded the updates for today.  Looks like one of the updates is a new nvidia-glx-new driver.  My guess is it was not the updated kernel since you still have the problem when booting into the old kernel but it is the new nvidia driver.  If you can find the old driver you might give re-installing the old driver and see if that corrects your problem.  I'm not going to install the upgrades for a few days or until we figure out what caused the problem.

Good luck.

---

### Post by pAt84 on 2008-05-26
Is it only me or is the CPU stuck at 800 Mhz (or whatever your lowest level is) for everyone when running on battery?

Pat

---

### Post by ACLBandit on 2008-05-27
Touchscreen is up-and-running here on the -17 kernel. 

The surest way to get it running is to remove the linuxwacom folder from your  home folder, and also get rid of the patch file and the linuxwacom*.tar.bz2 from your home folder. 

Then run through Wombat's tutorial on page 3 in full, changing ONLY the part where it mentions the -16 kernel to -17.

I think that I was trying to double-patch the file or something unknowingly, which is likely the reason I couldn't recompile correctly.

---

### Post by DesiDishoom on 2008-05-27
hey guys, i'm relatively new to the ubuntu world, but i've managed to get it running successfully with full functionality on two other machines at home. but, as hard as i may try, when i try to get the wireless working on this HP tx2000z tablet, it keeps freezing up a few minutes after the network gets connected. It is never the same time after connection, and it's sometimes during the connection stage. 

I am positive the wireless card is the culprit because i can install as many other drivers as i want, and as long as i don't get the wireless up and running, and everything runs great. But as i said, once i use ndiswrapper to install the dell drivers (like was mentioned on page 2 of this thread) it freezes every time i boot up. 

I have the Broadcom BCM4310 (rev 01) card. I am using the updated version (-17) of hardy 8.04, although the -16 kernel did the same thing...

Any help would be AWESOME because vista is annoying the crap out of me, and getting over this roadblock would absolutely make my summer.

---

### Post by unterfuhrer on 2008-05-28
can anyone explain howto get the calibrationtool to work, i can figure it out. I have tested many times and all a get in the terminal is:

```
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device 'Synaptics'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'
Use of uninitialized value in system at ./calibrate.pl line 35.
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'
Use of uninitialized value in system at ./calibrate.pl line 36.
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'
Use of uninitialized value in concatenation (.) or string at ./calibrate.pl line 40.
Use of uninitialized value in concatenation (.) or string at ./calibrate.pl line 40.
Use of uninitialized value in multiplication (*) at ./calibrate.pl line 112.
Use of uninitialized value in multiplication (*) at ./calibrate.pl line 113.
Use of uninitialized value in multiplication (*) at ./calibrate.pl line 115.
Use of uninitialized value in multiplication (*) at ./calibrate.pl line 116.
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'
```

does you know whats wrong ? The touchpad works but it is wrong calibrated.

Thanks

---

### Post by sjones411 on 2008-05-29
You guys have been so helpful with getting my Tx2000z running under Ubuntu that I'd like to give something back.  I know how useful the buttons built into the screen can be for graphics design people like myself, so here's a short tutorial I made for getting the DVD and QuickPlay buttons to do something useful.  So without further adue...

**Keybinding guide for the HP Tx2000z Tablet PC.**

First, we're going to use XBindKeys to bind different applications or scripts to the key.  So we'll need to download that.  We'll also download an on screen keyboard called xvkbd, which we'll use later.

```
 sudo apt-get install xbindkeys xvkbd 
```

Now that we've got that taken care of, we'll need to set up a confituration script.

```
 gedit ~/.xbindkeysrc 
```

Xbindkeys works pretty easily.  All you have to do is type in the name of the program in quotes, and then the key you'd like to bind it to on the next line.

```

"cellwriter"
 c:0xed
"xvkbd -text "\Cz""
 c:0xcd

```

Alright, now save the file.  Before we go any further we need to test xbindkeys out.  Open up a terminal and type:

```
 xbindkeys -v 
```

Now, try pressing the DVD button (0xed) or the QuickPlay button (0xcd), if everything went right, the program or script you assigned to them should work.  In the above script, the DVD button will launch the great handwriting to text program CellWriter, and the Quick Play button will send the key commands for Ctrl-Z to the computer, great for us graphic artists.  However, any terminal command that can be placed within the quotes and should work.  I highly recommend using the [rotate script written by lordoflima]("http://ubuntuforums.org/showpost.php?p=5020078&postcount=88").

Now then, we just have to get get xbindkeys to launch at startup.  To do this, go to the menu up at the top and hit System --> Preferances --> Session.  Next, click the Add button.  In the Name Box type "xbindkeys", and then for the Command type "xbindkeys" again.

Tada!  That's all there is to it... for the first two keys.  Unfortunately, the rotate key and the mobility system key are not recognized by Ubuntu's kernel by default, and will take some more work to get functioning properly.  I'll post the second part of my tutorial once I get it working myself.  Hope you guys find this walk through useful!

---

### Post by sjones411 on 2008-06-01
I know that the touch screen is a strange issue, and for the most part mine calibrated well.  If you poke the center of the screen it works perfectly, but the further away I get from the center the more off it becomes.  I gets so bad that I cannot even click on anything in the last inch of my display.  This picture shows the area of which I can click in.  To take it, I dragged my finger from the top left to the bottom right.  Is anyone else having such strange issues with their tablet?  Thanks in advance.

[http://img175.imageshack.us/img175/5152/screenshotqo9.png]("http://img175.imageshack.us/img175/5152/screenshotqo9.png")

---

### Post by ACLBandit on 2008-06-02
Jones, if it's just the touchscreen you're talking about, then yes, I am most certainly having issues. I can't calibrate it, I don't want it to be there anyway, and it just generally sucks.

At least the wacom pen is pretty well-calibrated, otherwise I'd be screwed.

---

### Post by DesiDishoom on 2008-06-02
This thread is absolutely amazing. I have everything working for the most part, except for the touchscreen (without the stylus) is WAY off, and never consistently so either...

BUT i have a more pressing issue:

is anyone else having issues with the display not turning back on once it's turned off? This issue is really crippling because i can't put it into suspend/hibernate or even let it sit there until the display turns off, or else it won't turn back on and i have to do a hard reboot. 
this almost seems like a hardware thing than something with ubuntu, but any ideas would be greatly appreciated.

---

### Post by pAt84 on 2008-06-02
Yep, that is true for me as well. It also happens when you close the lid for a while and open it again: The screen won't turn back on. Have to restart X then.

Another issue is that my CPU is locked at 800 Mhz while running on battery. I'd appriciate if anyone could comfirm that.

Pat

---

### Post by DesiDishoom on 2008-06-02
yeah, ditto on the 800 Mhz lock on battery...no clue how to change that. tried changing the default cpu scaling to 'performance', but that didn't do anything either.

it really hurts especially when since the desktop cube, expo, and other compiz-fusion stuff doesn't run very smoothly...

---

### Post by sjones411 on 2008-06-02
> **DesiDishoom said:**
> BUT i have a more pressing issue:

is anyone else having issues with the display not turning back on once it's turned off? This issue is really crippling because i can't put it into suspend/hibernate or even let it sit there until the display turns off, or else it won't turn back on and i have to do a hard reboot. 
this almost seems like a hardware thing than something with ubuntu, but any ideas would be greatly appreciated.

I have the same issues where if I close my laptop's lid, I don't know how to automate this, but if you press Ctrl+Alt+F1, then press Ctrl+Alt+F7, and maybe move the mouse around a little, then your screen should come back.  It takes a bit of fiddling some times, but keep trying and it should work.

---

### Post by DesiDishoom on 2008-06-04
uh oh, just got the update notification that the new kernel is available. i'm going to try and update it, and follow the instructions on page 3, changing only the -16 to -18, and i'll post whether i can get the wacom up after the kernel update!

---

### Post by ACLBandit on 2008-06-04
The new updates killed my wireless card-- because it's apparently supported now. Lol.

If it happens to do the same to you, *and your wireless WAS previously working*, simply open the restricted drivers manager and turn off the new entry, "wl." 

Reboot, and all is well. Only thing left is to run the touchscreen tutorial... again...

EDIT 4 mins later: Not even a problem :) Wacom runs again on the new -18 kernel. All you have to do, once again, is run the tutorial.

If the files are already patched and such, you can just start at the ./configure step while in the linuxwacom folder. If not, or if you're not sure, the best thing to do is just to remove the source files you used previously and start at the beginning.

The only change, of course, is the kernel number-- do this line of the tutorial 
```
 sudo cp src/2.6.24/wacom.ko /lib/modules/2.6.24-16-generic/kernel/drivers/input/tablet/wacom.ko

```

Like THIS instead: 
```
 sudo cp src/2.6.24/wacom.ko /lib/modules/2.6.24-18-generic/kernel/drivers/input/tablet/wacom.ko

```

Good luck! ^_^

---

### Post by DesiDishoom on 2008-06-04
nice dude, props for taking the plunge and getting it all to work! i'm relatively new to ubuntu, so could anyone enlighten me on how often these kernel updates come around? i'm not really looking forward to having to follow that tutorial over and over again too often..,(although i'd assume i'd be able to do it all without the tutorial after the first few times...silver lining maybe?)

---

### Post by ACLBandit on 2008-06-04
I don't seem to remember kernel updates being nearly so frequent before-- but then again, I also haven't had much use for paying attention. I didn't run anything before with... what's it called... "kernel modules," I think? I now have three-- VirtualBox, Cisco VPN, and the wacom thing. Yaay for a high-maintenance note-taking thing for summer classes.

Hardy is a relatively new release. I, having no idea what the updates are based upon (i.e., based on need, based on a release schedule, whatever), wonder if perhaps it will calm down as 8.04 ages a bit.

---

### Post by DesiDishoom on 2008-06-05
nice got mine working too! thanks aclbandit. 

i think it kinda sucks that there isn't a powerful opensource program to mimic OneNote, cause that's really the only thing i miss about Windows...that and being able to log in with my fingerprint. has anyone been able to integrate the fingerprint reader yet?

---

### Post by ACLBandit on 2008-06-05
> **DesiDishoom said:**
> 
i think it kinda sucks that there isn't a powerful opensource program to mimic OneNote, cause that's really the only thing i miss about Windows...that and being able to log in with my fingerprint. has anyone been able to integrate the fingerprint reader yet?

I don't think there is any fingerprint integration yet. :(

However, there is an open-source notetaking app that I like, though it isn't as powerful as OneNote appears to be.

It's called xournal, I think it's in the repositories.  Another one you might want to look into is Jarnal, a java-based program with similar features. Jarnal, though, took up too much memory and caused a laptop overheat when I was running WinXP in a VM at the same time.

So I recommend Xournal. Not as feature-rich, but it might get the job done.

---

### Post by DesiDishoom on 2008-06-05
yea i've tried Xournal...seems more like an alternative to Windows Journal, which like you said, gets the job done. But the biggest upside to OneNote is the ability to print pdf to it and write all over it, print screen clippings to it, and basically just organize nearly all of my life into it haha. But yep, i'll definitely live with booting into Vista when i need that functionality, and using Xournal for the rest.

---

### Post by sjones411 on 2008-06-05
> **DesiDishoom said:**
> yea i've tried Xournal...seems more like an alternative to Windows Journal, which like you said, gets the job done. But the biggest upside to OneNote is the ability to print pdf to it and write all over it, print screen clippings to it, and basically just organize nearly all of my life into it haha. But yep, i'll definitely live with booting into Vista when i need that functionality, and using Xournal for the rest.

I agree, Ubuntu needs a good OneNote clone.  However, if all you're needing is OneNote's Print to PDF feature, then you're in luck.  Ubuntu has a rather nice PDF Printer, and Xournal can easily annotate PDF documents.  For instructions on how to get Print to PDF working, follow this link:

[http://www.arsgeek.com/?p=1720](http://www.arsgeek.com/?p=1720)

Enjoy!

---

### Post by MurDoK on 2008-06-06
> **ACLBandit said:**
> The new updates killed my wireless card-- because it's apparently supported now. Lol.

If it happens to do the same to you, *and your wireless WAS previously working*, simply open the restricted drivers manager and turn off the new entry, "wl." 

Reboot, and all is well. Only thing left is to run the touchscreen tutorial... again...
[...]

Hello. It has also happened to me but in my case the restricted drivers manager doesn't show any new entry named "wl". It only shows the nvidia one.
:confused:

dmesg shows **wlan0: link not ready** when I try to configure it manually.
(**ifconfig wlan1 up** does nothing)

---

### Post by sjones411 on 2008-06-06
> **MurDoK said:**
> Hello. It has also happened to me but in my case the restricted drivers manager doesn't show any new entry named "wl". It only shows the nvidia one.
:confused:

dmesg shows **wlan0: link not ready** when I try to configure it manually.
(**ifconfig wlan1 up** does nothing)

I can't test this for myself since I'm in the process of switching over from Wubi to native Ubuntu, but part of the problem could be which wireless card you have.  ACLBandit and I both have the G/B wireless card, not the B/G/N card.  The new driver may only be for those people who did not upgrade their card to the new N standard.  Once again though, I have no way of testing it right now and it's just speculation. :-\"

---

### Post by MurDoK on 2008-06-06
Well, first of all. It's solved.
Now I don't know if it was caused by the upgrade or because I had been playing with another wifi usb card and patching kernel to inject packets... but with older kernels it didnt work neither.

I solved it into the Network menu. I activated the device there and it worked :confused: strange...

My card is a/b/g/n rev3. I thought all models brought this one!

---

### Post by dimonzub on 2008-06-06
> **DesiDishoom said:**
> 
is anyone else having issues with the display not turning back on once it's turned off? This issue is really crippling because i can't put it into suspend/hibernate or even let it sit there until the display turns off, or else it won't turn back on and i have to do a hard reboot. 
this almost seems like a hardware thing than something with ubuntu, but any ideas would be greatly appreciated.

i had this problem as well and CTRL+ALT+F1 then CTRL+ALT+F7 did not help me as well. i have followed instructions for hibernate on the TC1100 laptop and it worked for me

[http://wiki.linuxquestions.org/wiki/Tc1100#Hibernate_and_suspend_to_RAM]("http://wiki.linuxquestions.org/wiki/Tc1100#Hibernate_and_suspend_to_RAM")

See if it will help you.

---

### Post by MurDoK on 2008-06-08
Hi.
I have not seen anyone complaining about his keypad that is not working (I mean the keypad using Fn key, Fn+U=4, Fn+L=3...).
At least in the spanish layout it doesn't work by default.
Here is the recipe of how I solved it:

Open a terminal, then:
```
xmodmap -pke > .xmodmap
```

It prints the current keymap table that is being used to the file .xmodmap.

Now edit it. The lines I changed were:

```

keycode  79 = KP_Home KP_7
keycode  80 = KP_Up KP_8
keycode  81 = KP_Prior KP_9
keycode  83 = KP_Left KP_4
keycode  84 = KP_Begin KP_5
keycode  85 = KP_Right KP_6
keycode  87 = KP_End KP_1
keycode  88 = KP_Down KP_2
keycode  89 = KP_Next KP_3
keycode  90 = KP_Insert KP_0
```

removing the first alias, so it remains as:

```

keycode  79 = KP_7
keycode  80 = KP_8
keycode  81 = KP_9
keycode  83 = KP_4
keycode  84 = KP_5
keycode  85 = KP_6
keycode  87 = KP_1
keycode  88 = KP_2
keycode  89 = KP_3
keycode  90 = KP_0
```

Finally type:
```
xmodmap .xmodmap
```

And test if it works.

Execute it for all users and before logging in:
```
sudo mv .xmodmap /etc/X11/Xmodmap
```

Note: Your keycodes may differ :confused:
Note2: I don't know the gui method to do it

---

### Post by sjones411 on 2008-06-08
Up until now I've been using Wubi (The Windows Based Ubuntu Installer) for my Ubuntu installation.  However, I want to switch over and use a traditional Ubuntu install.  I've already uninstalled Wubi and then I fired up my Ubuntu install CD.  Once in the Live CD however, I became somewhat confused.  My tx2000z came with one of HP's recovery partitions, and I don't have any experience installing Ubuntu on a machine with 2 existing partitions on it.  And also unfortunately, I want a relatively smell Ubuntu install (roughly 10 GB), and it's automatic partitioner does things by percentages, so when I get near 20GBs the text becomes unreadable.  I did buy the $20 recovery CDs from HP, so should I even be worried about the recovery partition?  What did you guys do for your installs?

---

### Post by Fuzzie 360 on 2008-06-09
> **sjones411 said:**
> Up until now I've been using Wubi (The Windows Based Ubuntu Installer) for my Ubuntu installation.  However, I want to switch over and use a traditional Ubuntu install.  I've already uninstalled Wubi and then I fired up my Ubuntu install CD.  Once in the Live CD however, I became somewhat confused.  My tx2000z came with one of HP's recovery partitions, and I don't have any experience installing Ubuntu on a machine with 2 existing partitions on it.  And also unfortunately, I want a relatively smell Ubuntu install (roughly 10 GB), and it's automatic partitioner does things by percentages, so when I get near 20GBs the text becomes unreadable.  I did buy the $20 recovery CDs from HP, so should I even be worried about the recovery partition?  What did you guys do for your installs?

What I did was I used the vista partition editor and shrunk my main volume some space and left it unallocated. And if the vista editor will not let me shrink any more, I would use partedmagic livecd to edit the partition through gparted and fix the ntfs partition with ntfsfix v2 (any version less will not work). Then I would i use the CD/DVD i burnt and install throught the anaconda installer and I specificly say to "use largest continuous free space" so it doesn't touch my other two partition. Hope that helps.

---

### Post by Fuzzie 360 on 2008-06-09
Sorry for double posting guys, but I found out the solution for those of you who are stuck in 800MHz when on battery!

You guys have been great help to me (even though I'm on Fedora instead of Ubuntu) and now it's time for me to repay you guys :P

All I had to do to fix this CPU scaling problem is to run this:

```
sudo modprobe powernow-k8
sudo modprobe acpi-cpufreq
```

or for fedora users (modprobe link is not present):
```
su -
modprobe powernow-k8
modprobe acpi-cpufreq

```

There you go! CPU scaling goodness on battery.
(I don't know how, I don't know why, but running it at this particular order magically made it work even though i got a resource-is-busy error upon acpi-cpufreq)

To make this permanent, add these lines to /etc/rc.d/rc.local:
```

modprobe powernow-k8
modprobe acpi-cpufreq

```

I'm sorry if there is a need to install some packages because I may have installed some necessary packages while I was frantically working for a solution (although highly unlikely ;)).

-------------------------------------------------------------

Now, I'm going to tell you how to get the fingerprint reader working :D
Just go here and it will explain everything to you:
[http://www.reactivated.net/fprint/wiki/Pam_fprint](http://www.reactivated.net/fprint/wiki/Pam_fprint)

It works fine, however, please note that current support is kinda wonky and chance of reproducibility of your configured fingerprints is very low. I recommend putting 10 copies of your left thumb as your other fingers as a failsafe. Do not get rid of password fallback! Chances are you will get locked out. You need to wait until the fprint project matures.

If you are unable to login or save your fingerprint you might want to change permissions and ownership of your ~/.fprint profile directory

-------------------------------------------------------------

For those of you who wants inking (pen -> text) support, you should install cellwriter! it works really good so far

-------------------------------------------------------------

For those of you who are **not in Ubuntu** and the special buttons (DVD and Quickplay buttons) are not giving a response through xbindkeys, you need to map the keys to a keycode using setkeycodes. Test it out and if it works okay, add it to /etc/rc.d/rc.local

Here's an example:
```
setkeycodes e008 200 #Quickplay button
setkeycodes e00e 201 #DVD button
```

and in .xbindkeysrc:
```
"cellwriter"
 c:169
"rotatesrn.sh"
 c:168
```
Note: Of course, you need your own **rotatesrn.sh**


-------------------------------------------------------------

Now, if you anyone want to help me with my problem (TX2000 Filesystem Corrupts Upon Resume From Suspend), please post in [this forum thread](http://forums.fedoraforum.org/showthread.php?p=1027479#post1027479) thanks!

---

### Post by ACLBandit on 2008-06-09
FANTASTIC call on the hibernation/suspend fix-- I've been looking for something like that for ages!! ^_^

---

### Post by M42 on 2008-06-09
> **dimonzub said:**
> i had this problem as well and CTRL+ALT+F1 then CTRL+ALT+F7 did not help me as well. i have followed instructions for hibernate on the TC1100 laptop and it worked for me

[http://wiki.linuxquestions.org/wiki/Tc1100#Hibernate_and_suspend_to_RAM]("http://wiki.linuxquestions.org/wiki/Tc1100#Hibernate_and_suspend_to_RAM")

See if it will help you.


Beware, this blew my xorg and had to boot the recovery mode, have it fix X and then copy my old xorg.conf to the /etc/X11/ directory.

---

### Post by unterfuhrer on 2008-06-09
> **dimonzub said:**
> i had this problem as well and CTRL+ALT+F1 then CTRL+ALT+F7 did not help me as well. i have followed instructions for hibernate on the TC1100 laptop and it worked for me

[http://wiki.linuxquestions.org/wiki/Tc1100#Hibernate_and_suspend_to_RAM]("http://wiki.linuxquestions.org/wiki/Tc1100#Hibernate_and_suspend_to_RAM")

See if it will help you.

In that link its writen:     

*  In /etc/X11/xorg.conf, add this line to the Device section describing the nVidia adapter: 

Option "NvAGP" "1"

I can't find were to writ it in xorg.conf, anyone that could post ther xorg.conf so i can see were to write it?

Thanks

---

### Post by ACLBandit on 2008-06-09
Didn't blow my xorg.conf at all, worked like a dream. Mine looks as follows:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	0
	Option "NvAGP" "1"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	Option "NoLogo" "True"
	Option "RandRRotation"
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x800"	"1280x720"	"1280x768"	"800x600"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Synaptics Touchpad"
        Inputdevice     "TabletPCStylus"
        Inputdevice     "TabletPCStylus2"
       Inputdevice     "TabletPCStylus3"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

Section "InputDevice"
    Identifier "TabletPCStylus"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
    Option "Type" "stylus"
    Option "SendCoreEvents" "true"	
    Option "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
    Option "Button2" "3"  # make side-switch a right button
#  Option "TopX" "225"
   # Option "TopY" "122"
   # Option "BottomX" "26365"
   # Option "BottomY" "16488"
EndSection

Section "InputDevice"
	Identifier "TabletPCStylus2"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
	Option "Type" "stylus"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/input/wacom"
EndSection

Section "InputDevice"
    Identifier     "TabletPCStylus3"
    Driver         "wacom"
    Option         "ForceDevice" "ISDV4"
    Option         "Type" "eraser"
    Option         "Button3" "2"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
EndSection
```

---

### Post by joutsen on 2008-06-10
> **ACLBandit said:**
> FANTASTIC call on the hibernation/suspend fix-- I've been looking for something like that for ages!! ^_^

From this I deduce you have been able to get the suspend to work reliably, i.e. you have fixed the problem of the screen not waking up with the rest of the machine.

Could you or anyone else with suspend working post the full /etc/default/acpi-support contents here? And just to make sure, perhaps also the "Device" section of /etc/X11/xorg.conf?

Thanks!

---

### Post by paulo_raca on 2008-06-10
Hi guys!
At first I was very disappointed with my screen calibration. If I calibrated it to work OK in the middle of the screen, it would behave oddly near the edges (I had to click about 1 cm "outside" the screen to pick a scrollbar), and, of course, if I calibrated it to work in the borders, it would become weird in the middle.

Since TopX, TopY, BottomX, BottomY attributes weren't able to address this problem, I've written a patch to linuxwacom to allow finer calibration:

[http://sourceforge.net/tracker/index.php?func=detail&aid=1957296&group_id=69596&atid=525127](http://sourceforge.net/tracker/index.php?func=detail&aid=1957296&group_id=69596&atid=525127)

I hope someone finds it useful :)

---

### Post by MurDoK on 2008-06-10
I found a ticket in launchpad from a guy who has reported also a problem related to cpu-scaling. I think it's the same than in our case:

[URL="https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/228374"]
https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/228374[/URL]

---

### Post by Wolvenhaven on 2008-06-10
Edit: Fixed the wireless and tablet problems.

---

### Post by M42 on 2008-06-10
> **xraytroubadour said:**
> Hello again,

Ok, I barely understand what I just did, but for now my low-resolution problem seems to be solved. Even though I may be the only one having the problem, I'll document it here now (I hate seing threads that finish with "Hey I found the solution", and then nothing)

Anyway, as I said I have no clue what this all mean. I'll also stop here since I am probably mostly talking to myself. (I wonder why nobody else got this issue, though...)

I developed the same low res problem.  Thanks for posting your solution.  It worked for me as well.

---

### Post by wire604 on 2008-06-11
> **pAt84 said:**
> Well yeah, thing is that I myself do not really know what I am doing. ;)

Did you actually run the guide on a fresh installation of hardy? That is what I did and it worked like a charm. I also got the same error telling me that the module is not there.

Edit: And as for you lsusb? What is going on there? Here is mine:
```

Bus 002 Device 004: ID 056a:0093 Wacom Co., Ltd 
Bus 002 Device 003: ID 064e:a110 Suyin Corp. 
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 001 Device 001: ID 0000:0000 

```

The last one is my mouse. Your AuthenTec-thingy is probably the fingerprint reader. I don't have one for some reason. But what is the general 'Hewlett-Packard' and 'Chicony Electronics Co., Ltd'? Mouse? Keyboard? While your wacom lies on Bus 1 mine lies on Bus 2. Someone else with the tx2000z should print his/her lsusb output. Maybe your issue likes there although I doubt it. 

Pat

Hey Pat !
which version of the file linux-wacom did you use ?

---

### Post by Wolvenhaven on 2008-06-11
Thanks for all this information guys, I have gotten everything working.  However I cannot figure out how to get the calibration script and the rotate script working.  Where exactly do I place them?  What do I do to run them?  And how do I bind the rotate script to the rotation button?

---

### Post by pAt84 on 2008-06-11
> **wire604 said:**
> Hey Pat !
which version of the file linux-wacom did you use ?

The one, TomTheWombat is refering to in his tutorial: 0.7.9-11

Best
Pat

---

### Post by mika_aus on 2008-06-11
I have been following the tutorial line by line and I can get the touchscreen and the pen to work,

Attached is the first error that I have come across. I have a tx2004au running 8.04 64bit. installed all the updates that are available as of today. Kernal 19 I think. I am still learing all the ling as I used to be a windows person. please help.

~/linuxwacom-0.7.9-11$ rmmod wacom
ERROR: Module wacom does not exist in /proc/modules
mz@mz-laptop:~/linuxwacom-0.7.9-11$ cp src/2.6.24/wacom.ko /lib/modules/2.6.24-19-generic/kernel/drivers/input/tablet/wacom.ko
cp: cannot create regular file `/lib/modules/2.6.24-19-generic/kernel/drivers/input/tablet/wacom.ko': Permission denied

---

### Post by MurDoK on 2008-06-11
> **mika_aus said:**
> I have been following the tutorial line by line and I can get the touchscreen and the pen to work,

Attached is the first error that I have come across. I have a tx2004au running 8.04 64bit. installed all the updates that are available as of today. Kernal 19 I think. I am still learing all the ling as I used to be a windows person. please help.

~/linuxwacom-0.7.9-11$ rmmod wacom
ERROR: Module wacom does not exist in /proc/modules
mz@mz-laptop:~/linuxwacom-0.7.9-11$ cp src/2.6.24/wacom.ko /lib/modules/2.6.24-19-generic/kernel/drivers/input/tablet/wacom.ko
cp: cannot create regular file `/lib/modules/2.6.24-19-generic/kernel/drivers/input/tablet/wacom.ko': Permission denied

type 'sudo' before 'cp' and almost always when you get a permission denied error
```
sudo cp src/2.6.24/wacom.ko /lib/modules/2.6.24-19-generic/kernel/drivers/input/tablet/wacom.ko
```

---

### Post by mika_aus on 2008-06-11
That did the trick thanks guys. All i need to make work if the figure print scanner for logging on and screen rotate and map all the buttons and find the best program to test the webcam. any thoughts?:guitar:

---

### Post by pAt84 on 2008-06-11
Well, my webcam worked out of the box with 8.04 (in Skype). So you might wanne give this a try.

---

### Post by mika_aus on 2008-06-11
what is the best way in calobrating the touch screen? the pen is fine the touch side of it is getting worse. Is it possible to set up the tablet to be like . [http://www.youtube.com/watch?v=UrCOWqZYQEc](http://www.youtube.com/watch?v=UrCOWqZYQEc)

if it what am i missing??

---

### Post by sjones411 on 2008-06-11
> **mika_aus said:**
> ...and find the best program to test the webcam. any thoughts?

You should try the webcam program "Cheese".  It's a clone of Photobooth for Mac OS X.  It's in synaptic, go look it up.

---

### Post by Wolvenhaven on 2008-06-12
Even when plugged in my cpu is stuck at 800mhz.  What are you guy's fixes for this.  Also with xbindkeys, how do I bind the rotation script?  ' "rotation.sh" c:205 ' doesn't work.

---

### Post by teras on 2008-06-12
> **Wolvenhaven said:**
> Even when plugged in my cpu is stuck at 800mhz.  What are you guy's fixes for this.  Also with xbindkeys, how do I bind the rotation script?  ' "rotation.sh" c:205 ' doesn't work.

That's normal behavior, to save battery life.
If you need more CPU power, this number should change upwards.

---

### Post by sjones411 on 2008-06-12
> **Wolvenhaven said:**
> Even when plugged in my cpu is stuck at 800mhz.  What are you guy's fixes for this.  Also with xbindkeys, how do I bind the rotation script?  ' "rotation.sh" c:205 ' doesn't work.

Does the rotate script work in the terminal?  Don't forget to chmod +x rotation.sh.

EDIT: Ah, I also forgot, you have to point to where the script is.  So if it's in your home folder it would be "~/rotation.sh".

---

### Post by Wolvenhaven on 2008-06-13
> **sjones411 said:**
> Does the rotate script work in the terminal?  Don't forget to chmod +x rotation.sh.

EDIT: Ah, I also forgot, you have to point to where the script is.  So if it's in your home folder it would be "~/rotation.sh".

I was just really dumb,I forgot to do the sh for "sh /rotation.sh"

(written using cellwriter, thanks guys)

---

### Post by wire604 on 2008-06-14
hey hey i got it working !

---

### Post by mika_aus on 2008-06-15
Has anyone got the screen rotate button and the button next to it working? If so how do you map the buttons and add the additional code to make the screen rotate. i have already got the screen to rotate but i cant map the buttons. Also has anyone test the additional screen outputs?

---

### Post by Blayde on 2008-06-16
Thanks so much for your help on this thread. I've got the circle-with-one-arrow button set to run the rotate script and the touch screen working good enough to be useful.

As far as the wireless goes, the Restricted Hardware Drivers added one called 'wl' that has left me less than satisfied. I don't think WPA or WEP work and I'm hoping that it's the reason I can't get a shell when I ssh to other computers (although I have no idea why a borked network driver would cause ssh to not work).

The two screen buttons (one with two arrows and the other like a gear) I can't get to work either. They don't show up in xev so I guess they need an entire driver just to use two buttons *grumble

One last thing, what is the status of the remote control thing? I figured it would just do the same thing as the keyboard but it doesn't even do anything on mine... Is there some IR stuff i need to install to make it work?

---

### Post by mika_aus on 2008-06-16
THe remote works out of the box. It runs in Jukebox

---

### Post by Blayde on 2008-06-16
Alright, I feel silly now. The remote does in fact work - it just came with a bad battery.

I'm pretty sure the wl wireless driver breaks my ssh: It doesn't happen when I'm using a wired connection. I suppose I should file a bug on launchpad... I'd like to use ndis for the time being but I'm running hardy-amd64 and haven't had any luck finding 64-bit windows xp drivers...

to get the dvd and circle-with-one-arrow buttons working read this
  [http://aldeby.org/blog/index.php/en-hp-pavilion-multimedia-buttons-configuration-under-linux-linux-quickplay.html](http://aldeby.org/blog/index.php/en-hp-pavilion-multimedia-buttons-configuration-under-linux-linux-quickplay.html)

like i said before the other two buttons will most likely need a driver

---

### Post by Wolvenhaven on 2008-06-18
> **Blayde said:**
> Alright, I feel silly now. The remote does in fact work - it just came with a bad battery.

I'm pretty sure the wl wireless driver breaks my ssh: It doesn't happen when I'm using a wired connection. I suppose I should file a bug on launchpad... I'd like to use ndis for the time being but I'm running hardy-amd64 and haven't had any luck finding 64-bit windows xp drivers...

to get the dvd and circle-with-one-arrow buttons working read this
  [http://aldeby.org/blog/index.php/en-hp-pavilion-multimedia-buttons-configuration-under-linux-linux-quickplay.html](http://aldeby.org/blog/index.php/en-hp-pavilion-multimedia-buttons-configuration-under-linux-linux-quickplay.html)

like i said before the other two buttons will most likely need a driver

The wl driver does not work with the wacom usb wireless card yet.

---

### Post by tempo500 on 2008-06-18
hi,
i finaly got to upgrade to hardy, everything is going much smoother than gutsy. thanks to all posting their solutions! i am running the latest nvidia betas, because all the opengl stuff in autodesk maya wont work with the stable one... i still have 1 open issue.

i bound screen rotation and undo to the (physical) screen buttons. works great! but they dont if the lid closed(with the screen up). anyway... i would like it much more if the screen would flip automaticaly 180 when i turn and shut the lid.

thanks again, phil

---

### Post by joutsen on 2008-06-19
On getting the suspend to work:

At least on the tx2020eo version, suspend works (2 test cases) by adding "noapic nolapic irqfixup" to the kernel parameters. No other changes to the standard Ubuntu install seem to be necessary.

If you have not added kernel parameters before:
Parameters can be added to /boot/grub/menu.lst, at the end of each kernel command line. (And reboot.)

---

### Post by amba on 2008-06-19
hi,
i just tried to compile myself the wacom-thing to get stylus working, when typing:
./configure --enable-wacom
i get this error:
*checking for C compiler default output file name... configure: error: C compiler cannot create executables*

I'm new at Kubuntu, just installed it few days ago.
Linux kernel headers are installed, no clue why gcc should'nt create execs :(
Thanks!

EDIT:
ok, i'm noob, i can't read.
Didn't set up the proper environment. My error was about build-essential :oops:

---

### Post by amba on 2008-06-22
Hello again,
i got almost everything working!
Thank you very much guys, this forum rox!!

I got a trouble with rotation script, it doesn't work at all.
If i type in shell (as user or root, it's same)

:~# xrandr -o left

i get this error:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  158 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```

There ain't more info in Xorg.0.log * user.log * /var/log/messages * dmesg

Do you know why it happens?

---

### Post by joutsen on 2008-06-23
amba, have you restarted the X server?

---

### Post by amba on 2008-06-23
ehm..
i think i've read all the post in this thread, but i missed TomtheWombat's one, number #73.
It was xorg.conf setting, now fixed. Thank you

---

### Post by mirosol on 2008-06-24
Hi again.
My post at finnish forums paid out ([original finnish thread is here](http://forum.ubuntu-fi.org/index.php?topic=18172.0)) (thanks to you also, joutsen). I managed to get TomTheWombat's wacom installation working, as well as almost everything else.

I Have only those two dead buttons, that don't seem to wake up. Everything else is working great.

I even got [this script from mgonber](http://mirosol.kapsi.fi/tx2020/rotation.sh.txt) to rotate stylus and screen 90 degrees clockwise at the same time.

I finally had time to translate that finnish post to english, so [here's my howto](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm) in english.

Thank yous to everyone, who helped me.

---

### Post by joutsen on 2008-06-24
This thread is starting to be too long...

Was there a "final" solution for calibrating the touchscreen for finger use?

Thanks,
+ Mikael

---

### Post by mirosol on 2008-06-24
Didn't find anything yet, but my best guess is to calibrate it manually. Like TomTheWombat's original stylus calibration... Which works perfectly. At least for me.

I think it would be enough to get it disabled, but don't know how to do that either... Sometime ago someone tried, with no permanent results on this thread.

Ok.

I added manual calibrations that someone posted on this thread earlier.

Check my xorg.conf. Works ok with that.

---

### Post by majo on 2008-06-25
Since I updated ubuntu (after new installation) I have problems with my mouse on touchpad (tx2000z) 

For example

I open firefox then I land on some page that I can scroll down if I hit down arrow it goes all the way down. Duno why?

Btw I installed everything from first page and fallowed everything from page 1-17 :) everything else works great. Oh only thing that I notice is if I hit mute button its not changing the light to amber, but that does not bother me that much.

Please help me with above issue. Thank you.

---

### Post by gali98 on 2008-06-25
Hey guys!
Siennalizard has started a thread and I have also helped to get a comprehensive tutorial on the tx2000 series....
[http://ubuntuforums.org/showthread.php?t=837657](http://ubuntuforums.org/showthread.php?t=837657)
Just letting you know that If you need some help you may also check out there.
Also this may interest the Wacom Fans:

> Thanks for all this. Hold off on the Wacom work: I have been in touch with the developers, and they're going to be updating their driver to support this tablet any day.

Siennalizard told me this. Maybe we can see some good calibration very soon. Cheers,
Kory

---

### Post by eeg710 on 2008-06-26
Hi all,

First off, thanks for your help with getting most everything else working.  I'm still having some trouble with the Wacom driver.  I think I've tracked down the problem to its source, but I don't know how to fix it.

When I run ./configure --enable-wacom as in Wombat's guide, it can't find "ncurses.h" so it won't install most of the build options.  I can post the entire output if you need it, just let me know.  Does anybody know of a fix for this?

Thanks in advance,

Ian

---

### Post by gali98 on 2008-06-28
Hey Guys just updating something from my previous post (sorry Ian but I can't help you but I'm sure someone can! :))
I spoke of the updated wacom for tablets like ours. 
I found the link to the mailing list discussing it in case anyone was interested.

[http://www.nabble.com/Wacom-tablet-USB-touchscreen-on-HP-TX2130ea-td18059563.html](http://www.nabble.com/Wacom-tablet-USB-touchscreen-on-HP-TX2130ea-td18059563.html)

The part that interested me was when he talks about rewriting the protocol. Sounds good to me! Hope it comes soon. Thanks,
Kory

---

### Post by pAt84 on 2008-07-12
Well, am I the only one who is having issues with standby? I did all the stuff from the wiki (change the two lines in the file and add NvAGP to X's config file). However, it still will not do the trick. Hibernating works fine but for standby the display just does not turn back on. Same happens when I close the lid but at least here I can turn it on again with some ALT+CTRL+F1/F7 magic. I tried several different boot parameters without success.

Pat

---

### Post by dharivs on 2008-07-13
Hi,

Thanks a lot for your great work! I followed all your posts and now I have my tx2000es working like a charm... Well, there are a few issues:

  - Hight load cycle count: it was at 200!! With hdparm -B 254 (or 255) it works well, but the hdd gets a little hotter than usual (before: 48, after: 50).
  - Life battery: I cannot get more than one hour and half of battery life.

I installed powertop from Intel and I get that the 50% of consumption comes from ehci_hcd:usb2, which is this: "Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7c65640 USB-2.0 "Tetrahub"".

I will try to disable it, and test... I wonder if it will affect only to the card reader.

If someone knows how to improve the battery life, can you post some advises?

Thanks a lot!

---

### Post by mrumble on 2008-07-23
I have read through a lot of these forums and found that people are having problems with CPU scaling while on battery. I'm having the OPPOSITE problem... on current I'm stuck at 2.2GHz (both processors). When I unplug, it immediately jumps into whatever scaling settings I have set.

Thoughts? Ideas?

---

### Post by TorchlightJay on 2008-07-25
Hey, is anyone else having problems with their wireless and kernel 2.6.24-20-generic? Any ideas as to what's wrong?

---

### Post by gali98 on 2008-07-26
I did a while back.... I am on rt. What I did was go in synaptic and do a manual downgrade and locked it. After a while the module package was updated and it worked again... Hope that helps... :)
BTW...

The linux-wacom dev package has been updated to 0.8.1.1 (the source not a .deb or anything) which includes real support for usb tablet pc's. (see my above post)
I compiled it without any packages and the tablet part worked in about two minutes.
I had to calibrate the touch myself but it only took less than ten or so minutes.
For some reason wacomcpl is broken in some way, but I think someone submitted a patch or something on it.
Anyway thought I would let y'all know. It works great...
Well, actually the pressure on the pen is messed up. it jumps up to max in the at middle pressure then starts coming down again. I am going to file a bug report or something.
Have a good Day!

Kory

---

### Post by TomtheWombat on 2008-07-26
The open-source 'wl' driver appears to support our broadcom chipset now.  This driver will load instead of the ndiswrapper driver.  'wl' does not appear to work with WAP encryption.  I'm not sure about WEP...  You could probably blacklist wl and force ndiswrapper to load..

---

### Post by ztidwell on 2008-07-26
If anyone is still having the problem with having to press Alt + F1 then Alt + F7 when the screen is turned off, I found a solution [here]("http://ubuntuforums.org/showthread.php?t=780996").

---

### Post by tempo500 on 2008-07-27
did anybody get the omke.pl to work? it should enable the lid buttons even when its shut/tablet mode. [http://sourceforge.net/projects/omke/]("http://sourceforge.net/projects/omke/")

it starts fine with "sudo ./omke.pl -k 1" the feedback is:
"HP Omnibook multimedia/onetouch keys enabled."
unfortunately the buttons disable again when i shut the lid.

ps.: the buttons work fine when the lid is open.

---

### Post by gali98 on 2008-07-27
I have written a short tutorial on how to get the stylus and touchscreen working with a new version of linuxwacom made for Usb tablets.
This way you don't have to apply patches....
go here to see
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)
Kory

---

### Post by ztidwell on 2008-07-28
> **tempo500 said:**
> 
unfortunately the buttons disable again when i shut the lid.


My buttons worked with the lid open right out of the box.

I was able to get the buttons working when the lid is closed by updating to the latest bios from HP.

---

### Post by gali98 on 2008-07-29
> **ztidwell said:**
> My buttons worked with the lid open right out of the box.

I was able to get the buttons working when the lid is closed by updating to the latest bios from HP.

How did you update the bios? (no floppy drive)
I doubt I will but just want to know for the future...
Do you have to do it through vista?

Kory

---

### Post by ztidwell on 2008-07-29
> **gali98 said:**
> How did you update the bios? (no floppy drive)
I doubt I will but just want to know for the future...
Do you have to do it through vista?

Kory

Yeah, I downloaded the HP flash app and ran it from Vista.

---

### Post by FakeOutdoorsman on 2008-07-29
> **gali98 said:**
> How did you update the bios? (no floppy drive)
I doubt I will but just want to know for the future...
Do you have to do it through vista?

Kory
I did it by following this thread:
[HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")

---

### Post by tempo500 on 2008-07-30
thats interesting... just got my laptop back from hp, thei updated the bios for me because of nvidias heat problem... which bios version are you using? still having problems with those buttons. dont do me any good if they just work with an open lid... thanks phil

---

### Post by gali98 on 2008-07-30
Wait a second... What buttons are you talking about?

The DVD and Quickplay (or whatever it was) buttons work....

I don't guess I have tried the media buttons on the side....

Kory

---

### Post by ztidwell on 2008-07-31
My DVD and quickplay buttons always worked, but they stopped working if I converted the laptop to tablet mode.  The bios update fixed that.

---

### Post by tempo500 on 2008-07-31
yes the dvd and the button bellow(circle arrow) the media buttons on the outside worked out of the box.
i mapped the rotation script and a undo command onto the buttons, which works great, they just refuse to work when the lid is shut/ in tablet mode. i had my tx2140 in service two time because the gpu was heating up to 110 degrees. there was a press release from nvidia because of faulty gpus... the first time hp changed the heatsink and fan, which did not work, then they changed the motherboard and updated the bios. so i am not sure if i want to touch the bios right now, beause my current one changed the speed of the fans so it doesnt overheat. did you notice after your bios update that the fans spinn faster? thanks, phil

```
sudo gedit /etc/X11/xorg.conf
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "NoLogo" "True"
    Option         "RandRRotation"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
EndSection

sudo apt-get install xbindkeys xvkbd
sudo cp tx2000 alternative.sh /usr/bin
 gedit ~/.xbindkeysrc
"WacomRotate.sh"
 c:0xed
"xvkbd -text "\Cz""
 c:0xcd
testing
 xbindkeys -v
System --> Preferences --> Session
xbindkeys
```

---

### Post by TomtheWombat on 2008-07-31
I upgraded the bios recently, and I have also noticed that the fans are spinning faster/more often..  It is rather annoying.

---

### Post by marvlowe on 2008-07-31
I'm trying to get my broadcom wireless card to work on HP Pavilion 6000 laptop. It was working with proprietary driver B43 but I can no longer connect with it. I tried using the windows xp driver with Ndiswrapper. I downloaded sp34152.exe from HP site and following your instructions using cabextract I get the following:
marv@marv-laptop:~$ sudo cabextract sp34152.exe
[sudo] password for marv: 
sudo: cabextract: command not found

I'm have 64bit Hardy 8.04 kernel 2.6.24-19-generic. Is this command not available in this version? Am I just doing something wrong?

Marv

---

### Post by pAt84 on 2008-07-31
well, this thread is for the tx2000z. However, you are just missing the program cabextract here. Install it!

```
sudo apt-get install cabextract
```

Pat

---

### Post by gali98 on 2008-08-04
I have updated my tutorial again and everything is working almost perfect..
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

check it out..
Kory

---

### Post by SeanBlader on 2008-08-08
I have three things.

Crashed under suspend this afternoon which apparently corrupted the whole ubuntu partition, so grub couldn't get to the menu.lst. Something about an error saying superblock was bad. I ended up reinstalling, no lost data, just about 4 hours of effort in getting the OS back to where I wanted it. But now I have a SuperGrub CD ready to boot to back to Vista in an emergency.

Other than that, I love this thread. I was just brave enough to try hibernate and the system came back up which is encouraging.

And I think this thread should be more prominent at the top of the forum.


Actually I do have a few issues. The stylus is always dragging on the touchscreen, and touching the touchscreen definitely needs calibration. I'm using the 8.1-2 wacom driver, which I haven't tried to find the calibration utility for, but on the previous install when I ran it, it didn't read any touches at all, who's got tips for those elements?

On top of that, what's good to touch the screen for other than the Gimp and CellWriter?

---

### Post by Murphy2712 on 2008-08-14
I've a new problem : my microphone doesn't record sound anymore.
My soundcard works and I can hear something if I tap in the microphone but skype or twinkle can't hear something (it worked one month ago! I don't know if I made something wrong or if it's a bad update...)

Any hint ?

My modprobe is "snd-hda-intel model=hp" or "snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0".

---

### Post by gali98 on 2008-08-14
Well the second one should work..... 
Really none of the models for this sound are complete for our breed of laptop.
First, you are on a tx2000 series right?
Second you cannot have both entries... you might want to check...
third make sure you are completely updated....
if it still doesn't work, you might want to reinstall the package
linux-ubuntu-modules-2.6.24-19-generic
also I am working on writing some code for the driver that will autodetect our laptop and map all the inputs right...
I have the autodetect part (that was really easy) and now I am working the mapping part (the very very hard part).... I am not a coder, but I think I can do it....
I don't really have to code it, it is more of a problem-solving thing...
But don't hold your breathe, school is about to start and work is getting hectic so it may be many weeks.......
Kory

---

### Post by Murphy2712 on 2008-08-17
I use Debian Lenny, TX2050EF.
I'm using the driver "hp" OR "3stack" without any difference : sound works but microphone doesn't (since one month).
The last Debian kernel are 2.6.24-7 and 2.6.25-7 : also no microphone.
Maybe I'll try to boot with Vista to see if it's not an hardware problem...

---

### Post by gali98 on 2008-08-18
did you use the full line:

snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0

in /etc/modprobe.d/alsabase

and restart?

this should make the mic work.
Kory

---

### Post by SirKnight on 2008-08-22
One of the last things I would very much like is pressure sensitivity in Flash. Through [http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151) I set up pressure sensitivity easily in GIMP, which is great. I'd very much like to get the same effect in Flash. I'm using Wine to run MX 2004. Flash detects the tablet, but the pressure seems locked at the minimum possible, smaller than the thinnest brush stroke. There doesn't seem to be device preferences in the same way GIMP has them, so if anyone has any advised next steps or knows the solution, that would be incredibly helpful.

---

### Post by gali98 on 2008-08-22
you might try here...

[http://www.ehow.com/how_2182838_use-graphics-tablet-flash.html](http://www.ehow.com/how_2182838_use-graphics-tablet-flash.html)

Kory

---

### Post by TorchlightJay on 2008-08-24
Hey everyone, 
  I have one question. I have those two new kernels ending in 20 and 21 and my wireless doesn't work. Anyone overcome this product yet?

---

### Post by gali98 on 2008-08-24
try and downgrade the module package to an earlier package.
This happened a while back for the rt kernel modules and I downgraded. The next update fixed it.
Kory

---

### Post by SirKnight on 2008-08-24
> **gali98 said:**
> you might try here...

[http://www.ehow.com/how_2182838_use-graphics-tablet-flash.html](http://www.ehow.com/how_2182838_use-graphics-tablet-flash.html)

Kory

Not that simple, sadly. I don't really know why, but somewhere along the line, either Wine or Flash doesn't understand the screen's pressure input. It recognises it's there, but cannot read the pressure from the stylus. Hmm.

---

### Post by psycodrumfreak on 2008-08-25
I'm still having problems with my sound.  I've tried appending 
options snd-hda-intel model=hp
to the end of alsa-base and restarting it, but to no avail.  I'm using a tx2000 with 8.04 Hardy Ubuntu.  Any suggestions?

Reading over this forum over and over again, it occurred to me that my chipset is not Intel, it's the AMD 2.4 x 2.  Also, I am tri-booting this laptop with Vista, Xp, and Ubuntu.  all of which are on separate partitions.  Do I need to designate a number after hda, and if so, corresponding to what?  Also do i need to change intel to amd or nvidia. (Since hardware tester says my card is nvidia)

Well, after reattempting the tutorial on this thread, I'm not sure if reinstalling the nvidia drivers for the VGA display part changed anything or i restarted the computer instead of alsa-utils.  Either way my sound is now working.  

However i am running into a problem with the wireless.  Not so much that it doesn't work...I can locate the wireless networks and the one that I have access to, I cannot complete a connection with it. I did install ndiswrapper following my upgrade to 8.04, But i'm not seeing much of a difference.  The router is a D-Link Dl-624. Any other suggestions?

---

### Post by MadCoder on 2008-08-27
> **TomtheWombat said:**
> I updated my instructions with the patch for touchscreen support!  I noticed that it issues a button down command before it moves the cursor, though.  Be careful because it will start dragging things all over.

I'm sorry to rise the question again, but I was unable to fix this myself... I got touch & stylus & eraser fully functional and calibrated, but this bug is really nasty and I cant find why it happens/how to fix this. If you need any more info - just ask.

BTW I had to choose between microphone and correctly coloured mute button. I chosen model=3stack and orange mutebutton for now, but IMHO it is a hack.

---

### Post by gali98 on 2008-08-27
What version are you on (linux-wacom)?

Here is my tutorial for the newest version....
everything works...
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)
try it...
Kory

---

### Post by MadCoder on 2008-08-28
I managed to get some ugly sound-like thing from internal mic (problem was in amplification settings). But it really sucks when you have to talk really loudly so that your voice gets to the recordg software(skype). And also, this breaks normal colors for mute button=( So imho it is all a great hack, since in vista it worked fine. The damned file following.

```
options snd_hda_intel index=0 model=3stack position_fix=0 single_cmd=0
```

PS: IMHO since alsa is a kernel driver suse/ubuntu means nothing.

---

### Post by gali98 on 2008-08-28
That nasty input white noise is a driver issue. I think for whatever reason it is mapping something to input that shouldn't be there. You can't mute it. It does not come from any microphone. As soon as I track it down in the driver source I can fix it, but I am not a coder, and with school going the way it is, it may not be until spring break.

What I suggest doing is getting on the alsa forum or mailing list (mailing list would be better...) and telling them about it. Give them the module (snd-hda-intel) and do
> cat /proc/asound/card0/codec#0 >codec
then upload the file it makes (codec)
They might be able to fix it real easily. I'm not a coder so I'm not sure :)

Here is my codec file if you want to upload it too....

Also if they do help you and need testers, pm me and I will give you my email.

and I will be happy to help. I just don't have a lot of time, and I am working on the tablet part right now....
Thanks,
Kory

---

### Post by MadCoder on 2008-09-09
Hehe. sorry was afk for some time. if u need any help with tablet - you can pm me and i'll give my mail/jabber/icq. About alsa.. i just dont want to waste any more time. anyway while not at home i use external mic wich works just fine=) and at home i do not use notebook=) However, here is the file.

---

### Post by MadCoder on 2008-09-14
People of Ubuntu! If you have this laptop, and 64 bit kernel (i hope you have), you can do two things. First, upgrade to latest linuxwacom driver, it works out of the box with no patches , but with option --enable-xserver64 to configure.
Also, you can abandon windows NDIS driver and use bcm43. To do so you should download latest firmware package from openwrt.org or using nice scriptie install-bcm43-firmware (i am unsure if it installs in ubuntu by default...) bcm43 is a separate kernel module and you should build your own kernel with it (install the ssb driver also), or just install it with package manager. For now it fails to use maximim possible txpower(32 dbm), however i could not see any difference. powersave features work ok.
If you need any info on this - contact me. If you use 32 bit kernel USE NDISWRAPPER!
 Good luck=)

---

### Post by gali98 on 2008-09-14
Actually it does not use b43 (at least on the tx2000) but the wl driver.
This is because the specific device is not yet working with the b43 driver.
However it does everything you descirbe and does use the firmware files.
If you just use the restricted drivers it will work on both bits. (32 and 64 :))
I think it is put out by broadcom directly.
This driver (wl) works on both 32 and 64bit (at least for me) and wpa works (at least on 64, I have not tried it on 32)

For a full tutorial on the wacom tablet part (including touch) please see my tutorial:

[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

Just don't anyone to be confused :P
Kory

---

### Post by ACLBandit on 2008-09-15
Just found out something good: I *finally* got my CPU frequency scaling to move higher than 800 MHz on AC Power! 

All you need to do is the following. I have no idea if this is considered "good" or "safe," but it worked and I'm happy.

1)Alt-F2
2)Type gconf-editor, press enter
3)Click down to apps-->gnome-power-manager-->cpufreq
4)Change the value of performance_ac to "100"
5)Change the value of policy_ac to "performance

My CPU frequency is now the full, much-yearned-for 2.2GHz. Yaaay! ^_^

---

### Post by gali98 on 2008-09-15
actually another (probably safer) way to do this is to open a terminal and do

 sudo dpkg-reconfigure gnome-applets

then hit yes when asked.

Now if you add the cpu frequency scaling monitor

(rightclick on top bar -> add to panel -> drag cpu frequency scaling monitor to where you want it)

and click on it, you can change scaling/modes.

Have fun...
Kory

I would keep it on ondemand, unless this does not allow full potential. Also a note:
on the tx2000z, whenever I am on battery, it does not allow me over 800 MHz (per core) no matter what I do.....
Hope this helps. Also if you do this, I suggest changing the setting back to whatever it was before....

Note about selecting the yes, here is a problem (that I don't worry about)

 Bug #17604 :
> 
    Oh, please, not another setuid root application if we can avoid it. Which file does cpufreq-selector need access to to change the CPU speed? And why should a normal user be able to change the CPU speed in the first place? The automatic CPU speed works well enough for the majority of users, and control freaks can always use sudo to manually set the speed, or deliberately shoot themselves in the foot by making the binary suid root (as explained in README.Debian).

---

### Post by MurDoK on 2008-09-19
Hey folks, I hope the 800MHz-stuck-on-battery-mode is fixed for Intrepid.
Meanwhile, could someone confirm this bug in launchpad?
Thanks in advance!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271973]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271973")

---

### Post by ir0nman on 2008-09-22
Has anyone got suspend to work reliably yet? I don't care so much about hibernate, I would prefer to have the standby ability. Anyway, just haven't seen anything about it lately, but lots of people have complained about the problems. Thanks in advance guys.

Thanks,
-Rick

---

### Post by Cyborg_572 on 2008-09-23
I haven't tried this myself, but you could probably fix the cp set to 800 mhz on battery problem by turning of the limit cpu to 800 mhz when on battery option in the BIOS settings

---

### Post by gali98 on 2008-09-23
On tx2000z I updated My bios to the latest version (in my vista partition) and used the options
noapic nolapic irqfixup
on boot and both Suspend and Hibernate work. Sometimes when I hibernate it doesn't shutdown completely or it restarts.. It's weird, but when you boot up it still  goes back to its previous state.
Suspend is also a little wierd. If you shut the lid, it doesn't put it in suspend, but If you open it then close it back, it does....
Not to bad to deal with....
Kory

---

### Post by ir0nman on 2008-09-25
Adding those options seems to have worked for me, thanks!!!

---

### Post by MurDoK on 2008-09-25
> **Cyborg_572 said:**
> I haven't tried this myself, but you could probably fix the cp set to 800 mhz on battery problem by turning of the limit cpu to 800 mhz when on battery option in the BIOS settings

I don't think it's a bios limit since as you can read in my bug report, unloading and reloading certain modules, it works.

@gali98:
Aren't you experiencing this problem too? If so, please confirm the bug and maybe it will be fixed for Intrepid release :).
Leaving a 'me too' comment would be enough. Thanks in advance

---

### Post by gali98 on 2008-09-25
Yes I am. but only on battery power... I can check that bios setting, but I doubt that is it. I doubt it will be fixed in intrepid, but it depends on how much attention your bug generates and how easy it is to fix :) 
Bug confirmed at launchpad!

@ir0nman - Welcome!:)

Kory

---

### Post by MurDoK on 2008-09-25
> **gali98 said:**
> Yes I am. but only on battery power... I can check that bios setting, but I doubt that is it. I doubt it will be fixed in intrepid, but it depends on how much attention your bug generates and how easy it is to fix :) 
Bug confirmed at launchpad!

@ir0nman - Welcome!:)

Kory

Good! Anyways better 'confirmed' than 'new' :D

---

### Post by gali98 on 2008-09-26
Oh dear... this "workaround" is not good. Whatever modules it unloads and loads.. Well basically it kills it.
There must not be any temperature monitoring, because after maybe 20 minutes of doing this all of a sudden my laptop died.
Just shutoff without warning, and it was very, very hot.
So I am going to post that at the launchpad. I do not suggest doing that anymore as it could be very harmful to our precious lappies...
Kory

---

### Post by MurDoK on 2008-09-27
I'm sorry about that:( but at the moment I haven't had any behaviour similar to that :confused:

---

### Post by gali98 on 2008-09-28
hmmm.... What laptop are you on?

I was playing a game, and that was probably the cause.
I don't use any kind of cooler and the game is pretty intensive.
That is the only thing that it could be, as it has never done it before, and never after even after hours of playing that game.
I just didn't want anybody to kill their laptop :)
It did work though :P
Kory

---

### Post by pooyaplus on 2008-10-04
Hi,
I actually asked this question in another thread regarding wacom under hardy, but I guess heres' the place to get the answer.

Have you guys managed to get the right click working for the pen? I can not either play around with multiple objects easily.

I think the solutions I have tested so far regarding the tx2000 and the touchscreen functionality is limited to a point-and-click function for a single object.

Any ideas?

---

### Post by pooyaplus on 2008-10-05
Anyone going to test the right click functionality?

---

### Post by gali98 on 2008-10-05
Yes right click is working.
Just use wacomcpl. (as in open up the terminal and write wacomcpl and press enter)
You can select what button is for what styulus action and a few extra stuff.

Also I'm not sure what you mean "for a single object"?
Explain a little futher.
Kory

---

### Post by pooyaplus on 2008-10-06
Well in that case, I'm in business, as there is no device to choose from the list in wacomcpl  :)

By single object I mean a single pdf file, for example, or anything else on the desktop.

---

### Post by gali98 on 2008-10-06
Please upload your xorg.conf and I will have a looksie at it.
And on the single object do you mean that you are trying to click on two files at once?
Or are you just trying to click and drag with the box and multiselect?
Kory

---

### Post by pooyaplus on 2008-10-07
Kory,
Here is the xorg.conf attached. But I guess the problem is with the synaptic touchpad device. As it is not configured yet :popcorn:

---

### Post by gali98 on 2008-10-07
Okay I uploaded a version that should work. I also tried to fix the synaptics pad.
Kory

---

### Post by pooyaplus on 2008-10-07
Thanks for that, will test it asap. By the way, how did you fix the pad? I mean I may need to install something to get the scroll working. Right?

---

### Post by gali98 on 2008-10-07
No... You had the pad configured as a normal device. I added it under the driver synaptic.
Kory

---

### Post by pooyaplus on 2008-10-08
Kory,
Thanks for the fix. But the xmodmap still isnot working. The key bindings seems to be correct. I saw that window once, when I set the keys weeks ago and that disappeared in a blink of eye. Well at least I think I saw that, or may be that was just a deja vu. Anywhere else than Gconf you know to set the keys to bind the keys?  

Thanks for the xconf fix again.

---

### Post by pooyaplus on 2008-10-08
Kory,
Thanks for the fix. But the xmodmap still is not working. The key bindings seems to be correct. I saw that window once, when I set the keys weeks ago and that disappeared in a blink of eye. Well at least I think I saw that, or may be that was just a deja vu. Anywhere else than Gconf you know to set the keys to bind the keys?  

Thanks for the xconf fix again.

---

### Post by pooyaplus on 2008-10-08
Here is what wacomcpl command show. (see the attachement)
:confused:

---

### Post by gali98 on 2008-10-08
Okay... I'll post about the xmodmap stuff at the other post.. Sorry for taking so long....

Anyway I need you to run these commands

cd ~/Desktop

rm -r linuxwacom-0.8.1-4

wget [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.1-4.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.1-4.tar.bz2)

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade

sudo apt-get remove wacom-tools xserver-xorg-input-wacom

sudo apt-get install linux-headers-generic

tar xjvf linuxwacom-0.8.1-4.tar.bz2

cd linuxwacom-0.8.1-4

./configure --enable-wacom

make

sudo make install

sudo rmmod wacom

sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

(if you are on Intrepid or the 2.6.27 kernel, you need to change 2.6.24 to 2.6.26)


sudo depmod -e

sudo modprobe wacom


See if that works. Also reupload your xorg just to make sure we did not miss anything.

Also are you on the tx2000 or tx2500?

Kory

---

### Post by pooyaplus on 2008-10-11
Kory,
I have already done those steps to get the touchscreen working. And the wacom seems to work flawlessly. The only problem is the wacomcpl and the xmodmap! I am now using the xorg.conf that you uploaded in the previous posts. And I am on tx2000z US model.

The xmodmap and keybinding for the elisa works until you logout of the system or restart it; then it's gone.

---

### Post by pooyaplus on 2008-10-11
Hi again, 
touchpad setting in System>Preferences>Touchapd says:
```

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

```

How should I use the XF86config to use the gsynaptics or is it better just to simply set that xorg option to ture?

---

### Post by pooyaplus on 2008-10-11
Kory, 
here are the xorg.conf files; the first one is my previous OLD setting and the latter is the one you gave me. I finally managed to get the key bindings working, not sure if it works after another boot up or not. 

Anyways, the touchscreen pointing is not tuned when rotated, no matter in which position it is. Only the normal position gives me the correct pointing. May be that's due to the omission of the stylus 2, 3, and 4 in your xorg.conf setting?!

---

### Post by gali98 on 2008-10-11
Wow you've been busy :)
Sorry it has taken me this long to answer, but I have been short of time lately...
First on the synaptics issue, you will have to use the xorg.conf option as xf86config is not compiled on ubuntu. (it should be I think, but when xorg is built for ubuntu, they do not use the option to build it... don't ask me :))

and reason I ask you to basically redo the tutorial is because the devices were not showing up in wacomcpl, which they should be.
Do they still not show up? If they do, you can calibrate touch and the stylus there.
If not, you probably need to run the tutorial again...

As far as rotation.. I am not sure what you mean... 
Do you have the script that most people are using?
upload whatever script you have and I can fix it also.
The nameing convention of PCStlyus1 and so on is outdated.
the stylus, touch, eraser way works a lot better.
the script may call PCStylus1 or whatever to rotate when it should be calling touch and stylus to rotate. Just upload that.

On the .Xmodmap not loading that may be a problem.
here is what I suggest you do.
Rename that file to something else. (so that /home/yourusername/.Xmodmap
does not exist)

then restart.
Move it back ((so that /home/yourusername/.Xmodmap does  exist)
remember, it is case sensative.

then restart again and see if that gui loads, and make sure that the Xmodmap file is loaded. If it does still does not work, you can probably just add the xmodmap loading command you use to the session.
I think I have answered everything I can for now..... :)
Post back and we will go from there.
Kory

---

### Post by pooyaplus on 2008-10-12
Kory,
I appreciate that, and I understand as I've been really busy these days, and getting this laptop to work was an extra burden these weeks.

Anyways, I have gone through this tutorial, from linux on laptops website:
[http://mirosol.kapsi.fi/tx2020/tx2000howto.htm]("http://mirosol.kapsi.fi/tx2020/tx2000howto.htm")

but with the newest stable packages. And that's where the stylus 1,2,.. came from. 

The only difference between the xorg.conf I have been using recently and yours; is that of the rotation screen dimensions being defined in the stylus 1, 2, 3, and 4. (I guess so ;))  

I see your point to redo the work and maybe I have to do it over again; but if I could set the rotated screen size and dimensions that would be a relief in these busy days.

---

### Post by pooyaplus on 2008-10-14
Kory,
attached is the rotation.sh file that handles the rotation of the screen and resolution changes. The key bindings are now working, not sure of the reason behind their previous behavior. 

There is actually another problem that is driving me crazy when I am on my laptop, and that is the cursor jumps!! It always jumps to a fixed spot at the bottom corner of the screen; Where the firefox's weather forecast plugin is located.  

Have anyone seen such a thing before? Or maybe there is a problem somewhere else with this bloody laptop.

---

### Post by gali98 on 2008-10-14
Yes I know exaclty what you are talking about!!
If you weren't aware, 0.8.1-5 came out a couple days ago and I think it fixed most of this...
Just visit my tutorial for exact instructions...
Basically download it, configure it, make it, make install it, and then copy the module over and restart....

anyway on the other problem...

a better way to do rotation is with a daemon...
I found this source file on the net one day and it works great. Not only does it rotate, but is does some stuff with resolution so that it looks better.
I uploaded the source file below.
All you need to do is download it to you desktop.
Then run 
sudo apt-get install libxrandr-dev
and then 
gcc -lX11 -lXrandr -o .rotate.bin rotate.c
mv .rotate.bin ~/

then go to System->Preferences->Sessions
and add a new one with the command /home/yourusername/.rotate.bin
with whatever name you want.
then use the script I uploaded (just paste it all over the script you already have so you won't have to mess with gconf-editor agian :))
after that just log out then log back in and test it to make sure it works..
Kory

---

### Post by pooyaplus on 2008-10-15
Kory, 
Thanks for the info, I will get the 0.8.1-5 and will do a fresh cofig as soon as I find some time just for myself :)

Would you do me a favor and attach the bin file in a new post again. I could not spot that file in your previous posts as this thread is getting too big to navigate through. :popcorn:

Pooya

---

### Post by pooyaplus on 2008-10-15
All right, I finally did a fresh config. I got the new 0.8.1-5 and did the necessary steps, almost learned to heart as I have gone through it almost 100 times so far:) 

All I need is the rotate.bin to get the rotations to work. Hopefully.

---

### Post by gali98 on 2008-10-15
lol I forgot to attach it...
I will have to wait until I get home though. I am at work now. Just wait a few more hours :)
Kory

---

### Post by gali98 on 2008-10-15
Okay I am now uploading the source file. Just use the instuctions in my previous post to get it working :)
You need to rename it to rotate.c
Kory

---

### Post by pooyaplus on 2008-10-16
Well, I followed the steps for that C binary rotation file, bit I did not really understand the difference between this one and my own shell script. For both you need to bind the key to get it working. Where the daemon comes to play its role? 

By the way, the key binding functionality is gone again. I just renamed the key binding command to .rotate.bin, does that suffice?

---

### Post by gali98 on 2008-10-16
Oh dear.. :)
No you should have left the keybind the way it was.
The way the daemon works is that the new script (the one I said I would upload then forgot twice :)) only calls the display to rotate. (not the tablet parts) 
The daemon detects this and then rotates the tablet and does a little magic with gnome to get some better graphics.

So here is what you should do now..

First, change your keybinding to how it was before.
Next put the binary file (the file you made from the source) in you home folder named .rotate.bin
now go to System->Preferences->Sessions
and add a new one with the command /home/yourusername/.rotate.bin
with whatever name you want.

Next open up your existing script then download the script I uploaded (the actual one :))
and just copy and paste it over your existing one and save it.
Then log out and log back in.
And that is it.

Kory

---

### Post by ir0nman on 2008-10-17
Has anyone gotten the packages that are already default installed in Intrepid to work? I keep getting what seems to be no module loading. My dmesg | grep Wacom gives me only:
[   46.750005] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
Is anyone else getting this problem? I copied my /home from 8.04 after the amd64 iommu bug got me, but I don't see that causing a problem here. Anyway thanks for the help in advance.
Take Care,
-Rick

---

### Post by gali98 on 2008-10-17
They worked for me. I just formated my hard drive and installed intrepid beta.
Do you have both packages installed? (wacom-tools and xserver-xorg-input-wacom)
I wouldn't know what to tell you otherwise....
I cannot be postive they work, because I was testing a dev package of linuc-wacom at the same time, but I am pretty sure I removed everything before installing the packages.
Have you tried removing the module then probing it again?
Kory

---

### Post by ir0nman on 2008-10-17
Weird, I have both packages installed, I made sure of that. I've ran a rmmod wacom and a modprobe wacom no help there. I had everything working in hardy with the patched source. Thats just weird I could try reinstalling the packages and see if that helps I guess. Did you do anything other than your xorg config? 

Thanks for the help,
-Rick

---

### Post by gali98 on 2008-10-17
Like I said, I was testing packages, so it was probably already installed without my realization. You are not the only person who said it did not work.
Plus I am on the tx2000. You are on the tx2500 aren't you?
A couple of things to try:
Make sure you are up to date
reinstall them
Make sure your xorg.conf is right. (I just copied mine over from Hardy and it worked.)
Make sure you restart after reinstalling them. For whatever reason this is necessary instead of just restarting X.
Kory

---

### Post by ir0nman on 2008-10-17
Actually I am on a tx2000 as well, I copied my xorg from hardy first, but that didn't work, and then I tried one modifying mine to look more like yours from the Tablet PC Issues thread mine hardy one was pretty old and I figured it might have changed since then, that didn't help though, so I'm going to try reinstalling them now and rebooting. I suppose I could always manually install them though the thought of having it all done already was really nice lol.

Thanks for all the suggestions,
-Rick

---

### Post by pooyaplus on 2008-10-20
Hi, I am back again. :)) Sorry about the gap. 
OK. Here is what I've got:
I copied and pasted the new rotate.sh to my previous shell script, and added a new command for my session manager to run the binary C file. The key bindings are fine, BUT I still have the previous problem. 

The cursor does not come to the place where I press the pen. It needs calibration, I guess. This happens only when the screen is rotated. 

How can I test the start up session command I just have set? As the shell script seems to work.

---

### Post by gali98 on 2008-10-20
Okay make sure the daemon is running by running it manually then try the script.
if it still does not work, try running the command:
xsetwacom set stylus rotate ccw (you can use half, ccw, cw, and none.)
and see if that has any effect. (if not post any output from that command)

also on it not being calibrated, is it mirrored? or is it just off? Does it work with no rotation?

Kory

---

### Post by pooyaplus on 2008-10-21
I thought we were supposed to remove the wacom-tools when configuring the wacom, the command you named (xsetwacom) requires the wacom-tools to be installed:
```

The program 'xsetwacom' is currently not installed.  You can install it by typing:
sudo apt-get install wacom-tools
bash: xsetwacom: command not found

```

And that is not obviously what we want to do! Not again! :)

I checked the current session programs; and our bin file (.rotate.bin) was in the list. How can I run the command manually anyway?

The cursor is not mirrored, and is on but pointing somewhere else than where it is supposed to. And is working fine with no rotation.

---

### Post by gali98 on 2008-10-21
That is correct. But when running my tutorial, you compile xsetwacom
and sudo make install copies that program to your computer.
If you are getting that message, you did something wrong.
If you still have that linuxwacom folder, just cd into it and run 
sudo make install 
if not, download it again and run the general:
./configure --enable-wacom
make
sudo make install

Doing this will probably fix the calibration issue.
The daemon is probably running, but to run it manually just cd into your home folder:
cd ~
and then run the program like this:
./.rotate.bin

see if any of this helps at all... :)
Kory

---

### Post by pooyaplus on 2008-10-22
Right. But why the wacom is working just fine with no rotation? By the way, the daemon returns these every time time I rotate the screen (I ran it manually):

sh: xsetwacom: not found
sh: xsetwacom: not found
sh: xsetwacom: not found
sh: xsetwacom: not found

---

### Post by gali98 on 2008-10-22
The reason it is working is because the driver is installed (the kernel module wacom.ko)
However xsetwacom which changes settings for the module live is obviously not installed.
(which is the reason you are getting those messages.)
Just run the commands in the post above to get it installed. (I promise it really won't be painful this time :))
and it should work automatically.
Kory

---

### Post by pooyaplus on 2008-10-26
Wow, Thank you ever so much for all the helps. Finally it is working. I am just wondering why there been problems as I had done the configuration and installations over and over again.

Anyways, it is working and it's time to do some blues.:guitar:
:)

I have a friend that has configured the sl-modem and seems to be satisfactory for the country going where cable connection is not available. will post the  results back here soon.

Thanks again Kory.

---

### Post by gali98 on 2008-10-26
Glad you got it working :)
Have fun with the modem...
Kory

---

### Post by Murphy2712 on 2008-11-01
When I use
xsetwacom set "TabletPCStylus" Rotate xxx
it works with xxx=NONE,CW,CCW but not HALF !
With HALF, I get this error message :

$ xsetwacom set "TabletPCStylus" Rotate HALF

X Error: 8 BadMatch (invalid parameter attributes)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set TabletPCStylus value for 'Rotate'

Any idea ?
Maybe my xsetwacom is bad ?
I use the last linuxwacom-0.8.1-6 (with ./configure, make, make install).

---

### Post by pooyaplus on 2008-11-01
There is no bad xsetwacom as far as my concern. May be it is not configured properly. Try configuring it with this option:
```

./configure --enable-wacom
```

---

### Post by gali98 on 2008-11-01
actually you probably need to use 
```
./configure --enable-wacom --prefix=/usr
```
and you are using the wrong device names in your xorg.conf. (you are still using the way when you had to patch the source. That is a badly outdated style now)
if you upload your xorg.conf, I would be happy to fix it for you.
Kory

---

### Post by Murphy2712 on 2008-11-01
I already used "./configure --enable-wacom"
With "./configure --enable-wacom --prefix=/usr" I have the same error for HALF.

and here's my xorg.conf :

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	#Option		"Device"	"/dev/input/mice"
	Option		"Device"	"/dev/input/by-id/usb-Logitech_USB_Receiver-mouse"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#EndSection

Section "InputDevice"
    Identifier "TabletPCStylus"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
    Option "Type" "stylus"
    Option "SendCoreEvents" "true"	
    #Option "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
    Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-wacom"
    #Option "Button2" "3"  # make side-switch a right button
    Option "TopX" "225"
    Option "TopY" "122"
    Option "BottomX" "26365"
    Option "BottomY" "16488"
EndSection

Section "InputDevice"
	Identifier "TabletPCStylus2"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
	Option "Type" "stylus"
	Option "SendCoreEvents" "true"
	#Option "Device" "/dev/input/wacom"
	Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.1-wacom"
EndSection

Section "InputDevice"
    Identifier  "TabletPCStylus3"
    Driver      "wacom"
    Option      "ForceDevice" "ISDV4"
    Option      "Type" "eraser"
    Option      "SendCoreEvents" "true"
    #Option     "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
    Option	"Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-wacom"
EndSection

Section "Device"
	Identifier	"nVidia Corporation C51 [Geforce 6150 Go]"
	#Driver		"nv"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	Option		"HWCursor"	"off"
	Option		"RandRRotation"
#	Option		"Rotate"	"CW"
EndSection

Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [Geforce 6150 Go]"
	Monitor		"Écran générique"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	#InputDevice	"Synaptics Touchpad"
	InputDevice     "TabletPCStylus"
        InputDevice     "TabletPCStylus2"
        InputDevice     "TabletPCStylus3"
EndSection

#Section "Module"
#	load "wacom"
	#Load "glx"
#EndSection

```

And another thing : the computer hangs at startup displaying "Setting up standard PCI resources", I could only continue by pushing the power button 2 times.
I use kernel 2.6.26-1-686 with : noapic noirqdebug irqpoll.

---

### Post by gali98 on 2008-11-02
Okay... what are you on? (Hardy or Intrepid) and are you using a custom kernel?
if you use 2.6.27 you don't need any flags... 

on you xorg.conf, I uploaded what you need to use.
Kory

---

### Post by Murphy2712 on 2008-11-02
I'm on Debian Lenny (testing).
Even in unstable there's no 2.6.27 for now.
And always :
$ xsetwacom set "stylus" Rotate NONE
$ xsetwacom set "stylus" Rotate CW
$ xsetwacom set "stylus" Rotate CCW
$ xsetwacom set "stylus" Rotate HALF
X Error: 8 BadMatch (invalid parameter attributes)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set stylus value for 'Rotate'

But even CW or CCW don't seem to work fine : the cursor is never where I expect it to be (tested with xrandr -o right/left/inverted,normal) and it never goes out of the upper screen.

---

### Post by gali98 on 2008-11-02
Okay... first, Have you tried the new xorg.conf and restarted (the whole computer.. for whatever reason it makes the reason when restarting just x doesn't. I think it has something to do with HAL)
next try using sudo with xsetwacom and see if you get the same error.

I've never used straight debian so I'm not sure exactly how the system runs compared with ubuntu.

if it still does not work, can you run 
make clean
./configure --enable-wacom --prefix=/usr
make
sudo make install
sudo cp src/2.6.26/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/

and post all the output (every bit of text there is)
Thanks,
Kory

---

### Post by xavier1936 on 2008-11-02
Does the touch screen works for ubuntu 8.10 ?

---

### Post by gali98 on 2008-11-03
Yes.... See my tutorial on the matter.... If you have problems, you might also check the latest posts in that thread...
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)
Kory

---

### Post by Murphy2712 on 2008-11-03
> **gali98 said:**
> Okay... first, Have you tried the new xorg.conf and restarted (the whole computer.. for whatever reason it makes the reason when restarting just x doesn't. I think it has something to do with HAL)

Yes, but I had to change some input for the wacom to work fine :
Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-wacom"
and
Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.1-wacom"
because :
```
dmesg |grep Wacom
[   11.299323] input: Wacom ISDv4 93 as /class/input/input9
[   11.372822] input: Wacom ISDv4 93 as /class/input/input11
[   11.373249] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
murphy@debiantablet:~$ ls -l /dev/input/by-path/
total 0
lrwxrwxrwx 1 root root  9 nov  3  2008 pci-0000:00:0b.0-usb-0:5:1.0-event-mouse -> ../event1
lrwxrwxrwx 1 root root  9 nov  3  2008 pci-0000:00:0b.0-usb-0:5:1.0-mouse -> ../mouse0
lrwxrwxrwx 1 root root 10 nov  3  2008 pci-0000:00:0b.1-usb-0:2.1:1.0-event- -> ../event10
lrwxrwxrwx 1 root root  9 nov  3  2008 pci-0000:00:0b.1-usb-0:2.3:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 nov  3  2008 pci-0000:00:0b.1-usb-0:2.3:1.0-wacom -> ../event9
lrwxrwxrwx 1 root root  9 nov  3  2008 pci-0000:00:0b.1-usb-0:2.3:1.1- -> ../mouse2
lrwxrwxrwx 1 root root 10 nov  3  2008 pci-0000:00:0b.1-usb-0:2.3:1.1-wacom -> ../event11
lrwxrwxrwx 1 root root  9 nov  3  2008 platform-i8042-serio-0-event-kbd -> ../event0
lrwxrwxrwx 1 root root 10 nov  3  2008 platform-i8042-serio-1-event-mouse -> ../event12
lrwxrwxrwx 1 root root  9 nov  3  2008 platform-i8042-serio-1-mouse -> ../mouse3
lrwxrwxrwx 1 root root  9 nov  3  2008 platform-pcspkr-event-spkr -> ../event8

```

> **gali98 said:**
> 
next try using sudo with xsetwacom and see if you get the same error.
I've never used straight debian so I'm not sure exactly how the system runs compared with ubuntu.

Nothing different.

> **gali98 said:**
> 
if it still does not work, can you run 
make clean
./configure --enable-wacom --prefix=/usr
make
sudo make install
sudo cp src/2.6.26/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/

and post all the output (every bit of text there is)
Thanks,
Kory

And there's my outputs,
thanks.
I'll try if it's the same with a 64bit kernel... but never succeed in having wifi in 64bits (and is there a new method without ndiswrapper?).
[edit]
With my 64bits kernel it's worse, configure detects a 2.6.24 kernel and there's no wacom.ko in src/2.6.26/
```
----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.24
  module versioning - no
      kernel source - yes /usr/src/linux

```
but :
```

uname -a
Linux debiantablet 2.6.26-1-amd64 #1 SMP Thu Oct 9 16:53:32 UTC 2008 x86_64 GNU/Linux

```

---

### Post by gali98 on 2008-11-03
Okay... looking in your output, the only thing I noticed was this:
Xorg SDK - no  (in the configure command)

Mine says:
found in /usr/lib/xorg


So did you run the apt-get install commands at the beginning of my tutorial?
Try those, if that doesn't work, you might try searching debian packages (on the web) to see if you can find the package that has that folder in it. Maybe that is the problem. I can't see any other differences....
Hope this helps :)
Kory

---

### Post by Murphy2712 on 2008-11-04
Sure it helps !
I had to install xorg-dev, which installs
```
libdmx-dev libdmx1 libexpat1-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev
  libfs-dev libpixman-1-dev libxaw7-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxevie-dev libxevie1 libxfixes-dev libxfont-dev libxft-dev libxinerama-dev
  libxkbfile-dev libxkbui-dev libxkbui1 libxmu-dev libxmu-headers libxmuu-dev libxpm-dev
  libxrandr-dev libxrender-dev libxres-dev libxss-dev libxtrap-dev libxtst-dev libxv-dev
  libxvmc-dev libxxf86dga-dev libxxf86misc-dev libxxf86vm-dev pkg-config
  x11proto-bigreqs-dev x11proto-composite-dev x11proto-damage-dev x11proto-dmx-dev
  x11proto-evie-dev x11proto-fixes-dev x11proto-fontcache-dev x11proto-fonts-dev
  x11proto-gl-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev
  x11proto-resource-dev x11proto-scrnsaver-dev x11proto-trap-dev x11proto-video-dev
  x11proto-xcmisc-dev x11proto-xf86bigfont-dev x11proto-xf86dga-dev x11proto-xf86dri-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xorg-dev
  xserver-xorg-dev zlib1g-dev

```
to finally have
```

BUILD ENVIRONMENT:
Xorg SDK - yes /usr/include/xorg
BUILD OPTIONS:
wacom_drv.so - yes /usr/lib/xorg/modules/input
wacom*_drv quirks - libc-wrapper Uninit-called IsXExtensionPointer key-events dixScreenOrigins

```
instead of
```
BUILD ENVIRONMENT:
Xorg SDK - no
BUILD OPTIONS:
wacom_drv.so - no /usr/lib/xorg/modules/input
wacom*_drv quirks -

```

So now rotate HALF works ! :popcorn:
And also touch (which doesn't) !

Thanks a lot !

---

### Post by gali98 on 2008-11-04
Great..
but wait.. you said touch doesn't work? I don't guess I understand that last part :)
Kory

---

### Post by Murphy2712 on 2008-11-05
Oups, sorry : didn't (before this step).

Did you try a recent wl driver for wifi ? (in order to leave ndiswrapper)
I've read in this thread that it doesn't support encryption yet.

---

### Post by gali98 on 2008-11-05
The wireless works fine on my laptop. From what I've read, apparently wpa2 encryption does not work. It did work in Hardy however. I don't use encryption so I can't tell you for sure.
Kory

---

### Post by ir0nman on 2008-11-06
I'm using wpa2 encryption at my house and I've had no problem so far with the wl driver. Worked out of the box so to speak lol.

-Rick

---

### Post by Murphy2712 on 2008-11-10
What's the full name of "wl" driver/package ? I can't find it in my Debian.

---

### Post by gali98 on 2008-11-10
hmmm... I think wl is the resticted driver b43.. The driver itself is not proprietary, but the firmware (you get with b43-cutter) is. I think it is really just the kernel module, so I don't know what package it is in... You are on straigh debian aren't you?
Kory

---

### Post by Murphy2712 on 2008-11-12
I found that there's a special package that installs the firmware automatically :
apt-get install b43-fwcutter
But when I charge the module b43, there's no wlan0, only this in dmesg :
```
Broadcom 43xx driver loaded [ Features: PMLR, Firmware-ID: FW13 ]
```
I'm on Debian (Lenny).

---

### Post by gali98 on 2008-11-12
right.. thats the package I meant, I just spelled it wrong.. lol.
Okay, I don't know where to go from here. Ubuntu provides the Proprietary Hardware application that can download those drivers easily.
At this point the only option may be to compile the driver or something like that. This link may be useful to you:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Kory

---

### Post by kqian on 2008-12-11
Hi there, 

So just to be clear, your headphones now work? Because I've been at it for 2 weeks now, and couldn't get them to play any sound at all... What was it you did in the end that finally fixed it? 

I've also added that line 
options snd-hda-intel model=hp 
at the end of alsa-base

Any thoughts? 
Thanks for your time in advance.

---

### Post by Murphy2712 on 2008-12-11
> **kqian said:**
> Hi there, 

So just to be clear, your headphones now work? Because I've been at it for 2 weeks now, and couldn't get them to play any sound at all... What was it you did in the end that finally fixed it? 

I've also added that line 
options snd-hda-intel model=hp 
at the end of alsa-base

Any thoughts? 
Thanks for your time in advance.

I'm not sure you want to know.
I had a good setup but the microphone volume was set too high randomly at X startup so it produces some Larsen and the integrated sound card did not endure it well : after 10 times of doing this, the sound gradually decreased and now my soundcard is really DEAD. Checked with dual-boot Vista. I'm using some 10 dollar USB soundcard right now and will return the laptop for warranty soon.
Yes, software could damage hardware.

---

### Post by TorchlightJay on 2008-12-22
Hey has anyone successfully flashed the BIOS? I do not have a version of Windows running and in the past with other computers, I would create a bootable CD-ROM with MS-DOS 6 on it then I would burn the *exe file and other BIOS files onto another CD and flash the BIOS that way. Not much luck doing that with the HP SoftPaq files. Anyone have experience doing this with HP's running Linux or in particular the tx2000?

---

### Post by TomtheWombat on 2008-12-22
I didn't have any luck outside of installing windows.  :(  There are tutorials out there for installing windows on a flash drive, but it would have to be quite sizeable.

The should really offer a burn-bios-to-bootable-cd option. :)

P.S. Is there a recent bios?  I did a bios update in late spring that turned up all the fans.  The computer sounds like a lawn mower now.  You may not want that update unless you are afraid of your Nvidia chip dying.

---

### Post by pooyaplus on 2009-01-05
Hi, after almost a long time being away from this thread, this one is making mad. ](*,)

With the help of the guys here, to be more specific, gali98 (kory); I have almost no problem with my laptop, except the mouse jumps! Unfortunately, the cursor lands on a very bad area - where my firefox weather add on is located. And guess what, the browser heads to the weather forecast website.

Any ideas how to get rid of this jumps?

Thanks.

---

### Post by TomtheWombat on 2009-01-05
> **pooyaplus said:**
> With the help of the guys here, to be more specific, gali98 (kory); I have almost no problem with my laptop, except the mouse jumps!

Does the cursor jump while you are typing?  I resolve it by pressing the little button underspacebar to disable the trackpad.  My problem may be that I touch the trackpad while typing.

That is the only solution that I know of.

---

### Post by pooyaplus on 2009-01-05
No, I have the jumps even when I am surfing using my optical mouse.

---

### Post by lainzee on 2009-01-06
My touchscreen still isn't working - the stylus works fine, I have the eraser and the click button and everything, but when I touch the screen with my finger I'm getting no response.  No big deal, honestly, but I'm wondering why it isn't working.

My computer is a hp tx2000z.  I'm running Ubuntu 8.1.  Kernel is 2.6.27-9-generic.

My current xorg is attached.  Thanks in advance for any help.

---

### Post by lainzee on 2009-01-06
Nevermind.  I ran through the tutorial in the other thread [tablet pc issues] and its working perfectly now.  I don't think it was a problem with my xorg, but somewhere else in the installation process.

---

### Post by pooyaplus on 2009-01-10
Good you got it sorted. By the way, do you have that mouse jumps too?

---

### Post by Wolvenhaven on 2009-01-14
Ok, I used this thread to get 32bit 8.04 working completely with my tx2000z.  Thank you guys for all of that, however I'm having problems again.  I upgraded to 64bit 8.10 when I installed 4gb of ram and now I'm having quite a few problems.  Touchscreen won't work, I've tried following different guides, doing it the old way by compiling it; and still no luck.  I am also having a lot of instability problems, programs freezing for a few seconds or shutting down completely, if I try running setting for graphics other than none i get tearing, the title bar of applications will gray out and disappear.  I am generally hating 8.10 and thinking about downgrading to 64bit 8.04 because I know I can follow this guide and get it to work.  What would you guys suggest?  Working on this or giving up and redoing my install?

---

### Post by TomtheWombat on 2009-01-14
> **Wolvenhaven said:**
> Ok, I used this thread to get 32bit 8.04 working completely with my tx2000z.  Thank you guys for all of that, however I'm having problems again.  I upgraded to 64bit 8.10 when I installed 4gb of ram and now I'm having quite a few problems.  Touchscreen won't work, I've tried following different guides, doing it the old way by compiling it; and still no luck.  I am also having a lot of instability problems, programs freezing for a few seconds or shutting down completely, if I try running setting for graphics other than none i get tearing, the title bar of applications will gray out and disappear.  I am generally hating 8.10 and thinking about downgrading to 64bit 8.04 because I know I can follow this guide and get it to work.  What would you guys suggest?  Working on this or giving up and redoing my install?

Grey titlebars and titlebar artifacts with Compiz running are a problem with the nvidia driver and compiz.  This happens on all video cards using the nvidia driver (to my knowledge).

[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447) explains how to install wacom under 8.10.  100% working on 64-bit.

I don't have any problems with 8.10 64bit locking up or instability.  Sorry about that :(

---

### Post by Wolvenhaven on 2009-01-14
> **TomtheWombat said:**
> Grey titlebars and titlebar artifacts with Compiz running are a problem with the nvidia driver and compiz.  This happens on all video cards using the nvidia driver (to my knowledge).

[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447) explains how to install wacom under 8.10.  100% working on 64-bit.

I don't have any problems with 8.10 64bit locking up or instability.  Sorry about that :(

I didn't have any problems in 8.04 with compiz and my nvidia drivers, thanks for the help. I'll try it out.

---

### Post by TomtheWombat on 2009-01-14
> **Wolvenhaven said:**
> I didn't have any problems in 8.04 with compiz and my nvidia drivers, thanks for the help. I'll try it out.

Yeah, I don't know what the problem is.  I do know that everyone has it.

---

### Post by Wolvenhaven on 2009-01-14
> **TomtheWombat said:**
> Yeah, I don't know what the problem is.  I do know that everyone has it.

Ok, good I thought I was the only one, I followed the touchscreen tutorial and still can't get it working, I really am contemplating going back to 8.04 where everything worked, the only change between 8.04 I've seen was wireless worked on install, otherwise I feel like there are more problems with 8.10 on this laptop than there were on 8.04.

---

### Post by alegir on 2009-01-19
I finally got my audio to work properly in Intrepid, with the headphones functioning and the speakers muted when the headphones are in use:

1. Download the latest alsa bundle:

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.19.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.19.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.19.tar.bz2
```

2. Compile/Install the alsa driver:

```
tar -xvf alsa-driver-1.0.19.tar.bz2
cd alsa-driver-1.0.19
./configure --with-cards=hda-intel --with-sequencer=yes
make
sudo make install
```

3. Compile/Install the alsa library:

```
tar -xvf alsa-lib-1.0.19.tar.bz2
cd alsa-lib-1.0.19
./configure
make
sudo make install
```

4. Compile/Install the alsa utilities:

```
tar -xvf alsa-utils-1.0.19.tar.bz2
cd alsa-utils-1.0.19
./configure
make
sudo make install
```

5. Compile/Install the alsa firmware:

```
tar -xvf alsa-firmware-1.0.19.tar.bz2
cd alsa-firmware-1.0.19
./configure
make
sudo make install
```

6. Add the following to /etc/modprobe.d/alsa-base:

```
options snd-hda-intel model=hp position_fix=1
```

7. Make sure the following is in /etc/modules:
   (The options may be redundant, but does not matter)

```
snd-hda-intel model=hp position_fix=1
```

7. Try to remove and re-insert the module and restart alsa:

```
sudo modprobe -r snd_hda_intel
sudo modprobe snd-hda-intel model=hp position_fix=1
sudo /etc/init.d/alsasound restart
```

8. You may have to reboot.

-----------------------------------------------

After these steps my mute button went from orange to blue, my 
headphone jack sense started to work, and the speakers 
are properly muted with the headphones plugged in.

------------------------------------------------

Here is some info about my system:

HP dv2000z

My kernel:

```
alegir@alegir-laptop:~$ uname -a
Linux alegir-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux
```

**Note: My kernel is 32-bit as I only have 1GB of RAM.**

My Ubuntu version:

```
alegir@alegir-laptop:/opt/alsa$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid
```

My sound card:

```
alegir@alegir-laptop:/opt/alsa$ lspci

...

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
  
...
```

---

### Post by alegir on 2009-01-20
I found that in intrepid the rotate screen and DVD keys no longer work as in Hardy.

Here is how I got mine working again:

**1.** Edit /etc/rc.local, which probably has the following if you had this working in Hardy:

```
setkeycodes e008 200
setkeycodes e00e 201
```

Using setkeycodes is no longer necessary in Intrepid as the hotkey-setup init script sets the keycodes properly. 

Comment the two lines as follows:

```
#setkeycodes e008 200
#setkeycodes e00e 201
```

**2.** Now we need to figure out the new keycodes using xev. Install xev if you don't have it:

```
sudo apt-get install xev
```

For the moment, manually start the hotkey-setup init script:

```
sudo /etc/init.d/hotkey-setup start
```

**3.** Execute xev (a window will open) and press the rotate button and the DVD button, which should produce the following (among other things):

```
alegir@alegir-laptop:~$ xev
...

KeyRelease event, serial 34, synthetic NO, window 0x600001,
    root 0x1a6, subw 0x0, time 819660, (1233,94), root:(1239,684),
    state 0x0, keycode [COLOR="Red"]201[/COLOR] (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x600001,
    root 0x1a6, subw 0x0, time 879223, (532,-38), root:(538,552),
    state 0x0, keycode [COLOR="Red"]234[/COLOR] (keysym 0x1008ff32, XF86AudioMedia), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

...

```

The keycodes are [COLOR="Red"]201[/COLOR] for the rotate button, and [COLOR="Red"]234[/COLOR] for the DVD button. 

**4.** Now modify your xbindkeysrc file to reflect the new keycodes:

```
"/path/to/your/rotate/script"
    c:201
"/path/to/your/dvd/script"
    c:234
```

replacing the paths with the scripts that you wish to associate with the two buttons.

**5a.** If you want screen rotation at the GDM login screen, add the following to /etc/gdm/Init/Default, before the exit command:

```
exec xbindkeys -f /path/to/your/xbindkeysrc [COLOR="Red"]&[/COLOR]
```

replacing /path/to/your/xbindkeysrc with the appropriate path to your xbindkeysrc.  

[COLOR="Red"]**Note:**[/COLOR] You must use the **plain GDM greeter** in order for this to work. The themed greeters do not
use the /etc/gdm/Init/Default script.

Since xbindkeys is executed at the login screen by root, the key bindings also apply to users, so you can move on to step 6.

**5b.** If you only need rotation after a user logs in, skip the previous step and put the following in /etc/rc.local:

```
xbindkeys -f /opt/wacom/rotate/xbindkeysrc [COLOR="Red"]&[/COLOR]
```

**6.** The hotkey-setup init script does not start during boot. I found a bug on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/280994") for the Dell XPS M1210 which suggests:

```
sudo mv /etc/rc2.d/S20hotkey-setup /etc/rc2.d/S29hotkey-setup
```

After this I am able to use the rotate and DVD buttons in Intrepid. 

I think this also affects the Fn-F# keys as well.

---

### Post by alegir on 2009-01-20
> **Wolvenhaven said:**
> Ok, I used this thread to get 32bit 8.04 working completely with my tx2000z.  Thank you guys for all of that, however I'm having problems again.  I upgraded to 64bit 8.10 when I installed 4gb of ram and now I'm having quite a few problems.  Touchscreen won't work, I've tried following different guides, doing it the old way by compiling it; and still no luck.  I am also having a lot of instability problems, programs freezing for a few seconds or shutting down completely, if I try running setting for graphics other than none i get tearing, the title bar of applications will gray out and disappear.  I am generally hating 8.10 and thinking about downgrading to 64bit 8.04 because I know I can follow this guide and get it to work.  What would you guys suggest?  Working on this or giving up and redoing my install?

Hi Wolenhaven,

I guess the thing to do is take it one problem at a time. There are a few things I would try **if my next recourse was re-installation**. 

In any case, have you tried Hardy 64 with your 4GB of RAM, because there is a fair chance that the problem will show itself on Hardy 64-bit as well.

---------------

If I understand correctly you went from:

32-bit Hardy w/ <4GB RAM  ==> 64-bit Intrepid w/ 4GB of RAM

So this makes me bring the RAM into question a little bit:

Did you buy the RAM from HP?

Did you mix different RAM with what you had already from HP? 

Did you go out and get 4GB of brand new RAM?

-----------------------

Also can you attach your:

/etc/X11/xorg.conf 
/var/log/Xorg.0.log

so we know what you are starting with. 

Also the output of:

```
grep -i "x driver" /var/log/Xorg.0.log
```

This will tell us the version of the Nvidia driver you are using.

```
cat /proc/version_signature
```

This will tell us your precise kernel.

Also, are you using ndiswrapper, or the native wl driver for the wireless?

-------------------------------------------
Things you can try:

**1. Try using envy-ng, sometimes it picks a better Nvidia driver then the restricted driver manager:** 

Described [here]("https://help.ubuntu.com/community/NvidiaManual#Installation%20with%20Envy/EnvyNG").

Make sure to revert back if this does not work by uninstalling the nvidia driver with envy-ng and re-installing the previous one with the restricted driver manager.

----------------

**2. Try noapic/nolapic/noacpi kernel boot arguments to see if the freezes go away or are reduced.**

You do this as follows:

a) Press ESC during boot to access the GRUB menu.
b) Type 'e' on the kernel entry in the list that you normally use.
c) Go down to the kernel boot command by hitting down and type 'e' to edit it.
d) This allows you to pass arguments to the kernel and turn off the splash screen.
e) Add noapic/nolapic/noacpi in various combinations.
f) Type 'b' to boot with the new arguments.

There is no saying what combination will work, but you need to try them all for a period of time, since it is not clear what is causing the freezes. Make sure to try them both together and separately. I would just boot into each combination and go about your usual business, and see if the situation improves.

----------------

**3. Try one of the Intrepid proposed kernels:**

a) Go to the following directory:

```
cd /etc/apt/sources.list.d
```

b) Edit a new file as follows:

```
sudo gedit intrepid-prop.list
``` 

and add the following:

```
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed main
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-proposed main
```

c) Update and install the proposed 2.6.27-10 kernel: 

```
sudo apt-get update
sudo apt-get install linux-image-2.6.27-10-generic
```

d) Reboot into the new kernel and see if it is usable and any improvement.

e) Undo the changes you made to your repositories:

sudo rm /etc/apt/sources.list.d/intrepid-proposed.list
sudo apt-get update

f) You can also try the proposed linux-image-2.6.27-11-generic:

```
sudo apt-get install linux-image-2.6.27-11-generic
```

-----------------------

The touchscreen tutorial worked for me (32-bit) as long as I didn't use the Debian packages and compiled linuxwacom from source.

In what way does it fail? I'm assuming that the guide went smoothly and it doesn't fail to compile or anything. 

Does the wacom module load properly?

Look at: 

```
tail -f /var/log/kern.log
```

and 

```
tail -f /var/log/messages
```

while removing and inserting the module:

```
sudo modprobe -r wacom
sudo modprobe wacom
```

---

### Post by pooyaplus on 2009-03-07
> **TomtheWombat said:**
> Does the cursor jump while you are typing?  I resolve it by pressing the little button underspacebar to disable the trackpad.  My problem may be that I touch the trackpad while typing.

That is the only solution that I know of.

Any one got any idea how on earth I can get rid of these jumps?!:(

---

### Post by alegir on 2009-03-07
> **pooyaplus said:**
> Any one got any idea how on earth I can get rid of these jumps?!:(

Go to System -> Preferences -> Mouse
The try adjusting the sensitivity.

---

### Post by pooyaplus on 2009-03-08
Will give it a shot, but why it should be related to the mouse sensitivity? Even if it is, it should not jump to the same spot every single time.:confused:

I will test it asap.

---

### Post by Wolvenhaven on 2009-03-11
alegir:  I went from 32bit 8.04 with 2gb of ram, replaced the ram with 4gb of corsair.  Installed 64bit 8.10.  The graphical issue is the nvidia bug with compiz, I gave up with that, and the instability issue was fixed a few days after I made the post.  I haven't bothered trying to fix the compiz issue or touchscreen because of being too busy with school.  I'm hoping that when 9.04 gets released everything works(I was told it would).  The touchscreen issue when I followed the 8.10 guide was everything worked fine, but it wouldn't work, when I tried the 8.04 instructions, I got too many errors to bother.  I have tried compiling it myself, using the precompiled files, and the packages, none of them worked.  I'd mess with it if I had time but school takes up too much.

Thanks for your help

-Wolvenhaven

---

### Post by TorchlightJay on 2009-03-19
Hey, anyone else having this problem. I am running Intrepid Ibex and my laptop will crash when I plug in power. Now if it is off, and I plug in the power cable, I can fully charge the laptop and then if I boot it without the plug, it'll run until the battery dies. however, if I plug in the power cord (with or without battery inserted), it'll shut itself down within 5-10 minutes. I am not sure if it is the specific laptop or software or whatever. Any ideas?

---

### Post by kashyapatel on 2009-03-27
hello,

I have been trying to get my Hp tx2000's wireless to get working but everytime I have tried it didnt work. I have been to forums/threads and [guides]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver"). but on Step 3 : sudo modprobe ndiswrapper

I get a fatal error message:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrappersudo, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ndiswrapper line 4: ignoring bad line starting with 'b44'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrappersudo, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ndiswrapper line 4: ignoring bad line starting with 'b44'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrappersudo, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ndiswrapper line 4: ignoring bad line starting with 'b44'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrappersudo, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ndiswrapper line 4: ignoring bad line starting with 'b44'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrappersudo, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ndiswrapper line 4: ignoring bad line starting with 'b44'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
Usage: modprobe [-v] [-V] [-C config-file] [-d <dirname> ] [-n] [-i] [-q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
FATAL: Error running install command for ndiswrapper


Can you suggest me how to go through it??

---

### Post by kashyapatel on 2009-03-27
update:

I got it working.dont know how but it did at last..:)
thanks..!!

---

### Post by pooyaplus on 2009-04-19
> **alegir said:**
> Go to System -> Preferences -> Mouse
The try adjusting the sensitivity.

Uhh, that did not solve my problem. I am going to contact the HP customer service to hear their comments too. Will post back the results soon.

---

### Post by ACLBandit on 2009-04-19
> **pooyaplus said:**
> Any one got any idea how on earth I can get rid of these jumps?!:(

I was actually having this problem for a while; it seems to be related to the Wacom, as discussed earlier in the thread (but good luck finding it-- this thread has gotten a little huge). 

The way that I fixed it was to download the newest linux-wacom drivers from [http://linuxwacom.sourceforge.net/;](http://linuxwacom.sourceforge.net/;) after compiling it the same way you do for the other ones, etc., it should stop "jumping." Hope this helps.

---

### Post by wingdom on 2009-04-21
I am new to Ubuntu on this computer, but I am no stranger in trying to get OSX86 to work. I was getting the jumping problem too with OSX. After a couple weeks of dealing with it, the problem started to happen in Windows too (I was dual booting OSX and Vista). Turns out that the problem was hardware, not software, and the only thing that could be done was to send it in and have HP replace the screen.
Now onto my question. I would like to put Ubuntu on my tx2000z, but this thread is huge. Is there some place with a guide to get me up to the current working status, or will I have to go through all the 30 or so pages this thread is currently at?

---

### Post by Favux on 2009-04-21
Hi wingdom,

You didn't say what version of Ubuntu you planned to install.  But this HOW TO should help you get Wacom up and running in Intrepid (maybe Hardy) and Jaunty:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Notice a link to the Rotation HOW TO towards the bottom of the first post.

I hope this is helpful.

---

### Post by wingdom on 2009-04-21
I am going to be installing the most recent version (Intrepid I guess). Thank you for the resources. I will be installing sometime soon. Anything I should worry about thats buried deep in the middle of this thread?

---

### Post by Favux on 2009-04-21
Hi wingdom,

Jaunty is about to be released.  The release candidate for Jaunty is currently out.  But as you can see from the HOW TO's it's a little tricky to set up Wacom currently.  Intrepid might be a little easier except the default linuxwacom 0.8.1-4 that comes with it isn't the best for a TX2000.  That's why the default install on the HOW TO is the production linuxwacom 0.8.2-2.  So either way you end up making changes.

It's always a good idea to read the resources to pick up tips.  But you shouldn't have to do it right away.

---

### Post by pooyaplus on 2009-04-26
Hi,

I guess Wingdom can find almost all the help he needs from the first pages of the current thread.

---

### Post by Favux on 2009-08-07
Hi everyone,

We have auto-magic rotation!  At least in Intrepid and Jaunty.  See HOW TO on post #225 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=23](http://ubuntuforums.org/showthread.php?t=996830&page=23)  Some more info. on the HOW TO on the first page also.

---

### Post by pooyaplus on 2009-08-13
Thanks Favux

Hope it is not the same headache like the previous dists. I will give it a shot and post back the results.

---

### Post by Murphy2712 on 2009-12-26
I don't know what's wrong with Ubuntu 9.10 but I don't have wifi anymore.
modprobe loads ok, but there's no new interface in ifconfig and nothing new in dmesg.
Any help?

---

### Post by pooyaplus on 2010-01-01
Hi Murphy,
I have not upgraded to 9.10 YET! Anyways, could you sort out the problem with the wifi? How other stuff are working(touch, rotation,super key,etc)?

Cheers.

---

### Post by Murphy2712 on 2010-01-21
Ok, so wifi with ndiswrapper doesn't work anymore, but it's now very easy: menu System=>Administration=>Hardware Drivers, then select Wireless Network Driver Broadcom STA, then Activate. That's all!

I've upgraded from 9.04 to 9.10 so maybe it could be different with a clean install.
Works:
- touchscreen with stylus,
- sound/microphone
- hardware keys for volume down-mute-up
- webcam
- bluetooth
- wifi, just install Broadcom STA hardware drivers
- lightscribe, just install drivers/software
- remote/IR
- external screen via VGA, just push Fn+f4
- sd card reader

Doesn't work out of the box:
- touchscreen with finger
- front audio jack, but with some configuration (model=hp) it's ok
- rotation and all 4 blue keys

Don't know because I don't use:
- fingerprint reader

---


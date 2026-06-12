---
title: "HOWTO: ATI Linux Drivers 8.18.6"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by leezer3 on 2005-10-13
Hiya guys,
As per the title- How to get the current ATI drivers working :)

First download them with this command (ATI in thier infinite wisdom have decided not to set the file type correctly, and to put them behind a referrer, so all of this is necessary)
```
wget https://a248.e.akamai.net/f/674/9448/1m/dlmdownloads.ati.com/drivers/linux/ati-driver-installer-8.18.6-i386.run --no-check-certificate --referer www.ati.com
```
Now, run the file with:
```
sudo ./ati-driver-installer-8.18.6-i386.run
```
Tell it to install the driver for the current X server, and let it run :)

Next, we need to re-configure the X-server-
```
sudo dpkg-reconfigure xserver-xorg
```
Select fglrx as opposed to ATI, the rest should be pretty self-explanatory.

**Update- 31st Oct 2005**
If the
```
sudo dpkg-reconfigure xserver-xorg
```
does not get your 3d acceleration working correctly (Should only happen with 'odd' cards), then try it with the ATI utility. For some reason, this is not setup properly when using the driver binary from the site, so you need to install it first, with
```
sudo apt-get install fglrx-control
```
then install the drivers as per above, and run
```
sudo fglrxconfig
```
again, this should be pretty much self-explantaory. Reboot, and hopefully you should now have working 3D acceleration.
Reboot.

That should be it :)

Cheers

-Leezer-

**Last Updated:** 8th November 2005

---

### Post by André on 2005-10-13
Hi,

when i use your HowTo i have some problems.

I ran the installer but when i start the ATI Control i see:

OpenGL vendor string: unavailable
OpenGL renderer string: unavailable
OpenGL version string: unavailable

Any ideas?? glxgears gives me a poor performance but fglrxinfo shows:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)

Calling fgl_glxgears brings up:
root@watson:~# fgl_glxgears
Using GLX_SGIX_pbuffer
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
root@watson:~#                                                  

HELP!! 

Greetings
André

---

### Post by leezer3 on 2005-10-13
Sorry, but I'm not going to be of much help here. The unavailable in the ATI control is normal; The fglrxinfo has changed slightly, and this means that the control can't get what it wants at the mo.
Your fglrxinfo results tell me that the driver is installed, but the errors you have are coming from the driver itself, as opposed to from X etc. 

As your card is on the supported list, this is as far as I can go :(

Sorry

-Leezer-

---

### Post by André on 2005-10-13
Hi,

found the solution via google and want to post it here if other people have the same problem:

[http://wiki.linuxquestions.org/wiki/Installing_ATI_drivers](http://wiki.linuxquestions.org/wiki/Installing_ATI_drivers)

Greetings
André, with decent 3D performance :-)

fgl_glxgears @ 2420 frames in 5.0 seconds = 484.000 FPS

---

### Post by GameManK on 2005-10-13
is this safe to do with the previous version drivers already installed?

---

### Post by jecos on 2005-10-13
[QUOTE=GameManK]is this safe to do with the previous version drivers already installed?[/QUOTE]

You might encounter problems..  remove three packages: fglrx-control,fglrx-driver and linux-restricted-modules with has fglrx.. then install new drivers

You might have to create sym links to fglrx commands or add them to your path..

---

### Post by André on 2005-10-14
If you had the previous from ATI and used their installer for it, then there is a fglrx_uninstall.sh in /usr/share/fglrx.

Maybe you should run this one first.

Greetings
André

---

### Post by zeroverse on 2005-10-14
I am unable to install it at all for some reason

> 08:00:08 (62.98 KB/s) - `ati-driver-installer-8.18.6-i386.run' saved [62368301/62368301]

zeroverse@zeropoint:~$ sudo ./ati-driver-installer-8.18.6-i386.run
Password:
sudo: ./ati-driver-installer-8.18.6-i386.run: command not found


The file IS in my home directory, so it's not that it can't find the file...it just won't process it.  What am I missing?

Any clues?

---

### Post by Cloud[01] on 2005-10-14
is it "executable" ?

chmod +x ./ati-blabla

ciop ciop

---

### Post by leezer3 on 2005-10-14
Sounds like you downloaded the file as root (With sudo?). Change the owner to your user, and then make the file executable before trying again.

Cheers

-Leezer-

---

### Post by allupinya on 2005-10-19
Well i wanta say "Good on ya M8"...For posting this..You are right.
It was a piece of cake..
I used it on my Server and my desktop 
1 Intel and 1 AMD...5 mins. each machine.
After screwing around for three or four days not getting them in . 
To have them go in that easy was almost emberassing..:p
I posted a thread linking back to here hoping to help some of the other poor sod`s get theres going:D ...
The only change i had to make was adding frame buffer= "yes"...
The small loss in "fps", is more then made up for in screen quality

---

### Post by soonindallas on 2005-10-20
many thanks OP for this.  I also had not succeeded until I used this method. like the previous poster i am a little embarassed.  there are 100 ati/fglrx threads on the forums, most of no interest.

---

### Post by Septor on 2005-10-20
People with AMD64 Breezy systems having problems with the ati driver should look at [http://ubuntuforums.org/showpost.php?p=429063&postcount=67](http://ubuntuforums.org/showpost.php?p=429063&postcount=67) for a potential fix.

---

### Post by djpharoah on 2005-10-21
dont know if it should work with mobile chipsets
tried it on my laptop which has a Mobile 7500 video chipset
xorg failed to start
so i had to switch back to "ati"

any idea if mobile chipsets are supported??/

---

### Post by Septor on 2005-10-21
[QUOTE=djpharoah]dont know if it should work with mobile chipsets
tried it on my laptop which has a Mobile 7500 video chipset
xorg failed to start
so i had to switch back to "ati"

any idea if mobile chipsets are supported??/[/QUOTE]

yes mobile chipsets are supported.. but not your 7500.  Use the ati driver for that.  The fglrx driver only supports Radeon 8500 or newer chips.  My Radeon Mobility 9600 works just fine with it.

---

### Post by elephanthunter on 2005-10-23
Fiddlesticks... I followed these instructions and can't run gears. It gives this error message:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32
```

If it helps, my xorg.conf device section for ATI is as follows

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	BusID		"PCI:3:0:0"
EndSection
```

And fglrxinfo outputs

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

...in contrast to the ATI Control Panel

```

OpenGL vendor string: unavailable
OpenGL renderer string: unavailable
OpenGL version string: unavailable
```

---

### Post by Single on 2005-10-23
[QUOTE=zeroverse]I am unable to install it at all for some reason



The file IS in my home directory, so it's not that it can't find the file...it just won't process it.  What am I missing?

Any clues?[/QUOTE]

I encountered the same problem as yours, and I managed to run it with
sudo sh ./ati-driver-installer-8.18.6-i386.run
Hope it helps :smile:

---

### Post by leezer3 on 2005-10-25
Elephant-hunter, try downloading fglrx-control from Synaptic, then reinstall the drivers.
Finally, run fglrxconfig and let this set up your drivers, and see what happens.

Cheers

-Leezer-

---

### Post by elephanthunter on 2005-10-26
[QUOTE=leezer3]Elephant-hunter, try downloading fglrx-control from Synaptic, then reinstall the drivers.
Finally, run fglrxconfig and let this set up your drivers, and see what happens.

Cheers

-Leezer-[/QUOTE]
Thanks :smile: , that seemed to do the trick.

---

### Post by Pettman on 2005-10-31
[QUOTE=allupinya]The only change i had to make was adding frame buffer= "yes"...
The small loss in "fps", is more then made up for in screen quality[/QUOTE]
Add where?

---

### Post by leezer3 on 2005-10-31
You can either add that in the xorg config file, or when using
```
sudo dpkg-reconfigure xserver-xorg
```
say yes when it asks you if you wish to use the kernel framebuffer interface.
On the vast majority of systems, this is not required, but use it if you have bad image quality.

Cheers

-Leezer-

---

### Post by Pettman on 2005-11-01
[QUOTE=leezer3]You can either add that in the xorg config file, or when using
```
sudo dpkg-reconfigure xserver-xorg
```
say yes when it asks you if you wish to use the kernel framebuffer interface.
On the vast majority of systems, this is not required, but use it if you have bad image quality.

Cheers

-Leezer-[/QUOTE]
Tried that, things still lagging like hell.

---

### Post by leezer3 on 2005-11-02
Hiya,
Lagging (In 3d games) is a totally different kettle of fish to bad image quality.
Run fglrxinfo, and post the output of that please.
If it tells you that it is using Mesa indirect or somtheing similar, then do this:
Try downloading fglrx-control from Synaptic, then reinstall the drivers.
Finally, run fglrxconfig and let this set up your drivers, and see what happens.

Cheers

-Leezer-

---

### Post by allupinya on 2005-11-06
Also if i may add another thought..
I play alot of games...I need an constent outlet from working on websites.."LOL":rolleyes: 
On some games, you will see lag in the intros (and sometimes in games) if you are using wine/cedega or other combos..Also in VMware, That can be directly related to memory issues ..Please check those as well.
If you have a fair amount of memory IE: 1gig or more. Try loading 98 or ME in VMware Workstation (latest build) and run your games inside that, in Ubuntu 5.10, It seems to work real well:)  
I love to run windows in linux...It`s like a big cup of coffee:p

---

### Post by gt24 on 2005-11-06
You might think I'm nuts... but I decided to try this on the Live CD.  I have a Radeon 9600.

Follow all the directions in the first post (including the additional bottom section), however when you go to install the drivers you must type sudo sh ./<whatever the program name was>
All default answers work perfectly.  To restart the X Server, hit CTRL-ALT-Backspace...  The OS will then automatically restart the X Server and automatically log you back in.  Once you are back to the destkop, you have your 3d acceleration... and a better idea as to how Ubuntu will run on that system.

Thought that report might help.

<edit> I had to get 3d acceleration working to first off see that it did work and more importantly to see some lovely Xscreensavers gosh darn it!  :) </edit>

---

### Post by lzfy on 2005-11-07
Can someone tell me what my PCI ID is? i have to reinstall Ubuntu because i screw up while configuring X :confused:  now i get a black screen when i boot up, i think i had a wrong value for the PCI ID. My card is a mobile Radeon x700 128MB

thanks

---

### Post by Inspector Hector on 2005-11-07
There is a small typo in the HowTo, it should be

```
sudo apt-get install fglrx-control
```
instead of
```
sudo apt-get fglrx-control
```

just to mentioned it :-)

---

### Post by Septor on 2005-11-07
[QUOTE=lzfy]Can someone tell me what my PCI ID is? i have to reinstall Ubuntu because i screw up while configuring X :confused:  now i get a black screen when i boot up, i think i had a wrong value for the PCI ID. My card is a mobile Radeon x700 128MB

thanks[/QUOTE]

"lspci -v" should show you your video cards PCI ID... might need to run "lspci -n" to get a number though.  For example on one of my machines:
```

# lspci -v
...
0000:01:00.0 VGA compatible controller: nVidia Corporation NV36.2 [GeForce FX 5700] (rev a1) (prog-if 00 [VGA])
        Subsystem: Elsa AG: Unknown device 0f63
        Flags: bus master, 66Mhz, medium devsel, latency 248, IRQ 19
        Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Expansion ROM at f1000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 3.0
...

```
So I see that the video card is on PCI bus 0000:01:00.0.  So now I run "lspci -n" to get the PCI ID for the card:
```

# lspci -n
...
0000:01:00.0 Class 0300: 10de:0342 (rev a1)
...

```

Usually you don't need to specify any of this though... where are you entering this?

---

### Post by leezer3 on 2005-11-08
[QUOTE=Inspector Hector]There is a small typo in the HowTo, it should be

```
sudo apt-get install fglrx-control
```
instead of
```
sudo apt-get fglrx-control
```

just to mentioned it :-)[/QUOTE]

Thanks.

Noted & fixed.

Cheers

-Leezer-

---

### Post by leezer3 on 2005-11-08
[QUOTE=lzfy]Can someone tell me what my PCI ID is? i have to reinstall Ubuntu because i screw up while configuring X :confused:  now i get a black screen when i boot up, i think i had a wrong value for the PCI ID. My card is a mobile Radeon x700 128MB

thanks[/QUOTE]

Hiya,
Did you let the installer autodect your card? - If you did, then the value it entered should be correct.
Most video cards will be found at BUS ID 1, but the integrated Mobility Radeon 9000 was at BUS ID 5 on my laptop.

For anyone else in this situation, there should be no need to reinstall- If the BUS ID is wrong, the the X-Server will be unable to start. Leave it for a few minutes, until it gives you the unable to start X-Server error message, and ok your way out of there. You should then be able to re-run the X-Server configuration, and add in the correct value.

Hope this helps.

-Leezer-

---

### Post by stalefries on 2006-02-03
I need help getting my card to work. First, my card according to lspci:

```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
```


Also, fglrxinfo:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

1, is my card supported?
2, can anyone tell me what I did wrong/do I need to give more info?

Some symptoms. After I reboot, after setting the driver to fglrx, etcetera, it says X cannot be started. I set the driver back to ATI, and startx works.

---

### Post by DoorGunner on 2006-02-03
Hi

your flgrxinfo indicates that the drivers didnt get installed completely......

give this a try....it is by far the best set of instructions out there

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

I would uninstall and start from scratch.....everything you need is in here.

hopefully this helps......

---

### Post by stalefries on 2006-02-03
Thanks. Trying it now.

---

### Post by stalefries on 2006-02-04
Gah! THat didn't work either! I found a thread ([http://ubuntuforums.org/showthread.php?t=7200](http://ubuntuforums.org/showthread.php?t=7200)) that is specifically for my card, but it uses the Mach64 drivers, as opposed to fglrx.

---

### Post by RaptorRaider on 2006-02-04
Why not update this thread to 8.21.7?

Also what if [this]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver") worked? Will using 8.16.8 or 8.21.7 fix a few large bugs?

For example, when I logout of GNOME/KDE or shutdown GNOME/KDE my monitor doesn't display anything; when it goes to let's say GDM I can't do anything because I'm not seeing anything.

---

### Post by RavenOfOdin on 2006-02-05
I followed this HOWTO to the letter, and it did not work. 

What now?

---

### Post by Boston on 2006-02-06
So I installed the lastest ATI drivers (8.16.20) for my ATI Radeon 9700 Mobility. Everything seems to be in order except it changed my screen resolution fro 1920X1200 to 1280X1024. I tried to configure it through System>Preferences>Screen Resolution but 1920X1200 isn't even an option.

How would I go about fixing this?

---

### Post by GazzaK on 2006-04-26
I followed the OP instructions, and the driver seems to work okay (Thanks OP), but on my Laptop has disabled the LCD panel and enabled the monitor out port, so I had to quickly find a CRT screen :) any ideas how to make either or both outputs "live"?

Edit:
Thanks to help from Duwial on the IRC channel, I think I got this working, by running "sudo fglrxconfig" and going through and making best guesses :)

---


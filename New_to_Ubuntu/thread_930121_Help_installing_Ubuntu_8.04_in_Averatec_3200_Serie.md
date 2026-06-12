---
title: "Help installing Ubuntu 8.04 in Averatec 3200 Series laptop"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by pincheLinux on 2008-09-25
Hi. I installed Ubuntu 8.04 on my old Averatec 3200 Series laptop. I used the Alternate CD because the Live CD would send me straight to the command line after I clicked on install. The Alternate CD install ran well but on the first boot I get stuck on "Running local boot scripts (/etc/rc.local)". Previously I tried Fedora 7 on this same laptop and had problems as well - I was sent to command line and could never load GNOME. Could this be related to the video card drivers?

Help?

---

### Post by pytheas22 on 2008-09-25
It could be the video drivers, or maybe something going on with one of the boot scripts.  Do you know exactly what kind of video card is in this machine?

Also, when the system stops booting, if you press control-alt-F2, are you brought to a command prompt where you can log in?

---

### Post by pincheLinux on 2008-09-25
Hi. Thanks for replying. I actually don't know exactly what kind of video card is in this machine. Can I find out in the command line? I found this though, maybe of some help: [http://www.ccs.neu.edu/home/gene/averatec-linux.html#video](http://www.ccs.neu.edu/home/gene/averatec-linux.html#video)

Yes, I do get a command prompt where I can log in if I press control-alt-F2. What does this mean?

---

### Post by oilchangeguy on 2008-09-25
> **pincheLinux said:**
> Hi. I installed Ubuntu 8.04 on my old Averatec 3200 Series laptop. I used the Alternate CD because the Live CD would send me straight to the command line after I clicked on install. The Alternate CD install ran well but on the first boot I get stuck on "Running local boot scripts (/etc/rc.local)". Previously I tried Fedora 7 on this same laptop and had problems as well - I was sent to command line and could never load GNOME. Could this be related to the video card drivers?

Help?

please provide the specs of this computer.

---

### Post by Jive Turkey on 2008-09-25
Type the command

```
lspci
```

after loging in, this should list all of the hardware on the pci bus, including the type of video chip you have post the output here.  

To start a graphical session from a txt only one, try typing:

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
startx
```

in that order.  When you log out it will drop you back to the text session you were in to start x in the first place.  Another possibility would be to ctrl+alt+f7 f7 is the one xserver uses. good luck.

One more thing, the xserver configuration file listed in the article you linked to doesnt exist in ubuntu.  Currently the file of interest is /etc/X11/xorg.conf  That article is either very old or is for a different distro.

you could post the contents of that file too and people might find something for you to change.

---

### Post by pytheas22 on 2008-09-25
Yes, please follow the steps in the post above to see if you can launch a graphical session that way.  If that works, we can figure out why it's not starting automatically.

If you can't start a graphical session, please post any error messages that you get when you try, as well as the output of:
```

lspci -nn
```

(or at least the line in the output that's relevant to your video card...it should be relatively obvious which line that is).

---

### Post by pincheLinux on 2008-09-25
Disclaimer, you're dealing with an absolute beginner here. I've been using PCs for ten years and want to get my feet wet with Linux so I'm installing it in this old Averatec 3200 Series laptop. 

So, that being said, after typing *lspci* I get the following:

> 00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc.VT8237 PCI Bridge
00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0a.0 Cardbus bridge: 02 Micro, Inc. OZ601/6912/711E0 CardBus/SmardCardBus Controller (rev 20)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

And after typing *startx* I get:

> :41 UTC 2008 i686
Build Date: 13 June 2008 01:08:21AM

Module Loader present
(II) Module "i2c" already built-in
(II) Module "ddc" already built-in
(EE) CHROME(0): No valid modes found
(EE) Screen(s) found, but none have a usable configuration.

Fata server error:
no screens found

waiting for X server to begin accepting connections
giving up.
xinit: Connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error.


---

### Post by pytheas22 on 2008-09-25
It seems to think that your xorg.conf file (which governs the graphical display is invalid).  If you type:
```

cat /etc/X11/xorg.conf
```

what is the output (I know that's a lot for you to copy over by hand, but it would be really good to see).

Here are also a couple of things that you can try while waiting for the next response:

1. reconfigure X server by typing:

```
cp /etc/X11/xorg.conf ~/Desktop/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
```

Then reboot.  Any luck?

2. if you press control-alt-F7, are you brought to a command prompt?  If so, what happens if you login there and type:
```

startx
```

---

### Post by pincheLinux on 2008-09-26
Hi pytheas. The X server reconfiguration didn't work. Here's what I get when typing *cat /etc/X11/xorg.conf*

> Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizEdgeScroll" "0"
EndSection

Section "Device"
	Identifier "Configured Video Device"
	Option "UseFBDev" "true"
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
EndSection

Section "Server Layout"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "Synaptics Touchpad"
EndSection

---

### Post by pytheas22 on 2008-09-26
Thanks for typing all that out.

Unfortunately, nothing stands out to me as a problem in xorg.conf, though.  Did you try pressing control-alt-F7 and running 'startx' there?

---

### Post by pincheLinux on 2008-09-26
Well, pressing control-alt-F7 brings me to a screen with the blinking cursor on top, but not logged in. Typing startx there doesn't do anything -- it just moves the cursor down after pressing Enter. I also tried ctrl-alt-f2 to log in, then once logged in try ctrl-alt-F7 but the same happened.

Any other ideas? Is my laptop just not capable of running Ubuntu 8.04?

Thank you for your patience.

---

### Post by pytheas22 on 2008-09-26
The laptop should definitely be able to run Ubuntu.   I think there's just some video issue that you need to get past, but I'm still not certain what it is.

Sorry to still not be able to give you any concrete answer, but what happens if you switch to the control-alt-F7 screen, then press control-alt-backspace?  Or control-C?  If there's a half-alive X server (aka graphical display) running there, which might be what's going on, these commands should kill it and give you a command prompt where you can type 'startx'.

You could also try using an older version of Ubuntu just to see what happens.  If this issue is caused by some peculiarity present only in 8.04, an older version should work.

I did google for your video card and wasn't able to find anyone else who had problems with it on Ubuntu...

---

### Post by pincheLinux on 2008-09-26
Hi pytheas,

Thanks for helping out. When I type ctrl-alt-F7 I go to a screen without login. If I press *control-alt-backspace* there I get
> ^[^H


If I press *control-C* I get
> ^{

I could try installing an earlier version of Ubuntu, but previously I also tried Fedora 7 and 10 and never got a GUI running either.

Any ideas?

---

### Post by pytheas22 on 2008-09-26
It does seem then like some kind of zombified process is running on the control-alt-F7 screen, which would normally host the graphical server.

If you log in (on the control-alt-F2) prompt and type:
```

ps -e | grep X
```

what does it say?

It might also not hurt to try burning an older version of Ubuntu, like 6.06, where the graphical stuff would be different than what it is in modern Ubuntu, to at least see if the live CD works there.  You can download 6.06 by going [here]("http://www.ubuntu.com/getubuntu/downloadmirrors"), choosing a mirror near you, then downloading the ISO.

Also, I have to leave for a trip soon for the weekend so may not be able to respond as quickly as I'd like, but I'll do my best.  I'm sorry this is ending up so complicated, but I'm sure we can figure it out if we try hard enough (you can figure everything in Linux out if you try hard enough...).

EDIT: the suggestions in the post below are also good, particularly the bit about switching to the vesa driver in your "Device" section (vesa is a generic fall-back driver that might work if your VIA drivers are failing).  You can edit your xorg.conf file by typing:

```
sudo nano /etc/X11/xorg.conf
```

That will open the file in a pretty primitive text editor, but it's the best you can do without a graphical interface (unless you know how to use fancy editors like vim or emacs).  The controls for saving the file etc. are displayed at the bottom of the screen.

---

### Post by Jive Turkey on 2008-09-26
OK, try these steps, or skip if you have already done them:
1. Use the verify media utility on your install CD, your cd burner might be the problem if those other distros didn't work also, if it fails check the MD5 of your image or do whatever to get a reliable image without errors.

If that didn't reveal a problem,
2. try editing your xorg.conf file, I think this is where your problem is.  I think you need a "mode:" line in your screen section, the syntax varies between different types of VGA controllers, I don't have a via one.  Find someone who has a VIA video chip and see how the "Device" "Screen" and "Monitor" sections are laid out.  I would edit the Screen section to look like this:
```
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection     "Display"
        Depth       24
        Modes       "1024x768"
    EndSubSection
EndSection

```

Also, the "Device" section usually specifies a driver but yours doesn't
try using this:
```
Section "Device"
Driver    "vesa"
Identifier "Configured Video Device"
Option "UseFBDev" "true"
EndSection
```
until you can figure out what the best driver for your VT83xx chip is.

When you ran```
cp /etc/X11/xorg.conf ~/Desktop/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
``` it should have started an interactive console app that asks you to input parameters for your xorg.config file.  Did you get any of that?

3. Also, try (with a connection to internet) whether step 2 works or not:
```
sudo apt-get install xserver-xorg-video-savage
``` 
and change the Driver in xorg set to "savage"
there are 3 or 4 other via video packages that might drive your chip, I would try each of them, they are "s3virge" "s3" and "via" you probably have all those packages installed already (I do and I have an nvidia chip!), so you could probably try each as the specified driver in xorg.conf.  Make sure to only specify one driver at a time in xorg.conf.  Reboot after changing the xorg.conf file each time.
The names of the packages for the last three drivers I mentioned are xserver-xorg-video-<nameofdriver> I don't think it will hurt anything to install all of them as they dont run unless they are called by xserver AFAIK.  They all (except s3) have man pages you can read by typing "man savage"
If none of that works I don't know what to tell you, you can pm me for clarification on any of this, I can't think of anything else that would help.

---

### Post by pincheLinux on 2008-09-27
**Jive Turkey**, thanks for explaining all that out. Unfortunately none of the above options worked. I checked the install CD for reliability and it is without errors. I edited xorg.conf 
in the "Screen" and "Device" section, rebooted, and same. When I run:

[I]cp /etc/X11/xorg.conf ~/Desktop/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg[/I]

I do get the interactive console app but after completing it nothing is different. Typing *sudo apt-get install xserver-xorg-video-savage* returns "xserver-xorg-video-savage is already the newest version."

Now, **pytheas**, if I type *ps -e | grep X* I actually don't get anything.

Just as a reminder, the problem is that at boot I get stuck on "Running local boot scripts (/etc/rc.local)".

So I installed Ubuntu 6.06 per pytheas' recommendation and it worked. This is how xorg.conf reads from Ubuntu 6.06. Maybe we can take ideas from that configuration and type it in 8.04s? I would really like to have the latest Ubuntu if that is possible. Is it?

> 
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated  Video"
        Driver          "via"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated  Video"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"

                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection


---

### Post by pytheas22 on 2008-09-28
Well it's certainly good news that 6.06 worked--at least we know that your hardware *will* work once it's configured properly.

The first thing to do now would be to copy your xorg.conf from 6.06 (which you pasted in your last post) into your /etc/X11/xorg.conf file on Ubuntu 8.04.  Then log out of the desktop and log back in.  Does 8.04 work then?

If you currently have both 8.04 and 6.06 installed to your hard drive, you could easily overwrite your broken 8.04 xorg.conf from with 6.06--this would save you the trouble of having to copy the file over from hand in nano.  Let me know if you need instructions on how to do that.  There are also other ways to get the file copied over which may be a little trickier but probably still faster (and certainly safer, since it eliminates the possibility of typos) than copying over by hand.  If you tell me which operating systems you currently have on your hard drive, we can figure out the easiest way to get the right values into xorg.conf.  Also let me know if you have an Internet connection on this machine, and whether it's wired or wireless.

---

### Post by pincheLinux on 2008-10-04
Hi Pytheas, thanks for your reply. I'm sorry for the long delay. Busy week. So I only have 6.06 installed (no partition) so I would like to either copy the file to a USB thumbdrive from the laptop to then copy it back after I install 8.04 back. Could you take me through how to do that? Also, I have a Vista PC in the network where I could copy the file as well and then copy back. Could you take me through that as well? I'm an absolute beginner. :(

Thanks!

---

### Post by pytheas22 on 2008-10-04
So you want to make a backup copy of your 6.06 system in case you need to reinstall it later, right?  If so, I've never actually done that myself, but there's a tutorial [here]("http://www.psychocats.net/ubuntu/partimage") that you could follow to easily backup the entire partition, which is the most reliable way to go.  You could also just create a tar.gz archive of your system and restore from that, but that method is not as reliable.

Let me know if the PartImage stuff works for you; if not we can look into other solutions.

---

### Post by pincheLinux on 2008-10-04
Oh, I meant copying just the xorg.conf from 6.06 to a USB, install 8.04 and then copy the xorg.conf on 8.04. Is that possible? If so, what are the command lines (since I won't have GUI on 8.04) to copy xorg.conf from the USB?

---

### Post by pincheLinux on 2008-10-04
Success! Problem solved! I actually found a workaround. From Ubuntu 6.06 I went to System>Administration>Update Manager and there was an option to update to Ubuntu 8.04. I just restarted after updating and the GUI is up and running! Wooohooo!

I'm still curious about learning how to copy from and to a USB drive from the command prompt though. I want to become a Linux geek: learn command lines, install multiple GUIs, program my own apps, customize the system, etc. Can you point me in the right direction to start learning the knots and bolts of Ubuntu/Linux? Thanks for all your help!

---

### Post by pytheas22 on 2008-10-04
I'm glad it's figured out :)  I'm surprised that upgrading all the way from 6.06 to 8.04 went smoothly, but congratulations to you that it did (I've had enough bad experiences using version upgrades that I usually just do a clean install when a new Ubuntu is released).

To copy your xorg.conf file from 6.06 to external media (i.e. your USB drive) would require you first to mount the USB drive using the 'mount' command (normally a device is auto-mounted when you plug it in and you're running Gnome, but this is how you would do it manually from the command line).  You can read how to do that [here]("https://help.ubuntu.com/community/Mount/USB").

Once the device is mounted, you would simply copy your xorg.conf file to it using the 'cp' command (I'll assume in the example below that your USB drive is mounted at /media/external):
```

cp /etc/X11/xorg.conf /media/external
```

To copy the xorg.conf file from 6.06 to 8.04, you would boot to 8.04, mount your USB stick, then use 'cp' again to overwrite 8.04's xorg.conf with the one that you copied out of 6.06:
```

sudo cp /media/external/xorg.conf /etc/X11/xorg.conf
```

As for more information getting started with Ubuntu, there is of course a ton of stuff around the Internet.  A particularly good site for understanding the fundamentals of Ubuntu and getting started with more advanced topics is [http://psychocats.net/](http://psychocats.net/), which is produced by another forum member and is a very well-written and comprehensive guide of many important Ubuntu basics.

---

### Post by pincheLinux on 2008-10-06
Well, actually, funny you mention that because I celebrated prematurely.  Even though the update went fine, now Ubuntu 8.04 doesn't let me connect to the internet either through the Ethernet or Wireless. But I started a new thread for that. See you there!

[http://ubuntuforums.org/showthread.php?t=939988](http://ubuntuforums.org/showthread.php?t=939988)

---

### Post by grover66 on 2008-11-22
To get it working in 8.10, after doing an alternate installation, I used the xorg.conf from the earlier post, but changed the following line in the Device section;

from:
Driver "via"

to:
Driver "openchrome"

...and all is well.

Mike :)

---

### Post by Merus on 2008-12-13
Hello, guys.

I was having this same problem and I edited my xconf as the one for 6.06, like the one mentioned here, and it worked.

I registered here on the forum mainly just to say thank to you all. :)

---

### Post by williamts99 on 2008-12-17
I used the following in my 8.10 /etc/X11/xorg.conf after installing using the alternative CD.  It is now working perfectly, though it might be able to be stripped down even more.

```
Section "Device"
Identifier "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
Driver "openchrome"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"

Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```

---

### Post by bigPoppaJosh on 2008-12-19
Man, I've been struggling with this problem for over a year now (well I gave up a few times) and I recently went back at it (it's the wife's computer and she's not too fond of being stuck with 6.04).  I'm so excited to try the new xorg config when I get home.  I had gotten to the point where (after a few late nights of setting up a PXE server etc to see if the problem was the cdrom) I knew it was the xorg.conf file, but couldn't figure out what to change.  

Thanks very much.  This thread wasn't here last year when I tried this the first time.  For the record, I had exactly the same issues, even to the point where the upgrade from 6.04 to 8.10 then fubar'ed my network connections.

Shouldn't this be an offical bug?  Works in 6.04, not in 7, not in 8.

---

### Post by williamts99 on 2008-12-19
Yes, there are two bugs listed that I have seen for this issue.  Maybe 9.04 will fix it finally :-)

The biggest pain is because the LiveCD doesn't work properly.  That can be fixed too, but it's more difficult.

Now I just have to take mine apart and fix the faulty DC power connector which got hot enough to burn my finger yesterday.

---

### Post by tripslipfall on 2008-12-21
> **williamts99 said:**
> Now I just have to take mine apart and fix the faulty DC power connector which got hot enough to burn my finger yesterday.

Could you help me there?

I have the same problem, and I'm pretty sure it's because it's shorting out, I'm just not positive, it still charges unless you move it the wrong way, it used to not charge at all, then I soldered everything up and it worked great for a few months, now it gets REALLY, and I mean REALLY hot after about 30-60 minutes.

Could you tell me what you did to fix this problem?

And to **bigPoppaJosh**, update to 8.10 from 6.04, then enter the following in the Terminal:

**gksudo gedit /boot/grub/menu.lst **

Then type your password in the box that pops up.

Then add acpi=noirq to the kernel line near the bottom of the page.

title	 Ubuntu 8.10, kernel 2.6.22-14-generic
root	 (hd0,0)
**kernel	 /boot/vmlinuz-2.6.22-14-generic root=UUID=a87de7c0-5109-4808-87e6-2676e4a0e894 ro acpi=noirq quiet splash**
initrd	 /boot/initrd.img-2.6.22-14-generic
quiet

That will fix the wired and wireless networking problems.

---

### Post by williamts99 on 2008-12-22
> **tripslipfall said:**
> Could you help me there?

I have the same problem, and I'm pretty sure it's because it's shorting out, I'm just not positive, it still charges unless you move it the wrong way, it used to not charge at all, then I soldered everything up and it worked great for a few months, now it gets REALLY, and I mean REALLY hot after about 30-60 minutes.

Could you tell me what you did to fix this problem?


I am still in the parts searching phase for mine.  I received the laptop from a customer that didn't want to spend the $ to replace the hard drive, just wanted data recovery.  It had been taken apart, some screws missing, slightly damaged, but for the most part works.  Though it will only charge the battery to about 30% and I have discontinued use of the laptop until I replace the jack and plug.  Just have to decide to spend the $10-15 on new parts, or used parts for $0.

If all of your soldered connections are good(not cold, proper amount), and there are no shorts from too much solder or solder in the wrong place then it is most likely the plug.  The jack and the plug should be replaced at the same time, or the worn out plug can damage the new jack. Looking at mine, both the jack and the plug are quite damaged. I would replace the plug if you haven't and double check on your soldering connections.  Though I doubt that it's your solder connections as you said that it worked great for a few months.

---

### Post by williamts99 on 2008-12-22
> **bigPoppaJosh said:**
> I had gotten to the point where (after a few late nights of setting up a PXE server etc to see if the problem was the cdrom)

Just for future reference, a great way to check the CD-rom drive of the target computer is to do an integrity check using the LiveCD.  The directions are at [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

---

### Post by bigPoppaJosh on 2008-12-22
I would have done that if I had suspected the CD itself, but rather I suspected the CD-ROM drive.

---

### Post by williamts99 on 2008-12-22
Just to clarify a little bit.  Performing the integrity check will fail if it is a bad CD, and it will also fail if the CD-ROM drive can not read the disk(aka faulty drive).  This is why it is a good test for both the CD and the CD-ROM drive.

Best Regards

---

### Post by williamts99 on 2008-12-24
A cut and paste howto(for tejas) for anyone installing on 8.10.

Once installed, you can get to the command line, sign in then issue the following commands:

```
cd /etc/X11/
```

```
sudo mv xorg.conf xorg.original
```

```
sudo wget williamts99.com/xorg.conf
```

Then reboot.

Of course the best is to just copy the xorg.conf I posted above just in case my file is no longer available.

Best Regards

---

### Post by bigPoppaJosh on 2008-12-28
Not if the CD-ROM has issues during the long install process, not the relatively short integrity check.  Thanks for the somewhat obvious tip tho

---

### Post by chrmnxpnoy on 2009-01-11
Okay can someone write all the info in lamens terms for us ubuntu noobs with Averatec 3200s to get ubuntu working properly :D

So far my officially pressed Ubuntu cd does not boot using LiveCD, goes to that Ubuntu@Ubuntu:~$ screen.  

From what I'm reading, I'll need to download the 6.06 release and then do an update to 8.10?  Please help :D

---

### Post by ugm6hr on 2009-01-11
> **chrmnxpnoy said:**
> From what I'm reading, I'll need to download the 6.06 release and then do an update to 8.10?  Please help :D

No.

Download the 8.10 Alternate CD (32-bit / i386).

Then, boot with the ethernet connected to a router that can get online.

Then run the commands as per [post #34]("http://ubuntuforums.org/showpost.php?p=6431814&postcount=34")

Then reboot.

---

### Post by melisandre on 2009-01-11
Hi all;

so, I seem to be having issues with Averatec 3200 as well. I installed 8.10 from the Alternate CD, and it was fine - but when I boot it seems to be "off-centre" and gets stuck - I see the little revolving cursor, which revolves, and then stops.

I can't access command prompt - any ideas? I figure it's something with the video card... (and you know something... Fedora 10, OpenSUSE 11.1, AND Mint 6 all gave essentially the same problem)

Thanks!

---

### Post by ugm6hr on 2009-01-11
Ctrl+Alt+F1 (or F2-F6) should get you to the command line.

---

### Post by melisandre on 2009-01-11
> **ugm6hr said:**
> Ctrl+Alt+F1 (or F2-F6) should get you to the command line.

Nope... not ctl+alt+f1 or f2 or f6 or f2+f6 (:P) worked... It just keeps getting stuck at the "would-be" login screen...

---

### Post by pytheas22 on 2009-01-11
> Nope... not ctl+alt+f1 or f2 or f6 or f2+f6 () worked... It just keeps getting stuck at the "would-be" login screen...

What happens if you press control-alt-backspace?

And to be clear: do you get to point where you can type in your username and password in order to log into Gnome, and then it freezes and you type them in and press enter?  Or does it freeze before the login screen even loads completely?  If the latter, how much of the login screen actually loads before it freezes?  And does your machine freeze totally, or can you still move the mouse?

---

### Post by bigPoppaJosh on 2009-01-11
It's definitely the X11 config, see the previous posts:popcorn:

---

### Post by williamts99 on 2009-01-12
> **melisandre said:**
> Hi all;

so, I seem to be having issues with Averatec 3200 as well. I installed 8.10 from the Alternate CD, and it was fine - but when I boot it seems to be "off-centre" and gets stuck - I see the little revolving cursor, which revolves, and then stops.

I can't access command prompt - any ideas? I figure it's something with the video card... (and you know something... Fedora 10, OpenSUSE 11.1, AND Mint 6 all gave essentially the same problem)

Thanks!


You can use the Recovery Mode to get yourself to a command prompt. [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

Then use the previous instructions to replace your xorg.conf

Best Regards

---

### Post by GapInTheClouds on 2009-01-24
Hi there,

Thanks for solving the Averatec problem. I've been trying to this for ages, but I still hit a snag.

I tried using the alternative CD to install 8.10, but it freezes about 16% into the copying of the files. This has happened three times now and each time I have used a different burned CD.

Next, I tried using the normal install 8.10 install CD and when it failed I used williamts99's xorg.conf file and retried startx and it starts up great :). Then I thought I'd try the install icon that you get on the desktop, but that also freezes (about 22% through). I tried again and the same thing happens.

I'm thinking that maybe the space I have set aside on the hard disk (6GB) might not be big enough. Could that be the case? Otherwise, I was thinking I could try the 'Install inside Windows' option. Does that work very well?

Cheers. Nearly there :)..

---

### Post by pytheas22 on 2009-01-24
> Hi there,

Thanks for solving the Averatec problem. I've been trying to this for ages, but I still hit a snag.

I tried using the alternative CD to install 8.10, but it freezes about 16% into the copying of the files. This has happened three times now and each time I have used a different burned CD.

Next, I tried using the normal install 8.10 install CD and when it failed I used williamts99's xorg.conf file and retried startx and it starts up great . Then I thought I'd try the install icon that you get on the desktop, but that also freezes (about 22% through). I tried again and the same thing happens.

I'm thinking that maybe the space I have set aside on the hard disk (6GB) might not be big enough. Could that be the case? Otherwise, I was thinking I could try the 'Install inside Windows' option. Does that work very well?

Six gigabytes should be fine for installing Ubuntu.  Did you check your CDs for defects?

---

### Post by GapInTheClouds on 2009-01-25
> **pytheas22 said:**
> Six gigabytes should be fine for installing Ubuntu.  Did you check your CDs for defects?

Thanks for that. Yes I checked that and it told me the CD was valid. In the end I converted the free space where I was going to put the Ubuntu partition to ntfs and installed using the 'Inside Windows' option. This seems to work fine, but I've heard that slows down the disk performance. Is that true? If so, I'm thinking that maybe I could 'Install inside Windows' on an existing partition, booting up that Ubuntu and installing in the space I originally set aside. Not quite sure how that would work though..

Maybe I should follow the 'if it ain't broke don't fix it' line of thinking :).

---

### Post by pytheas22 on 2009-01-25
> Thanks for that. Yes I checked that and it told me the CD was valid. In the end I converted the free space where I was going to put the Ubuntu partition to ntfs and installed using the 'Inside Windows' option. This seems to work fine, but I've heard that slows down the disk performance. Is that true? If so, I'm thinking that maybe I could 'Install inside Windows' on an existing partition, booting up that Ubuntu and installing in the space I originally set aside. Not quite sure how that would work though..


Yes, installing via [wubi]("http://wubi-installer.org/") (the 'Inside Windows' option) will generally give slightly slower performance, but only because NTFS file systems are prone to fragmentation, which makes disk access slower.  Unless your file system becomes super-fragmented, it shouldn't be too much of a problem.

You can, however, [move the wubi disk image]("http://ubuntuforums.org/showthread.php?t=438591") to a dedicated ext3 partition if you want to be adventurous.

---

### Post by aeb1 on 2009-01-25
> **pytheas22 said:**
> Thanks for typing all that out.

Unfortunately, nothing stands out to me as a problem in xorg.conf, though.  Did you try pressing control-alt-F7 and running 'startx' there?

Sigh, I'm NOT a newbie to UNIX/Linux. I just happen to be running through the configuration of an Averatec 3280 ( 3270-EH1 ) as we speak.

First of all, the UniChrome setting out of the box DOES NOT WORK reliably on this model! Yah, I'll get around to sending a bug report when I am done...

BUT, to get (K)UBUNTU running on this system, I had to force VESA drivers into the xorg.config under the generic output the xfix command gives you in recovery mode.

Boot into recovery mode.

Run xfix FIRST; that will get you into a GENERIC xorg.conf

Reboot and go into the root shell.

Then type

nano /etc/X11/xorg.conf

Scroll down to Section Device

Under 

Identifier       " Configured Video Device "

add the line

Driver      "vesa "


Than type ^O and ^X to get back to the root prompt.

Reboot the system and you should get a display.

I live dangerously, I didn't back up my xorg.conf file. People really ought to before ANY " Brain Surgery " of this type..

The CLI WAS the only way we drove UNIX, X was a PITA to work with.

---

### Post by aeb1 on 2009-01-25
> **aeb1 said:**
> Sigh, I'm NOT a newbie to UNIX/Linux. I just happen to be running through the configuration of an Averatec 3280 ( 3270-EH1 ) as we speak.

First of all, the UniChrome setting out of the box DOES NOT WORK reliably on this model! Yah, I'll get around to sending a bug report when I am done...

BUT, to get (K)UBUNTU running on this system, I had to force VESA drivers into the xorg.config under the generic output the xfix command gives you in recovery mode.

Boot into recovery mode.

Run xfix FIRST; that will get you into a GENERIC xorg.conf

Reboot and go into the root shell.

Then type

nano /etc/X11/xorg.conf

Scroll down to Section Device

Under 

Identifier       " Configured Video Device "

add the line

Driver      "vesa "


Than type ^O and ^X to get back to the root prompt.

Reboot the system and you should get a display.

I live dangerously, I didn't back up my xorg.conf file. People really ought to before ANY " Brain Surgery " of this type..

The CLI WAS the only way we drove UNIX, X was a PITA to work with.

More information: 

When I got into Kubuntu, I used the System Settings to install the VIA display driver... UNICHROME was unstable in my system ( the W2000 side IS stable, though ) 

I also changed the display to the generic 1024x768 LCD display..

Now to load the other fun stuff, like the KRELL monitor...

---

### Post by zrockstar on 2009-02-09
Guys thank you so much for this thread, it saved me a lot of time and headache. I was just wondering now what you guys with the 3200s did to get your wireless up and running? Mine sees my router, tries to connect, then just says disconnected. Anyone experiencing the same issues?

---

### Post by pytheas22 on 2009-02-09
> Guys thank you so much for this thread, it saved me a lot of time and headache. I was just wondering now what you guys with the 3200s did to get your wireless up and running? Mine sees my router, tries to connect, then just says disconnected. Anyone experiencing the same issues?

I don't have this laptop, but if you tell me the output of the following commands I'll try to help you get connected:
```

lspci -nn
sudo iwlist scan
uname -rm
```

Also, you may have better luck connecting with [wicd]("http://wicd.sourceforge.net") than Network Manager.

---

### Post by zrockstar on 2009-02-09
Thanks for offering to help. After I rebooted, it actually connected, but signal strength is really low. My desktop in the same room has full strength. Any ideas? Thanks.

---

### Post by pytheas22 on 2009-02-09
zrockstart: there could be various causes for a flaky connection.  Please post the output of:
```

lspci -nn
sudo iwlist scan
uname -rm
lshw -C Network
dmesg | tail -40
ping -c 10 google.com
```

With that information we should be able to come up with some potential solutions.

---

### Post by GapInTheClouds on 2009-02-12
> **pytheas22 said:**
> Yes, installing via [wubi]("http://wubi-installer.org/") (the 'Inside Windows' option) will generally give slightly slower performance, but only because NTFS file systems are prone to fragmentation, which makes disk access slower.  Unless your file system becomes super-fragmented, it shouldn't be too much of a problem.

You can, however, [move the wubi disk image]("http://ubuntuforums.org/showthread.php?t=438591") to a dedicated ext3 partition if you want to be adventurous.

Thanks for that. I went for the adventurous option and now it is on its own partition. Also quite a lot faster, I must say :).

Now as zrockstar describes, I also have the wireless being slow and sometimes disconnecting, which sounds like the same thing. Even though it should be connecting at 54Mbps (works in windows; downloads at 800kB/s), it seems to only manage 1Mbps (downloads at 30kB/s). I'm using WPA and thought it might be related to that, but WEP has the same thing. So I've taken the liberty of posting the rather LARGE output to your commands from post #53.

Hope you can help.

```
hugo@crazy-mac:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge [1106:3205]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:09.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
00:0a.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] [1106:7205] (rev 01)
hugo@crazy-mac:~$ sudo iwlist scan
[sudo] password for hugo: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:3F:3F:A8:32
                    ESSID:"SKY75616"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/100  Signal level:-72 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000032b53ce1b7
                    Extra: Last beacon: 668ms ago
          Cell 02 - Address: 00:1D:68:EC:8F:B9
                    ESSID:"klaus-wifi"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/100  Signal level:-48 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000001d661986
                    Extra: Last beacon: 368ms ago
          Cell 03 - Address: 00:1B:2F:A3:0C:38
                    ESSID:"Tea and Oranges"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/100  Signal level:-77 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000019b0507e427
                    Extra: Last beacon: 48ms ago

pan0      Interface doesn't support scanning.

hugo@crazy-mac:~$ uname -rm
2.6.27-11-generic i686
hugo@crazy-mac:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wmaster0
       version: 01
       serial: 00:11:09:09:22:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.64 latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:19:c7:d0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:e2:d4:41:9d:67
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
hugo@crazy-mac:~$ dmesg | tail -40
[  653.946234] wlan0: AP denied association (code=12)
[  654.149214] wlan0: associate with AP 00:1d:68:ec:8f:b9
[  654.151498] wlan0: RX AssocResp from 00:1d:68:ec:8f:b9 (capab=0x411 status=12 aid=0)
[  654.151525] wlan0: AP denied association (code=12)
[  654.348222] wlan0: association with AP 00:1d:68:ec:8f:b9 timed out
[  654.682659] wlan0: authenticate with AP 00:1d:68:ec:8f:b9
[  654.684713] wlan0: authenticated
[  654.684745] wlan0: associate with AP 00:1d:68:ec:8f:b9
[  654.689356] wlan0: RX AssocResp from 00:1d:68:ec:8f:b9 (capab=0x411 status=12 aid=0)
[  654.689389] wlan0: AP denied association (code=12)
[  654.884081] wlan0: associate with AP 00:1d:68:ec:8f:b9
[  654.886174] wlan0: RX AssocResp from 00:1d:68:ec:8f:b9 (capab=0x411 status=12 aid=0)
[  654.886184] wlan0: AP denied association (code=12)
[  655.084115] wlan0: associate with AP 00:1d:68:ec:8f:b9
[  655.086251] wlan0: RX AssocResp from 00:1d:68:ec:8f:b9 (capab=0x411 status=12 aid=0)
[  655.086258] wlan0: AP denied association (code=12)
[  655.284146] wlan0: association with AP 00:1d:68:ec:8f:b9 timed out
[  664.532337] wlan0: authenticate with AP 00:1d:68:ec:8f:b9
[  664.532389] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  664.534847] wlan0: authenticated
[  664.534855] wlan0: associate with AP 00:1d:68:ec:8f:b9
[  664.534861] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[  664.539779] wlan0: authenticate with AP 00:1d:68:ec:8f:b9
[  664.543778] wlan0: authenticated
[  664.543795] wlan0: associate with AP 00:1d:68:ec:8f:b9
[  664.546068] wlan0: RX AssocResp from 00:1d:68:ec:8f:b9 (capab=0x411 status=12 aid=0)
[  664.546078] wlan0: AP denied association (code=12)
[  664.740072] wlan0: associate with AP 00:1d:68:ec:8f:b9
[  664.749309] wlan0: RX AssocResp from 00:1d:68:ec:8f:b9 (capab=0x411 status=12 aid=0)
[  664.749322] wlan0: AP denied association (code=12)
[  664.944101] wlan0: associate with AP 00:1d:68:ec:8f:b9
[  664.956071] wlan0: RX AssocResp from 00:1d:68:ec:8f:b9 (capab=0x411 status=12 aid=0)
[  664.956085] wlan0: AP denied association (code=12)
[  665.147267] wlan0: association with AP 00:1d:68:ec:8f:b9 timed out
[  673.603451] wlan0: authenticate with AP 00:1d:68:ec:8f:b9
[  673.604994] wlan0: authenticate with AP 00:1d:68:ec:8f:b9
[  673.605597] wlan0: authenticated
[  673.605624] wlan0: associate with AP 00:1d:68:ec:8f:b9
[  673.609543] wlan0: RX AssocResp from 00:1d:68:ec:8f:b9 (capab=0x411 status=0 aid=1)
[  673.609572] wlan0: associated
hugo@crazy-mac:~$ ping -c 10 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=244 time=151 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=244 time=117 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=244 time=115 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=4 ttl=244 time=114 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=5 ttl=244 time=114 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=6 ttl=244 time=118 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=7 ttl=244 time=115 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=8 ttl=244 time=118 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=9 ttl=244 time=119 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=10 ttl=244 time=115 ms

--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9037ms
rtt min/avg/max/mdev = 114.278/120.107/151.498/10.618 ms
hugo@crazy-mac:~$ 


```

---

### Post by pytheas22 on 2009-02-12
GapInTheClouds: there's an older but stabler version of the driver for your card (rt2500) that may work better.  To give it a try, run these commands:
```

sudo apt-get install rutilt build-essential
wget http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz
tar -xzvf rt2500-cvs-daily.tar.gz
cd rt2500*/Module
make
sudo make install
echo rt2500 | sudo tee -a /etc/modules
sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
exit
```

Then reboot for the changes to take effect.  The one caveat to this is that you can't connect with Network Manager; instead, you have to use a utility called 'Rutilt Wlan Manager' (which will be installed by the commands above).  You can find it under the System>Administration menu.  Please use that utility to connect.

Is the connection any better (if not, it's easy enough to revert to driver you're currently using)?

---

### Post by GapInTheClouds on 2009-02-12
> **pytheas22 said:**
> Is the connection any better (if not, it's easy enough to revert to driver you're currently using)?

Thanks, pytheas22. That worked a treat! Now browsing at full speed :). Cheers and good ubuntuing.

Although, I've just spotted that now I can't use the VPN fuction because the network manager doesn't think I'm connected.. Any ideas?

---

### Post by GapInTheClouds on 2009-02-12
> **pytheas22 said:**
> Yes, installing via [wubi]("http://wubi-installer.org/") (the 'Inside Windows' option) will generally give slightly slower performance, but only because NTFS file systems are prone to fragmentation, which makes disk access slower.  Unless your file system becomes super-fragmented, it shouldn't be too much of a problem.

You can, however, [move the wubi disk image]("http://ubuntuforums.org/showthread.php?t=438591") to a dedicated ext3 partition if you want to be adventurous.

PS: I just remembered that the transfer went fine, except I had to change the boot manager. I had to tell it to look at (hd0,5) instead of ()/ubuntu/disk.

---

### Post by pytheas22 on 2009-02-12
Good to hear that driver works better.

I'm afraid I don't know of a good solution for the VPN issue.  Rutilt doesn't have any VPN plugins like the ones for Network Manager.  The only solution I know is to use a command-line VPN client.  Depending on which kind of VPN protocol you use, you may or may not already have the client installed.  Do you know which protocol you need (Cisco, OpenVPN...)?

You could also try connecting to your network with NetworkManager just to see what happens, but as I recall, this never works with the legacy rt2500 driver.  On the other hand, I haven't tried it since Ubuntu 7.10.

---

### Post by zrockstar on 2009-02-22
Pytheas,

Thank you for the help in the previous post, sorry I couldn't get my results up, I was out of town, but I did do what your suggested for Gap, and now I can not connect at all. Well actually, I think it connects, but does not resolve an IP. This is the same thing that happened with the regular wireless client before I got WCid. I know my router is Linux compatable, so there is something going on inside the machine. Any ideas on what it could be? Thanks.

Z

---

### Post by pytheas22 on 2009-02-22
zrockstar: maybe it's a DNS issue, which is easy to fix.  Please post the output of these commands after you're connected (as far as you know) to your wireless network:
```

cat /etc/resolv.conf
ifconfig
ping -c 5 google.com
ping -c 5 74.125.67.100
```

---

### Post by zrockstar on 2009-02-22
Thanks Pytheas, here we go:


zrockstar@ubuntu:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
zrockstar@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:45:25:9c:da  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:45ff:fe25:9cda/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1342044 (1.3 MB)  TX bytes:239038 (239.0 KB)
          Interrupt:11 Base address:0xae00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5814 (5.8 KB)  TX bytes:5814 (5.8 KB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:ae:e5:94  
          inet6 addr: fe80::211:9ff:feae:e594/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:13 txqueuelen:1000 
          RX bytes:6819303 (6.8 MB)  TX bytes:312786 (312.7 KB)
          Interrupt:11 Base address:0xc000 

ra0:avahi Link encap:Ethernet  HWaddr 00:11:09:ae:e5:94  
          inet addr:169.254.8.166  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xc000 

zrockstar@ubuntu:~$ ping -c 5 google.com
ping: unknown host google.com
zrockstar@ubuntu:~$ ping -c 5 74.125.67.100
PING 74.125.67.100 (74.125.67.100) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=1 Destination Host Unreachable
From 192.168.1.6 icmp_seq=2 Destination Host Unreachable
From 192.168.1.6 icmp_seq=3 Destination Host Unreachable
From 192.168.1.6 icmp_seq=4 Destination Host Unreachable
From 192.168.1.6 icmp_seq=5 Destination Host Unreachable

--- 74.125.67.100 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4046ms
, pipe 3

---

### Post by pytheas22 on 2009-02-22
It looks like you weren't connected wirelessly at all--I was thinking you were connected but couldn't resolve domain names.  So I understand the issue better now.

Which program are you using to connect?  You should be using Rutilt, which you can install by typing 'sudo apt-get install rutilt'.  Then launch it from System>Administration>Rutilt WLAN Manager.  wicd and Network Manager probably won't be able to connect you.

You may also need to tell Rutilt to use dhcp (I'm not positive though because I haven't used it in a long time).  You won't receive an IP address without dhcp.  If it doesn't ask you outright if you want to use dhcp, look around the settings for an option to specify it.  If you still can't figure it out, let me know and I'll get a screenshot.

It would also be helpful to see any exact error messages that you get from Rutilt, as well as the output of:
```

lshw -C Network
lsmod | grep rt
```

---

### Post by zrockstar on 2009-02-22
I am running Rutilt, and installed it as recommended, here is the output:

```
zrockstar@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: ra0
       version: 01
       serial: 00:11:09:ae:e5:94
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 latency=32 module=rt2500 multicast=yes wireless=RT2500 Wireless
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:25:9c:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.6 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f6:eb:8d:8b:15:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
zrockstar@ubuntu:~$ lsmod | grep rt
parport_pc             39204  0 
parport                42604  3 ppdev,parport_pc,lp
gameport               19468  1 snd_via82xx
snd_mpu401_uart        15360  1 snd_via82xx
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd                    63268  18 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                42184  2 drm,via_agp
rt2500                189664  1 
```

---

### Post by pytheas22 on 2009-02-22
hmmm, everything looks good there.  Did you look for a dhcp option in Rutilt?  What happens if you connect in Rutilt, then type this command:
```

sudo dhclient ra0
```

That should get you an IP manually.

---

### Post by zrockstar on 2009-02-22
```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:11:09:ae:e5:94
Sending on   LPF/ra0/00:11:09:ae:e5:94
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleepi
```ng.

---

### Post by pytheas22 on 2009-02-22
Sorry it's still not working, but we'll get there.  Could you please post the output of:
```

iwconfig
```

after you've connected to the network in Rutilt?

Also, did you get a chance to look for any settings in Rutilt related to dhcp?

---

### Post by zrockstar on 2009-02-22
Yes, the auto dhcp box was checked. Rutilt never actually connects to the network. I it shows signal strength and everything, but IP is N/A. It doesn't give me any errors about the password or that it can't resolve IP or anything. It just doesn't get one.

---

### Post by zrockstar on 2009-02-22
```
zrockstar@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"ZACNET"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1F:33:24:92:7D   
          Bit Rate=54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=79/100  Signal level:-45 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by pytheas22 on 2009-02-23
Will it connect if you turn off the security on your network?  What kind of encryption are you using?

---

### Post by Geryon on 2009-02-26
Hey guys,  I have everything working just fine on my Averatec these days.  Wireless works, video works, etc..  I installed 6.06 and upgraded to 8.04.  Which promptly killed my wireless.  The solution for this is to set your xorg as follows:

```

Section "Device"
       Identifier      "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
       Driver          "via"
       Option          "DisableIRQ"

       BusID           "PCI:1:0:0"
EndSection

```
After this the wireless works but it drops tons of packets.  This is due to an older, buggy driver in the kernel.  So the next step is to download the latest driver from RA Tech.  It can be downloaded from here:

[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

Grab the latest CSV for the 2500 and compile it.  A simple make, make install does the trick.  It will replace the existing one.  Then just reboot and everything should be set.  

My only remaining "problems" are my CD/DVD drive randomly panics the kernel if I copy a lot of data from it and my 3D worked better in 6.06 than it works in 8.04.  It appears to corrupt the display quite a bit.  As of now I have it hooked up to an external display running beautifully at 1680x1050 with the wireless pushing over 2MB/s throughput.

---

### Post by pytheas22 on 2009-02-26
**Geryon**: thanks for the information.  Regarding the wireless, the only thing I'd add is that you need also to blacklist the default drivers that Ubuntu uses in order for the rt2500 driver from serialmonkey to take effect.  The commands for blacklisting these drivers (as well as for downloading and compiling the rt2500 driver from serialmonkey) are available in post #55.

**zrockstar**: did you ever get your wireless going?  Because I was thinking the other day that if the serialmonkey driver won't work for you for some reason, we could ndiswrapper instead; it would probably work.

---

### Post by shadowjack1 on 2009-02-28
Thank you williamts99. I was following this thread after encountering the same problem installing 8.10 on an Averatec 3200, the install would always fail with the liveCD. Was wondering if the DVD drive was flakey, then noticed that one of the options in the bios boot order was 'boot from usb external drive'. Booted the alternateCD from an external drive, let it install and fail on reboot, then followed your instructions per #34. Works perfectly. Ended 4 days of newB frustration. Again, thanks

---

### Post by bdmp on 2009-04-01
> **williamts99 said:**
> A cut and paste howto(for tejas) for anyone installing on 8.10.

Once installed, you can get to the command line, sign in then issue the following commands:

```
cd /etc/X11/
```

```
sudo mv xorg.conf xorg.original
```

```
sudo wget williamts99.com/xorg.conf
```

Then reboot.

Of course the best is to just copy the xorg.conf I posted above just in case my file is no longer available.

Best Regards

I love you! Thanks so much! You saved my life!

---

### Post by bdmp on 2009-04-01
> **GapInTheClouds said:**
> Hi there,

Thanks for solving the Averatec problem. I've been trying to this for ages, but I still hit a snag.

I tried using the alternative CD to install 8.10, but it freezes about 16% into the copying of the files. This has happened three times now and each time I have used a different burned CD.

Next, I tried using the normal install 8.10 install CD and when it failed I used williamts99's xorg.conf file and retried startx and it starts up great :). Then I thought I'd try the install icon that you get on the desktop, but that also freezes (about 22% through). I tried again and the same thing happens.

I'm thinking that maybe the space I have set aside on the hard disk (6GB) might not be big enough. Could that be the case? Otherwise, I was thinking I could try the 'Install inside Windows' option. Does that work very well?

Cheers. Nearly there :)..

This is because it heats up and crashes. Put it up so air can flow and put a fan on it and it will work.

---

### Post by GapInTheClouds on 2009-05-02
> **williamts99 said:**
> A cut and paste howto(for tejas) for anyone installing on 8.10.

Once installed, you can get to the command line, sign in then issue the following commands:

```
cd /etc/X11/
```

```
sudo mv xorg.conf xorg.original
```

```
sudo wget williamts99.com/xorg.conf
```

Then reboot.

Of course the best is to just copy the xorg.conf I posted above just in case my file is no longer available.

Best Regards

Hello again,

Just upgraded to Ubuntu 9.04 and had similar problems as when I installed 8.10 when the graphics wasn't working. I just tried using the xorg.conf file from williamts99 from the previous time and it doesn't see to work this time. Stuck in the terminal :confused:. Any ideas?

Cheers.

---

### Post by GapInTheClouds on 2009-05-02
> **bdmp said:**
> This is because it heats up and crashes. Put it up so air can flow and put a fan on it and it will work.

Yes thanks for that. I've been practicing the stand-it-on-its-end for the last year mainly for Windows because it seems to always be using the CPU! In the end I got the installation to work via 'Installing inside Windows' and its worked ever since.. until I installed 9.04 (see previous post).

---

### Post by pytheas22 on 2009-05-02
> Just upgraded to Ubuntu 9.04 and had similar problems as when I installed 8.10 when the graphics wasn't working. I just tried using the xorg.conf file from williamts99 from the previous time and it doesn't see to work this time. Stuck in the terminal . Any ideas?

Log in on the command line and type:
```

startx
```

It will try to start the graphical server, then fail.  Towards the end of the output, you should see a reason given for why it failed--it will probably say something like *Fatal X Error: No Screens Found*, for example.  What is the error message?

---

### Post by GapInTheClouds on 2009-05-04
> **pytheas22 said:**
> Log in on the command line and type:
```

startx
```

It will try to start the graphical server, then fail.  Towards the end of the output, you should see a reason given for why it failed--it will probably say something like *Fatal X Error: No Screens Found*, for example.  What is the error message?

Hi pytheas22,

Yes, when I execute startx it lists lots of stuff that ends in:
```

(EE) CHROME(0): No valid modes found
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

I'm using williamts99's xorg.conf file. Thanks for helping :).

---

### Post by pytheas22 on 2009-05-04
I helped someone last week who was getting the same errors trying to start X on Ubuntu 9.04 using a VIA Chrome video card.  Apparently there's a bug with the chrome driver.  You can fix it (hopefully) by running these commands, which will compile and install a better driver:
```

sudo apt-get install build-essential subversion autoconf automake1.9 libtool
sudo apt-get build-dep xserver-xorg-video-openchrome
svn checkout http://svn.openchrome.org/svn/trunk openchrome
cd openchrome*/src
wget http://launchpadlibrarian.net/24709429/km400_panel.patch
patch -p1 < km400_panel.patch
cd ..
./autogen.sh --prefix=/usr
make
sudo make install
sudo dpkg-reconfigure -phigh xserver-xorg
```

(You will need to have an Internet connection to download the code; to get connected via etherent from the command-line, type 'sudo ifconfig eth0 up; sudo dhclient eth0'.)

Then reboot your machine.  Does X start?

(I got most of this from [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=852101&page=4").)

---

### Post by GapInTheClouds on 2009-05-06
> **pytheas22 said:**
> 
```

sudo apt-get install build-essential subversion autoconf automake1.9 libtool
sudo apt-get build-dep xserver-xorg-video-openchrome
svn checkout http://svn.openchrome.org/svn/trunk openchrome
cd openchrome*/src
wget http://launchpadlibrarian.net/24709429/km400_panel.patch
patch -p1 < km400_panel.patch
cd ..
./autogen.sh --prefix=/usr
make
sudo make install
sudo dpkg-reconfigure -phigh xserver-xorg
```

(I got most of this from [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=852101&page=4").)

Hi pytheas,

Thanks for that. It worked a treat using an ethernet connection :). Only thing I had to do was re-compile the rt2500 drivers and now I'm back as I was with new shiny Jaunty!

Cheers.

---

### Post by ctsdownloads on 2009-09-26
N/m

---


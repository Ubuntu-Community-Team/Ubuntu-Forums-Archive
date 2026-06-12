---
title: "[SOLVED] How do I install drivers for my VIA graphics card?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by simontaylor on 2008-06-15
Using onboard VGA Integrated VIA ProSavage8 Graphics, I've noticed that moving image and graphics playback is below par and recently, with the excellent guidance of alienexplorers I've edited my xorg.conf file to push the refresh rate for my monitor up to 70 Hz without noticeable effect.

Do you know how I install the drivers for my VIA graphics card?

Help would be greatly appreciated.

Yours,

Simon Taylor

---

### Post by JoshuaRL on 2008-06-15
First off, what version of Ubuntu are you running?

And what does it say in Screens and Graphics as far as the current video driver?

---

### Post by simontaylor on 2008-06-15
I'm running Hardy Heron 8.04... forgive me, but where is Screens and Graphics?

simon

---

### Post by JoshuaRL on 2008-06-15
I believe it's System->Settings.  If not, try Administration.

---

### Post by RomeReactor on 2008-06-15
> **simontaylor said:**
> I'm running Hardy Heron 8.04... forgive me, but where is Screens and Graphics?

simon

Hi. If you can't find it where JoshuaRL suggests, it may be located in 'Applications->Other->Screens and Graphics'. If you can't see the 'Other section of the Applications menu, you can enable it by right-clicking in the menus and selecting 'Edit menus'.

You can also launch it from the terminal (Applications->Accessories->Terminal) or by pressing ALT+F2 and write or paste:
```
gksudo displayconfig-gtk
```

Regarding your VIA gpu, it's very likely that you won't get more performance out of it than what it is currently giving you.

---

### Post by simontaylor on 2008-06-15
nearest relevant category: System>Administration>Hardware Drivers but this is for thirdparty/proprietary... and the only driver listed is for Atheros... my LAN. 

Looked through Hardware Testing which links up with Launchpad but it does not give details. You'd think I could access the details via Launchpad or some other local... there is a way, isn't there?

simon

---

### Post by simontaylor on 2008-06-15
Screens and Graphics - thanks for those tips RomeReactor - identifies the card as S3 Savage 4 and lists the drivers as "none"!

The running specs: 1280 x 960 @ 60 Hz

the reason I'm looking to install drivers for VIA is to increase refresh rate to 70 Hz.

thanks,
simon

---

### Post by RomeReactor on 2008-06-15
Make sure the necessary driver is already installed; please post the output of:
```
cat /etc/X11/xorg.conf | grep Driver
```

Also, search in Synaptic (System->Administration->Synaptic) for **xserver-xorg-video-savage**, which I think is the driver you want. If it's already installed, you can select it in Screens and Graphics.

---

### Post by simontaylor on 2008-06-15
I completed the tasks you suggested in reverse order... in order to establish that the "necessary driver is already installed" ... 

Yes, xserver-xorg-video-savage is already installed. I re-installed it to be safe. Then I went to Screens and Graphics and where it said driver "none" I changed it to S3 Savage 4 from the menus provided. It asked me to log off - along with all users. This I did, rebooting, to discover the black wall of blankness for the third time today!

Recovery mode, Xserver repair and I'm running again. (monitor is now listed as "plug-and-play"!)

> simon@simon-desktop:~$ cat /etc/X11/xorg.conf | grep Driver
	Driver		"kbd"
	Driver		"mouse"
simon@simon-desktop:~$ 

What does this mean?

simon

---

### Post by alienexplorers on 2008-06-16
Simon,
He wants you to list the video (configured video) section of your xorg.conf file. Run in terminal Cat/etc/X11/xorg.conf.  Copy and paste the whole thing here.
Donald

---

### Post by Victormd on 2008-06-16
type this in a terminal and see if it lists the proper graphics card (post the output):
```
lspci | grep VGA
```

---

### Post by simontaylor on 2008-06-16
I hope this is what was being requested. cat/etc/... when run in terminal came back with a no directory reply.

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier 	"Monitor0"
	VendorName 	"Philips"
	ModelName 	"107S21"
	HorizSync 	30 - 71
	VertRefresh 	50.0 - 160.0
	Option 		"DPMS"
	Modeline 	"1280x1024_70.00" 128.94 1280 1368 1504 1728 1024 1025 1028 1066 -HSync +Vsync
EndSection 

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

simon

---

### Post by simontaylor on 2008-06-16
Hi Victormd,

> simon@simon-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

which would seem to indicate I'm running with the correct drivers, no? which would further seem to suggest the news is all bad for higher performance. No?

simon

---

### Post by alienexplorers on 2008-06-16
simon,
now print out in terminal:
> lspci | grep VGA

---

### Post by simontaylor on 2008-06-16
Hi Victormd,

> simon@simon-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

which would seem to indicate I'm running with the correct drivers, no? which would further seem to suggest the news is all bad for higher performance. No?

simon

---

### Post by RomeReactor on 2008-06-16
Try this:
```
sudo lshw -C display
```
and paste the whole output; it should include which driver it's currently using.

As I said earlier, it's likely you won't get much of a performance boost out of that card; VIA integrated video solutions have somewhat limited capabilities.

---

### Post by simontaylor on 2008-06-16
Here's the output:

> *-display               
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: driver=prosavage_smbus latency=64 maxlatency=255 mingnt=4 module=i2c_prosavage


---

### Post by simontaylor on 2008-06-16
Thanks for looking, RomeReactor: I don't want a huge boost in performance, just something above the refresh rate I'm getting now. Used to run the same card with XP and it could handle much higher Hz rates. Is this one of those Linux peculiarities? Albeit that I wouldn't consider going back to microsoft.

best,

simon

---

### Post by alienexplorers on 2008-06-16
Hi Simon,  Put this in your "Device" section of xorg.conf:

> Section "Device"
    Identifier  "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
    Driver      "savage"
    BusID       "PCI:1:0:0"
    Option      "UseFBDev"      "true"
EndSection


---

### Post by alienexplorers on 2008-06-16
Change the mode line to:
> Modeline "1024x768_70.00"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync

Looked at the specs for your monitor and this is the highest resolution you can use with 70Hz.

Save xorg.conf and reboot.....

---

### Post by RomeReactor on 2008-06-16
> **simontaylor said:**
> Thanks for looking, RomeReactor: I don't want a huge boost in performance, just something above the refresh rate I'm getting now. Used to run the same card with XP and it could handle much higher Hz rates. Is this one of those Linux peculiarities? Albeit that I wouldn't consider going back to microsoft.

best,

simon

It's been a while since I've used a VIA gpu in Linux, but the drivers available for them rarely offer anything beyond the most basic functionality; as an example, many VIA gpus won't run desktop effects or 3D games in Linux, even if they are capable of it in windows.

In [this thread]("http://ubuntuforums.org/showthread.php?t=742895"), PmDematagoda suggests using the OpenChrome driver for your card. Maybe you could give it a try.

---

### Post by eeried on 2008-06-16
> Change the mode line to:

Modeline "1024x768_70.00" 76.16 1024 1080 1192 1360 768 769 772 800 -HSync +Vsync 

Can't this be dangerous?

I'd like to make the same video card display over 1024X768 on a 20" LCD screen. Xorg.conf has changed or rather xserver-xorg. You can't run dpkg to chnage your card or resolution and editing the xorg.conf can be tricky.

---

### Post by alienexplorers on 2008-06-16
I run 1280x1024x70 on a 14" monitor with no problems.

---

### Post by simontaylor on 2008-06-16
Both the monitor and device code interpellations have stuck after a reboot. However there is neither a noticeable improvement in performance nor in either sys>pref>screen resolution or Screens & Graphics any indication that one been made. In fact, the latter gives me a resolution of 640 x 480 @ 60 Hz and now names the driver as "savage, S3 Savage, SuperSavage, Twister,..."

Interesting how much you can do without there being a change and how little a complete meltdown needs to happen.

Thanks, alienexplorers, for your help so far.

---

### Post by alienexplorers on 2008-06-16
Have you tried the openchrome driver listed by RomeReactor.

---

### Post by alienexplorers on 2008-06-16
Try copying this over you screen section of xorg.conf.  The addition of the mode line may help:

> Section "Screen"
    Identifier  "Default Screen"
    Device      "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
    Monitor     "Monitor Generic"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Modes       "1024x768"
    EndSubSection
EndSection



---

### Post by simontaylor on 2008-06-16
RomeReactor & alienexplorers,
I've checked out the thread regarding openchrome ... I don't know enough to make an informed decision. Firstly, would you recommend the build or a simple 

> sudo apt-get install xserver-xorg-video-openchrome 

??? (of course the straight up sudo apt-get is very tempting.)

reading through the build, I don't understand the direction "Change into the newly created directory" and I don't know what an X screen is.

I suppose what I need to know is if I meet the blank wall of blankness on an install attempt, will I be able to use Xserver in recovery to recover?

best,
simon

---

### Post by alienexplorers on 2008-06-16
I hate building and compiling things.  If I can get it pre-built I will take that everytime.

---

### Post by RomeReactor on 2008-06-16
I would also suggest the install first.

---

### Post by alienexplorers on 2008-06-16
Hi RomeReactor,
How am I doing.  Not use to answering questions, but I figured I would give it a shot.  Most of my beans were from questions I asked.

Donald Saunders
ALienexplorers

---

### Post by RomeReactor on 2008-06-16
> **alienexplorers said:**
> Hi RomeReactor,
How am I doing.  Not use to answering questions, but I figured I would give it a shot.  Most of my beans were from questions I asked.

Donald Saunders
ALienexplorers

Like a true veteran, as far as I'm concerned. You've obviously learned a lot from the questions you had! It looks to me like you're more on track with simontaylor's issue than me.

---

### Post by simontaylor on 2008-06-16
thanking you both for your recommendations, but in the meantime my display has had a dose of gigantism: is this the new "subsection" in my xorg.conf "screen" section? 

Both Screen Resolution and Screen & Graphics now agree I'm running 1024 x 768 @ 87 Hz (I pushed it up from 85 where it was sitting when I rebooted). However the latter, when I push "Test" gives me grey herring-bone patterns and the display overall looks like 800 x 600 @ 60 Hz!

Yours, now really confused,

simon

---

### Post by alienexplorers on 2008-06-16
Go to screen resolution and see what it say's there.  If it is 1024x768_87 then hit apply and use that.

---

### Post by simontaylor on 2008-06-16
here we go again: round 3. My beans are running out: 

> sudo apt-get install xserver-xorg-video-openchrome
[sudo] password for simon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
xserver-xorg-video-openchrome set to manually installed.
The following packages were automatically installed and are no longer required:
  libportaudio2 libbeagle1 libjack0.100.0-0 libsox0 libcsound64-5.1 dvdauthor
  libfluidsynth1 libportmidi0 tcl8.4 liblo0 libnetpbm10 ladcca2
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
simon@simon-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


entirely out of my depth. Why is my terminal asking me insulting questions?

Why is "xserver-xorg-video-openchrome set to manually installed"? (whatever that means.)

Why is everything so big and clunky in my display now? Completely contrary to how the system is describing itself?

?!

Curiouser and curiouser, said Alice.

My head hurts, said simple simon.

---

### Post by simontaylor on 2008-06-16
here we go again: round 3. My beans are running out: 

> sudo apt-get install xserver-xorg-video-openchrome
[sudo] password for simon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
xserver-xorg-video-openchrome set to manually installed.
The following packages were automatically installed and are no longer required:
  libportaudio2 libbeagle1 libjack0.100.0-0 libsox0 libcsound64-5.1 dvdauthor
  libfluidsynth1 libportmidi0 tcl8.4 liblo0 libnetpbm10 ladcca2
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
simon@simon-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


entirely out of my depth. Why is my terminal asking me insulting questions?

Why is "xserver-xorg-video-openchrome set to manually installed"? (whatever that means.)

Why is everything so big and clunky in my display now? Completely contrary to how the system is describing itself?

?!

Curiouser and curiouser, said Alice.

My head hurts, said simple simon.

---

### Post by RomeReactor on 2008-06-16
Those errors are due to running that last apt-get command without sudo. Have you made a backup of xorg.conf yet? If not, this would be a good time to do so:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Once that's done, and if you did install the driver, try reconfiguring the display: Press CTRL+ALT+F1 to switch to a console, then run:
```
sudo /etc/init.d/gdm stop
```
and:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Follow the steps and keep the defaults unless you know for certain that an option needs changing; also make sure you choose the OpenChrome driver when asked for the video driver. When the process finishes, it should start the display and dump you to your graphical desktop. If it doesn't, run:
```
sudo /etc/init.d/gdm start
```
or reboot:
```
sudo reboot
```

If after all of this your display is in worse shape than before, you can recover the backup by running:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and restarting your display by pressing CTRL+ALT+BACKSPACE, or restart Ubuntu.

---

### Post by skymera on 2008-06-16
To be honest I've had no luck with Via drivers.

Unichrome and Openchrome both didn't work.
So i stick to Vesa to be sure. My laptop can't run effects anyway so im not too bothered.

---

### Post by simontaylor on 2008-06-16
OK. RomeReactor, and alienexplorers, thanks for sticking with this: where are we?

backed up xorg.conf

followed your instructions RomeReactor: console > run: sudo /etc/init.d/gdm stop

and: sudo dpkg-reconfigure -phigh xserver.xorg

and duly stopped GNOME display [OK]

and overwrote "possibly customised configuration" 

and and ... that's it. No fireworks. Nothing. No opportunity to enter new driver. 

so I: sudo /etc/init.d/gdm start

and was returned to desktop. The only difference I saw was in the splash screen: not as ridiculously oversized as the display I'm writing in now.

So I check xorg.conf:

> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Groundhog day!

I don't believe I'm in 1024 x 768 @ 87 Hz. If this is the promised land, I wanna go back to Kansas.

Sorry. A little flip, I know. Appreciate your help.

simon

---

### Post by RomeReactor on 2008-06-16
Try the steps again, but this time run:
```
sudo dpkg-reconfigure xserver-xorg
```
without the -phigh flag. It should let you select the display driver.

EDIT: Hardy is less dependent on xorg.conf for the display configuration, so that might be an issue in trying to specify certain parameters in xorg.conf.

---

### Post by simontaylor on 2008-06-16
hi skymera,
the object of this exercise in seat-of-the-pants terminal-flying by remote-control as far as I'm concerned is to improve the performance of the VGA by getting above a 60 Hz refresh rate, to 70 Hz or higher. I don't do graphics and flash fx but do look at the screen a lot and know that higher Hz is easier on the eyeball. alienexplorers suggested I try installing drivers, hence the present thread. Any advice welcome.

simon

---

### Post by alienexplorers on 2008-06-16
Sorry could not help more.  Let the big guys move in and get you going.

---

### Post by simontaylor on 2008-06-16
back out of console land again, RomeReactor. It's a bit like that zone in Nightwatch: the gloom. 

Tried: sudo dpkg-reconfigure xserver-xorg

And was grilled about how I like my keyboard and my mouse but not my VGA.

Hardy is exactly the word in relation to attempts to reconfigure xserver-xorg: although it has got me into big letters land: the display is still ridiculously zoomed-in.

simon

---

### Post by RomeReactor on 2008-06-16
See what options you get now in 'System->Preferences->Screen Resolution' or in Screens and Graphics; if you get get roughly the same, use Screen Resolution. Also, please post your current xorg.conf, to see if there are any significant changes:
```
cat /etc/X11/xorg.conf
```

---

### Post by simontaylor on 2008-06-16
Screens and Graphics: 1024 x 768 @ 87 Hz
(interestingly, when tested, it came back with: 

> Configuration test failed
Please verify the selected devices and configuration)

Ha ha: Sys>pref>Screen Resolution: 1024 x 768 @ 87 Hz ... and then on a whim, so sick of BIG LETTERS, I pushed it up to 1280 x 960 and guess what: 60 Hz. 

I went through and changed the modeline to that which appears in xorg.conf, since it seems at this stage it's a toss up as to whether I get higher Hz or higher resolution: it doesn't appear that I can have both *at this stage*. Further advice welcome. And your assistance has been invaluable. I've learnt a lot. However there's really no solution here, only resolution.

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier 	"Monitor0"
	VendorName 	"Philips"
	ModelName 	"107S21"
	HorizSync 	30 - 71
	VertRefresh 	50.0 - 160.0
	Option 		"DPMS"
	Modeline 	"1280x1024_70.00" 128.94 1280 1368 1504 1728 1024 1025 1028 1066 -HSync +Vsync
EndSection 

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection


Yeah. See, that's the modeline and monitor section alienexplorers suggested before he found it not to be the one this model of monitor should have. As I say, at this stage, I'm opting for greater resolution and slower refresh, red eyes or not.

Any ideas?

Best,
simon

---

### Post by RomeReactor on 2008-06-16
Let's try this: make a new backup of this configuration:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_new
```
then edit the current xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
edit **Section "Device"** so it ends up like this:
```
Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:1:0:0"
	Driver		"savage"
	Screen	0
EndSection
```
and **Section "Screen"**:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
```

Save the file, close gEdit, and restart the display (CTRL+ALT+BACKSPACE) or reboot. If upon reboot you're not stisfied with the results and want to restore the latest backup, run:
```
sudo cp /etc/X11/xorg.conf.backup_new /etc/X11/xorg.conf
```
and restart your display.

---

### Post by simontaylor on 2008-06-16
Here's what I get:

> Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:1:0:0"
	Driver		"savage"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

There is no noticeable effect: 1280 x 960 @ 60 Hz say both screen resolution and screens and graphics.

I did try, as a silly experiment, changing the drivers in Screens & Graphics to Other / Openchrome: got that familiar old black wall of blankness and the same old sinking feeling.

Is there something I'm missing in these edits? They seem to have taken me full circle.

best,
simon

---

### Post by RomeReactor on 2008-06-16
I think you've reached the limit of the Linux driver for your VIA gpu; I could be wrong, and there are certainly many more people here who are more experienced with your particular gpu than me, but as I said earlier, Linux drivers for VIA integrated cards are not on par with their windows counterparts, which is not the case for Intel, nVidia or ATI. I dislike suggesting a new video card because it's not a solution to the problem, but in your case it's either put up with the low refresh rate or get another card. A cheap GeForce in the 6000 range would be a step up.

Hopefully someone else can provide a solution to this issue.

---

### Post by simontaylor on 2008-06-16
RomeReactor,
we sneaked in that "depth 24," the significance of which I didn't recognise until I did a bit of research. I agree, no solution except resolution, until I get another card. 

In actual fact, this was not my main but a secondary concern on this forum. My chief concern was that I can't burn audio cds!

This issue has in the meantime gone cold: although it appears it has been kicking around for some years in Ubuntu land.

thanks RomeReactor and alienexplorers. Long day. 

Must be time for some of those beans that are all over the forum. Me, I've got the roaster! 

best,
simon

---

### Post by alienexplorers on 2008-06-16
I picked up a nvidia fx5200 for 45 bucks on newegg.com...  works really nice with ubuntu.

---

### Post by eeried on 2008-06-16
> Hardy is less dependent on xorg.conf for the display configuration, so that might be an issue in trying to specify certain parameters in xorg.conf.

I don't think Hardy has much to do with the new Xorg which is totally new. As I understand it this new xorg adapts to your video card and monitor. As I said before running dpkg-reconfigure xserver-xorg doesn't help a bit.

After editing your xorg.conf file you're advised to run the -phigh command mentioned above - so says the xorg.conf file.

As for installing openchrome, it's already installed -- probably installed when you install Hardy on a via-S3 machine.

---

### Post by JoshuaRL on 2008-06-16
> **RomeReactor said:**
> Try the steps again, but this time run:
```
sudo dpkg-reconfigure xserver-xorg
```
without the -phigh flag. It should let you select the display driver.

EDIT: Hardy is less dependent on xorg.conf for the display configuration, so that might be an issue in trying to specify certain parameters in xorg.conf.

> **eeried said:**
> I don't think Hardy has much to do with the new Xorg which is totally new. As I understand it this new xorg adapts to your video card and monitor. As I said before running dpkg-reconfigure xserver-xorg doesn't help a bit.

After editing your xorg.conf file you're advised to run the -phigh command mentioned above - so says the xorg.conf file.

As for installing openchrome, it's already installed -- probably installed when you install Hardy on a via-S3 machine.

Agreed.  From what I understand, the newest version of Xorg that is in Hardy has moved primarily to autodetection at bootup.  Thus the reason that in the xorg.conf it has merely "configured video device" instead of all the drivers and arguements like in Gutsy.  Also, I think that dpkg-reconfigure xserver-xorg now has strictly to do with the keyboard and mouse.  No settings for the video card or monitor are there.

What you might try is, besides Screens and Graphics, the GTK port of displayconfig from KDE.  You can open it with:
```

displayconfig-gtk

```
You might be able to easier set your monitor to what you need, although at this point I kind of doubt it.  I agree with Rome and others, VIA is nasty on Linux.  They have pretty crappy drivers, and don't release specs on their chips to make it easier for open source drivers to be written.  I have a VIA onboard chip on my computer, but I put in a nVidia 8400GS right away.

Sorry.

---

### Post by eeried on 2008-06-17
Hello all,

I agree that VIA's rather rotten and when you can change the video card you're lucky. Our LUG has been given a laptop with VIA chipset and apparently onboard S3 video card. As the screen doesn't light up anymore we have added a CRT monitor. It's fine to display 1024x768 but I was looking for a way to make it compatible with a 19" LCD screen, and I have some doubts, reading this thread carefully.

I'll try editing the xorg.conf file as has been described in this thread to see if the video card can be pushed to display 1280x1024 on a very good though old and small Trinitron CRT monitor.

I was told the new Xorg can now adapt to various video cards without you having to run dpkg-reconfigure...

---

### Post by simontaylor on 2008-06-17
Hi JoshuaRL,

> displayconfig-gtk
mmap /dev/zero: Permission denied
VESA BIOS Extensions not detected.



That's what I get. Reconciled to running 1280 x 1024 @ 60 Hz now I know why. (I could run 1024 x 768 @ 87 Hz but it's really pretty ugly on my monitor - it's like duplo as opposed to lego.) Vesa has come up before. It's in the Bios?

best,
simon

---

### Post by RomeReactor on 2008-06-17
Hi again, Simon. VESA is a display standard, and the VESA driver in Ubuntu is considered a generic solution if the system is unable to configure the display with a more appropriate driver. The VESA driver will work with any video card, but its performance leaves a lot to be desired.

Before Hardy, one could edit the xorg.conf file and specify which driver to use; this time around, with the new version of Xorg, it seems that's no longer the case.

EDIT: displayconfig-gtk is the Screens and Graphics application.

---

### Post by eeried on 2008-06-17
simontaylor, in fact you're lucky to be able to run 1280x1024 :guitar: I'll report if I manage to achieve the same feat on our old laptop

---

### Post by simontaylor on 2008-06-17
I feel like using a newzealandism, cherrr!

With RomeReactor and alienexplorer's help I feel we turned some turf.

best,
bien à vous,

simon

---

### Post by JoshuaRL on 2008-06-17
> **simontaylor said:**
> Hi JoshuaRL,



That's what I get. Reconciled to running 1280 x 1024 @ 60 Hz now I know why. (I could run 1024 x 768 @ 87 Hz but it's really pretty ugly on my monitor - it's like duplo as opposed to lego.) Vesa has come up before. It's in the Bios?

best,
simon

Okay, if it is saying you have permission errors, try putting gksu in front of it.  It would be:
```

gksu displayconfig-gtk

```
That may fix it.

Just a note, you would want to use gksu instead of sudo when launching graphical applications with root privilidges.  gksu means "graphical superuser-do".  That's a good rule of thumb;  sudo for command line, gksu for graphical.

And yeah, RomeReactor and alienexplorer are both pretty helpful.

:guitar:

---


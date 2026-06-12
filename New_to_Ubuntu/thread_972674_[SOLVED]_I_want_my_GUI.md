---
title: "[SOLVED] I want my GUI"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by ZOOstation on 2008-11-06
EDIT: [SHORTCUT TO THE LATEST STATE OF THINGS]("http://ubuntuforums.org/showthread.php?p=6135467#post6135467")

I just upgraded from 8.04 to 8.10. At the reboot to complete the upgrade process, I had no GUI. Still do. Just a terminal that alludes to display errors.
One example:
```
Could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be
disabled. Please restart GDM when
the problem is corrected.
```
I tried sudo dpkg-reconfigure xserver-xorg but with no noticeable result.
I installed fglrx-amdcccle, fglrx-kernel-source, and xorg-driver-fglrx successfully, not that it helped.
It suggested installing libamdxvba1 as well.
```
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  libamdxvba1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 412kB of archives.
After this operation, 1376kB of additional disk space will be used.
Err http://archive.ubuntu.com intrepid/multiverse libamdxvba1 2:8.543-0ubuntu4
  Could not resolve 'archive.ubuntu.com'
```
Fail.
I tried sudo startx and got:
```
X: warning; process set to priority -1 instead of requested priority 0
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server.
xinit: No such process (errno 3): Server error.
```

What I'm doing in the meantime is booting from livecd to access the forums (and my email and necessities), then rebooting from the hard disk to try suggested fixes. I don't want to do a clean install for fear it will wipe out my old files. (I never seem to backup in time for this kind of crisis).

I've been on Ubuntu for like a year but still don't really have a grip on the basics so please take me step-by-step through any solutions you have or information you need.

My specs, for what they're worth:
HP Pavilion zd8000 ("Lappy")
100 gb hard drive
3gHz Intel Pentium 4HT
ATI Mobility Radeon X600 graphics card
Need anything else?

---

### Post by bumanie on 2008-11-06
Try > sudo xfixIt is the updated command for the old "sudo dpkg-reconfigure xserver-xorg". If that doesn't work, try to go to hardware drivers and see whether the driver is enabled if it is, try to disable it and run with default vesa driver. If all works, try to re-enable the graphics card in hardware drivers. None of this may help - I think it sounds like a config. file is out of whack, but I'm not great at editing them.

---

### Post by ZOOstation on 2008-11-06
Thank you, I will try xfix on my next reboot.

As for your other stuff, please explain to me:
- How can I check, enable, and disable hardware drivers from the terminal?
- What is the vesa driver?

---

### Post by bumanie on 2008-11-06
Sorry. I slightly misread the original post - you can also try > sudo apt-get install ubuntu-desktop In fact try that before xfix. Don't worry about the drivers yet - tackle that if the above command fixes your GUI.

---

### Post by Poyntz on 2008-11-06
> **ZOOstation said:**
> 
- How can I check, enable, and disable hardware drivers from the terminal?


These may (or may not) be handy:
- lshw | less    - lists hardware
- lpinfo  - shows available devices or drivers

Hope they help. I've never personally used them so don't know :/

---

### Post by ZOOstation on 2008-11-06
Hokay, so:
```
me@Lappy:~$ sudo xfix
sudo: xfix: command not found

me@Lappy:~$ sudo lshw -c display
  *-display
       description: VGA compatible controller
       product: M24 1P [Radeon Mobility X600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx
```

Haven't heard of lpinfo, I'll try that out next time.
Dammit, I just read that I copied down "ubuntu_desktop" instead of "ubuntu-desktop." I'll have to retry that one too.

Another thing that's irritating me is that it takes a long time to start up and shut down. The startup splash loads almost halfway and then hangs. And when rebooting, the shutdown splash cuts from exactly halfway finished to a black screen with that little blinky input underscore, where it hangs for nearly three minutes before printing "acpid: exiting" and then restarts. I don't know if these things are related, I'll do a little googling to find out what acpid is. Unless you can tell me. But I do know that when starting up from the cd it takes a (reasonably) short amount of time and shutting down from the cd is practically instantaneous.

---

### Post by porchrat on 2008-11-06
I would imagine that acpi is the acpi daemon.  Some machines have hardware that rely very closely on acpi (Advanced Configuration and Power Interface).  Unfortunately ACPI was never really designed to work well with any Linux distro and thus causes a lot of problems.  Luckily Linux doesn't really need it to run (although if u disable acpi you will lose SMP functionality).

In order to boot ubuntu without using acpi you can add "noacpi" to your /boot/grub/menu.lst on the end of the line that contains your kernel details.  Note that this does mean you will have to turn the machine off yourself as without ACPI linux will halt, but the machine will not physically switch off.

It is annoying and of course the loss of SMP can be crippling to some people (depending on what you use the machine for).  With these problems in mind it may just be best 2 put up with the slow ACPI problem.

EDIT: What happens when you restart the gdm?

```
sudo /etc/init.d/./gdm restart
```

---

### Post by Poyntz on 2008-11-07
> **ZOOstation said:**
> Hokay, so:
Another thing that's irritating me is that it takes a long time to start up and shut down. The startup splash loads almost halfway and then hangs. And when rebooting, the shutdown splash cuts from exactly halfway finished to a black screen with that little blinky input underscore, where it hangs for nearly three minutes before printing "acpid: exiting" and then restarts.

[Go here]("https://bugs.launchpad.net/bugs/+filebug") to report the bug on launchpad. Remember to list the steps that you took to get to the problem along with your O/S version and the package version of acpi.

```
apt-cache policy acpi
```

---

### Post by ZOOstation on 2008-11-07
lpinfo seemed to do nothing. It didn't give me any info about devices or drivers. But I already posted the ATI card info above, if that helps.

ubuntu-desktop is already the latest version (it says).

And gdmrestart prints:
```
 * Stopping GNOME Display Manager...
   ...done.
 * Starting GNOME Display Manager...
   ...done.
```

:confused:

I will report the acpi bug, thanks.

---

### Post by ZOOstation on 2008-11-07
I was having trouble with apt-get update so I checked if I was properly connected to the internet. I was not, and once I enabled my internet connection I was able to update. And once I updated and upgraded, my startup and shutdown lags were fixed. But still no GUI, even after I made sure xorg-driver-fglrx and its associated packages were up to date.

One thing that also started post-upgrade is the following lines at the end of the startup process:
```
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/509196bc-6cac-47e1-a1ca-5b55cd50b1ab) = dev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/509196bc-6cac-47e1-a1ca-5b55cd50b1ab
kinit: No resume image, doing normal boot...
```

And it seems a new problem was created after upgrading. The packages linux-image, linux-image-generic, and linux-image-2.6.27-7-generic don't install completely. It appears to be a dpkg error.
```
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.27-7-generic (2.6.27-7.16) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
/etc/ucf.conf: line 1: root:x:0:0:root:/root:/bin/bash: No such file or directory
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-7-generic; however:
  Package linux-image-2.6.27-7-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.27.7.11); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-7-generic
 linux-image-generic
 linux-image
```

I wish that fixing any of the new problems that appear along the way would eventually turn out to be the reason I have no GUI. Any advice on that unrelated to the other stuff is most anxiously anticipated.

---

### Post by Poyntz on 2008-11-07
I'm not sure about the validity of the comment but I heard somewhere that firefox is required to run gnome-desktop. Do you have firefox installed? 
If not try installing it and see what happens 
```
sudo apt-get install firefox-3.0
```
Then reboot.
```
sudo shutdown -r now
```

---

### Post by ZOOstation on 2008-11-08
Firefox is installed in the latest version.

---

### Post by bscbrit on 2008-11-08
```

bscbrit@laptop:~$ man xfix
No manual entry for xfix
bscbrit@laptop:~$ sudo xfix
[sudo] password for bscbrit: 
sudo: xfix: command not found
bscbrit@laptop:~$ sudo apt-get install xfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xfix
bscbrit@laptop:~$ 

```

I'm running 8.10 with appropriate repos enabled, but I cannot find xfix anywhere. If I search in the repos I can find libxfixes3 but no obvious program that uses that library.  Have others found the same problem?

---

### Post by Poyntz on 2008-11-08
> **bscbrit said:**
> 
I'm running 8.10 with appropriate repos enabled, but I cannot find xfix anywhere. If I search in the repos I can find libxfixes3 but no obvious program that uses that library.  Have others found the same problem?

Option 1
Try this in terminal:
```
apt-cache search xfix
```

Option 2
[Go here]("http://packages.ubuntu.com/intrepid/libxcb-xfixes0") for libxcb-xfixes0
[Go here]("http://packages.ubuntu.com/intrepid/libxcb-xfixes0-dbg") for libxcb-xfixes0-dbg
[Go here]("http://packages.ubuntu.com/intrepid/libxcb-xfixes0-dev") for libxcb-xfixes0-dev
[Go here]("http://packages.ubuntu.com/intrepid/libxfixes-dev") for libxfixes-dev
[Go here]("http://packages.ubuntu.com/intrepid/libxfixes3") for libxfixes3
[Go here]("http://packages.ubuntu.com/intrepid/libxfixes3-dbg") for libxfixes3-dbg

As you are using Intrepid Ibex these links will hopefully be useful.

---

### Post by ZOOstation on 2008-11-08
I saw that the linux-image-2.6.27-7-generic problem is pandemic so I just deleted it for now. I'll work that one out as solutions develop.

Still no luck with the GUI. I found another thread where the suggestion of re/installing xorg and gnome-core worked for someone else. When I installed gnome-core it also suggested installing gnome-desktop-environment. But after installing both of those I still have no GUI.

Could this be relevant?
```
me@Lappy:~$ startx


X: warning; process set to priority -1 instead of requested priority 0
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

---

### Post by bscbrit on 2008-11-08
I've got all the lib files but no specific xfix program.  Curious.

---

### Post by ZOOstation on 2008-11-08
xfix doesn't do anything for me either. Command not found, just like bscbrit. I installed those packages you listed too, still no dice.

---

### Post by bscbrit on 2008-11-08
ZOOstation

I've discovered that there is NO xfix program.  It is an option that you are presented with when running the recovery program.

The problem is, often, that if the computer fails to find the correct hardware during installation then it will also fail to detect it when to try to use the xfix option.  The used to be a way of letting the user input information to assist in the configuration of xorg but that has changed recently.  Have a look at 'man xrandr' which might help in this particular case.

PS I raised a bug (#294202) a few days ago regarding this lack of user input when configuring xorg.

---

### Post by ZOOstation on 2008-11-08
Oh, right. Research tells me that xfix is the same as
```
dpkg-reconfigure xserver-xorg
```
Which hasn't done me any good either.

---

### Post by bscbrit on 2008-11-08
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

looks interesting but it is not a command that I am familiar with yet.

---

### Post by Poyntz on 2008-11-08
> **ZOOstation said:**
> Still no luck with the GUI

This is probably a silly question, but have you tried rolling back your graphic driver to the default graphic driver? I would give you the code to do this but, never having had a desktop failure, I handle drivers through the GUI program, and consequently don't know which shell program/command does it.

---

### Post by ZOOstation on 2008-11-08
I haven't, mostly because I don't know how. Looking around, I found someone's advice to do this by changing the /etc/X11/xorg.conf file from saying
```
Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
EndSection
```
to
```
Section "Device"
Identifier "Configured Video Device"
Driver "ati"
EndSection
```
When I looked at xorg.conf it didn't have either of those Driver lines in it, so first I tried adding fglrx then changing it to ati. Neither worked. I'll keep looking through that thread for help: [[ubuntu] Roll back video drivers]("http://ubuntuforums.org/showthread.php?t=817542")

Here's something important: when I use dpkg-reconfigure xserver-xorg it doesn't ask me for info about the display. It asks about my keyboard. Is xserver-xorg broken or somehow linking to the wrong file or something?

---

### Post by Poyntz on 2008-11-08
try
```
apt-cache search <your video driver here>
``` (eg, apt-cache search nvidia) 
or 
fire up aptitude (aka in console type: sudo aptitude), try the above, and then search for xorg related entries using aptitude. Look at the descriptions and see if there's something specifying driver config or the like. Additionally under xorg there should be a bunch of stuff for ATI drivers.
You should be able to find a program that will either install the driver you need or enable you to configure drivers from a list of drivers installed on your machine.

---

### Post by ZOOstation on 2008-11-09
I think my xorg.conf file is extremely broken.
```
# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```
No matter how many times I specify a device driver and save, it just reverts to this. I'm under the impression this is lacking a lot of information. If anyone knows how I can complete and correct xorg.conf and how to keep it that way, I'm anxious to hear it.

I tried this advice from that thread I linked to...
> **anindya_m said:**
> Something is wrong with your xorg.conf: it's missing sections. First we have to make sure the xorg-driver-fglrx is purged (dpkg --purge xorg-driver-fglrx) and xserver-xorg-video-ati package is installed. Then remove (or rename to something) your xorg.conf file and run ```
sudo dpkg-reconfigure xserver-xorg
```Enter the correct info (resolution, etc) in the following screens and your xorg.conf should be restored.
...and it got me somewhere. Not very far, but somewhere. (Again, dpkg-reconfigure xserver-xorg asks me only one video related question, and the rest are about my keyboard config. So the bit about entering my "resolution, etc." has me puzzled).

After following those instructions, when I use startx I get one of two responses. I haven't figured out yet what triggers one over the other.

The first is a sort of hashmarked background with a terminal in the upper left corner. I have some graphical capability but no desktop.

The second is a blank gnome desktop with an error message that reads "I could not start your session and so I have started the failsafe xterm session. Windows now have focus only if you have your cursor above them. To get out of this mode type 'exit' in the window in the upper left corner." Unlike the other response, this one has no terminal in the upper left corner. And after clicking OK to that error window it has no features whatsoever, just a moveable cursor. The pointer set and backdrop are clearly ubuntu defaults though, so that's an enormous improvement.

This second one is often preceded by a successful GDM login screen, from which I can effectively login and reboot, but the latter arrives back in the black screen terminal I've been in.

I'll keep examining xorg related packages and configs.

---

### Post by bscbrit on 2008-11-09
dpkg-reconfigure xserver-xorg no longer asks for user input.  Xorg 7.4 uses a different method of configuring the displays and it is fully automated.  What you are seeing is the correct method of operation of this version.

But, that doesn't help you solve your problem.  The command that you need to use is xrandr, which will enable you to input your own parameters. Try 'man xrandr' or Google for a similar expression to find more information.

Both xorg and the layout of xorg.conf have changed significantly under Ubuntu 8.10 and this has been a cause of some confusion for the users.  The GUI configuration tool displayconfig-gtk has also been removed, leaving users with only the command line to configure their computer displays.  I have raised a bug report against this lack of easy-to-use tool.   Because it is a new system there is also relatively little reference material in the forum to help those experiencing difficulties.

---

### Post by ZOOstation on 2008-11-10
xrandr outputs "Cannot open display"

I'm trying now to redo the upgrade using an alternate cd.

I put the iso onto my hard drive and can successfully mount it like I'm using a real cd. Being stuck in a terminal with no GUI I get no automatic response from the cd, so I have to get it running myself. The installation guide said to use
```
gksu "sh /cdrom/cdromupgrade"
```
This alerts me that GTK also cannot run its display. Reading that "gksu" is essentially a graphic interface for sudo, I tried
```
sudo sh /cdrom/cdromupgrade
```
Which begins pouring out text, but aborts after about ten lines about not being able to open files, mostly graphics.

So now I'm trying the actual alternate cd. As with the other, it does nothing if I insert it. gksu gives me the same response, but this time sudo sh doesn't work either. It can't find "/cdrom/cdromupgrade"
When I boot with the cd, the options "Install Ubuntu" "Check CD for defects" and "Rescue a broken system" all do the same thing: it begins giving me text (some options more than others) and then the display loses its mind. Attached is a photo of my screen when this happens.
[IMG]http://i35.tinypic.com/2rz8hab.jpg[/IMG]

Anyone got any bright ideas?

---

### Post by bscbrit on 2008-11-10
It really does look as though 8.10 is incompatible with your hardware although I cannot even begin to explain why it should be.  Either that or there is something seriously wrong with your hardware but I strongly suspect the former.  Does it run with the 8.10 Live Disk?

My belief is that you should try installing another distro, either an earlier Ubuntu ( I suggest 8.04 desktop) or perhaps Fedora.

---

### Post by ZOOstation on 2008-11-10
Yes it runs on the live disc. That's how I've been getting online to look for help. If I install from the live disc and partition it alongside the current system, essentially dual-booting a working 8.10 with a broken one, will it effect the files presently on my hard drive? I guess I just don't understand enough about partitions yet.

---

### Post by JKBurton on 2008-11-10
Whenever you can't start X, there is debugging info in its logfile, at /var/log/Xorg.0.log. It's waaaay too much info, naturally, and hard to read. But if you'll post the contents here I'll take a look and see what I have to offer.

Umm, first do dpkg-reconfigure xserver-xorg one more time, to put your configuration back the way Ubuntu thought it should be.

Keith

---

### Post by candtalan on 2008-11-10
> **ZOOstation said:**
> Yes it runs on the live disc. That's how I've been getting online to look for help. If I install from the live disc and partition it alongside the current system, essentially dual-booting a working 8.10 with a broken one, will it effect the files presently on my hard drive? I guess I just don't understand enough about partitions yet.

I very much sympathise.
Just a thought: if you are able to inspect and maybe copy the xorg.conf from the live CD operation - which works - and paste it into the failed installation - by various means -  I wonder if xorg is now such that this will be helpful?

hth

---

### Post by bscbrit on 2008-11-10
I'm just booting up the 8.10 Live Disk.  If my memory serves me well, the last time I tried this the xorg.conf contained nothing more than the default xorg.conf contents.  The clever bits are stored elsewhere and I haven't been able to identify how to manipulate them to change them to my liking.  I've tried to use both xrandr and xset but not to any benefit.

Yep, just as I thought, the xorg.conf contains nothing useful under Live Disk.

---

### Post by phidia on 2008-11-10
> **bumanie said:**
> Try It is the updated command for the old "sudo dpkg-reconfigure xserver-xorg". If that doesn't work, try to go to hardware drivers and see whether the driver is enabled if it is, try to disable it and run with default vesa driver. If all works, try to re-enable the graphics card in hardware drivers. None of this may help - I think it sounds like a config. file is out of whack, but I'm not great at editing them.

This is incorrect.

To issue 'xfix" you need to boot in recovery mode and no "sudo" is required there. "xfix" only works in recovery mode.

Also "xfix" isn't truly a update for the dpkg-reconfigure command since xorg isn't being used or isn't used as it once was.

---

### Post by phidia on 2008-11-10
> **bscbrit said:**
> dpkg-reconfigure xserver-xorg no longer asks for user input.  Xorg 7.4 uses a different method of configuring the displays and it is fully automated.  What you are seeing is the correct method of operation of this version.

But, that doesn't help you solve your problem.  The command that you need to use is xrandr, which will enable you to input your own parameters. Try 'man xrandr' or Google for a similar expression to find more information.

Both xorg and the layout of xorg.conf have changed significantly under Ubuntu 8.10 and this has been a cause of some confusion for the users.  The GUI configuration tool displayconfig-gtk has also been removed, leaving users with only the command line to configure their computer displays.  I have raised a bug report against this lack of easy-to-use tool.   Because it is a new system there is also relatively little reference material in the forum to help those experiencing difficulties.

Could you provide a link to that bug report?

Has anything been added to it-comments from devs?

---

### Post by bscbrit on 2008-11-10
I've run out of ideas.  The new Xorg has got me beat.  I'll keep trailing this thread so that I can learn how to fix problems in the future, but I fear that I will not be able to contribute much anymore.  ZOOstation, I'm sorry that I wasn't up to the task.

---

### Post by bscbrit on 2008-11-10
phidia

It is reported as bug #294202.  There are no additional comments since the report was raised on 05-11-2008.

[https://bugs.launchpad.net/ubuntu/+bug/294202](https://bugs.launchpad.net/ubuntu/+bug/294202)

---

### Post by ZOOstation on 2008-11-10
candtalan:

Yeah, I thought of that too. They're already identical, so no effect.

JKBurton:

You asked for it...
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux Lappy 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 10 15:55:32 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 2

(--) PCI:*(0@1:0:0) ATI Technologies Inc M24 1P [Radeon Mobility X600] rev 0, Mem @ 0xd0000000/0, 0xc8100000/0, I/O @ 0x00004000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules/fonts//libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched radeon from file name radeon.ids
(==) Matched radeon for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610, ATI RV670,
	ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE, ATI Radeon HD 3470,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI FireMV 2450, ATI FireMV 2260,
	ATI FireMV 2260, ATI ATI Radeon HD 3600 Series,
	ATI ATI Radeon HD 3650 AGP, ATI ATI Radeon HD 3600 PRO,
	ATI ATI Radeon HD 3600 XT, ATI ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000c8100000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon Mobility X600 (M24) 3150 (PCIE)" (ChipID = 0x3150)
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): PCIE card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb7f7f400]
2: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb79f5b07]
3: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb79c355a]
4: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb79c64fc]
5: /usr/bin/X(InitOutput+0x96f) [0x80aac9f]
6: /usr/bin/X(main+0x279) [0x8071b19]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b79685]
8: /usr/bin/X [0x8071101]
Saw signal 11.  Server aborting.
```
I hope you find something of value in that monster.

phidia:

The xfix function in recovery mode does little, so far as I can tell. The only output of any value is when it tells me it's backing up and overwriting xorg.conf
I also tried using the root terminal in recovery mode and typing "xfix" and got "-bash: xfix: No such command" or something like that.

---

### Post by Keen101 on 2008-11-10
you said you were having trouble with starting up bar hanging or going slow in the middle? 

We'll, if you edit your grub menu to say this > ## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=90ee8ca9-a49a-458f-a4c1-8a97c89a073f ro splash instead of > ro quiet splash

Then it will display what it is doing at bootup... and you can figure out if it is having any problems booting up.

 hope i said that clear enough. Don't just copy what i pasted, but i meant to explain that if you can edit you grub menu, and find your kernel that is booting, then by removing the word **quiet** you can have grub display what is happening at boot.

---

### Post by ZOOstation on 2008-11-10
Thanks Keen101, that problem's gone away but I'll see if that change still needs to be made. Perhaps it'd keep the problem from coming back.

---

### Post by JKBurton on 2008-11-10
ZOOstation, I did see some interesting stuff at the end of the Xorg logfile, but I don't know what to do about it.

Your video driver is actually crashing (see near the bottom where it says "Backtrace"?  That means a crash).  So it isn't just a configuration error. It's a real bug. I think the thing it was working on when it crashed was "DRI", which stands for Direct Rendering Interface and is needed for 3d acceleration...and that's all I know about it.

Googling got me several hits on the same problem popping up from time to time on the fglrx driver, apparently only on certain mixes of video and audio hardware (what audio would have with it, I don't know!). One guy fixed it buy applying a patch to his audio driver, but that was 3 years ago so that old patch definitely wouldn't work anymore.

Here are a couple of things to try in your /etc/X11/xorg.conf file. Please make a backup copy of the file before editing it...
  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.beforechgs
  sudo gedit /etc/X11/xorg.conf

I had an unrelated video problem with my ATI which was fixed by changing the "AGPMode" to a lower number. I got the impression there were several different problems in the current driver that could be fixed by this change.

To try it, edit your /etc/X11/xorg.conf file, find the "Device" section that talks about the video device. In mine, it looks like this:
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Add this line before "EndSection":
        Option          "AGPMode" "1"

Cross your fingers, and give it a try. If startx still leaves you with that lovely black screen, then add this to the bottom of the xorg.conf file and try again:
Section "Extensions"
    Option  "Composite" "Disable"  #make DRI work with fglrx.
EndSection

That was a fix to make DRI work last year, but isn't supposed to be necessary any more. If both those changes together don't work either, then just put the old copy of xorg.conf back, and I'm out of ideas for now. It would be interesting to take a look at a /var/log/Xorg.0.log on the open source "ati" driver instead of the "fglrx" one, for comparison...but I can't promise I'd learn anything useful :)

Best of luck,
Keith

---

### Post by ZOOstation on 2008-11-11
Relatively good news, everyone!

I installed clean off the Live CD and partitioned the hard drive in half. The good news is that the new install works beautifully and I can easily transfer my files from the broken system to the new one. So we haven't figured out what was wrong with the original upgrade, but it seems like we don't have to know.

I'm going to settle into this new install a little bit before I go figuring out how to undo the dual boot without losing files or functionality.

---

### Post by bscbrit on 2008-11-11
Good news!  The important thing is that you now have a working system.

Good Luck, and I hope to see you around the forums.

bscbrit

---


---
title: "Recent updates: unable to move cursor at logon"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by Hodevah on 2013-02-19
During the updates that recently were available and downloaded by myself, I moved to re-boot the computer as per the update request. Upon boot up, I was unable to move my cursor (unlike as it was prior to the updates) to the login window to place my login credentials.  Am using 12.10 **(not LTS)**.

Also, the screen resolution has changed from what it was before. Currently, and as was during the initial install of Ubuntu, the resolution was 1920X1080.

At the login screen there is a black border around the desktop real-estate. Ubuntu does show, but with the black border surrounding on all 4 sides. With the exception of the resolution having gotten wacked up after the updates as well as myself being unable to use the cursor to login and thence-forth change things, I have to log in via the Grub Advanced Menu Options and use the previous kernal for logging in to conduct my business. 

(1) I use a wireless mouse. Have tried to unplug/re-plug in transiever to no avail.
(2) Have tried a corded mouse to no avail.
(3) When trying to get into the Recovery Mode for Kernal *linux-image-3.5.0-25-generic (*latest kernal release), I cannot move the up/down arrow keys on the keyboard. ESC does not function either for that recovery mode. Basically, nothing. Even random key entries do nothing for the Recovery Mode for this particular kernal image. 

I do  not want to keep turning the 'off' button so as to exit the attempted logon as a normal exit is not possible when using this newer kernal release version.

Also, I have done a bit of researching throughout the forums. There do seem to be a number of problems that others have experienced with the most recent updates having been made available but those problems are all unique and quite different than the one I am experiencing at the moment. 

Here is some information regarding my computer graphics


> user@user-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts XT [Radeon HD 6800 Series]
user@user-desktop:~$ glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD BARTS
OpenGL version string: 2.1 Mesa 9.0.2
OpenGL shading language version string: 1.30
OpenGL extensions:> user@user-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts XT [Radeon HD 6800 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Barts HDMI Audio [Radeon HD 6800 Series]
03:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
04:00.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:01.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:04.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:05.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:07.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:09.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11)
0a:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30)
0b:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
0c:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11)
user@user-desktop:~$ 
I have a question _not jus_t regarding how to solve the above mentioned problem but the driver listed here at this link > [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Would they be the most appropriate drivers to install as I noticed that during the update (as far as I can recall) there was some kind of graphic update involved? 

 Please do correct me if I am wrong but I think I did see something via the update window being presented. 

Also, one final thing. 

Terminal command:

> grep blacklist /etc/modprobe.d/blacklist.confresult:

> user@user-desktop:~$ grep blacklist /etc/modprobe.d/blacklist.conf
blacklist evbug
**blacklist usbmouse**
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
Is the darkened **'usbmouse'** the reason why I cannot move the usb mouse in the newest kernal updates yet am able to manipulate the mouse cursor 

Currently am using (because this one allows me to manipulate my mouse/cursor):

> user@user-desktop:~$ uname -a
Linux user-desktop 3.5.0-24-generic #37-Ubuntu SMP Thu Feb 7 01:50:30 UTC 2013 x86_64 x86_64 x86_64 GNU/Linu
Currently have installed the following kernals at the moment:

> user@user-desktop:~$ dpkg -l | grep linux-image
rc  linux-image-3.5.0-22-generic                    3.5.0-22.34                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-23-generic                    3.5.0-23.35                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-24-generic                    3.5.0-24.37                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-25-generic                    3.5.0-25.38                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-22-generic              3.5.0-22.34                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-23-generic              3.5.0-23.35                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-24-generic              3.5.0-24.37                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP

The most recent kernal update is the one that is causing me some trouble with respect to aforementioned troubles. 

Also, just in case:

> user@user-desktop:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 004: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 005: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 004 Device 002: ID 05e3:0612 Genesys Logic, Inc. 
Bus 004 Device 003: ID 05e3:0612 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0db0:3871 Micro Star International 
Bus 002 Device 004: ID 0db0:a871 Micro Star International 
Bus 003 Device 006: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 003 Device 007: ID 4971:ce07 SimpleTech 
Bus 003 Device 008: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUBThank you kindly in advance for your help to my current situation.  ;)






.

---

### Post by DuckHook on 2013-02-20
Firstly, you must be commended for doing a truly phenomenal amount of groundwork before posting. I wish all users who ask for help would be this prepared and thorough. If you don't mind a tip, use the code tags rather then quote tags for even easier readability of output. This is the hash # mark at the top of the posting box.

As to your problem: I don't know why recent updates have caused such a raft of breakages. They seem to centre around video and WIFI.

I notice that you have the Radeon HD 6800 series chipset, but use the MESA driver with it. Have you tried the proprietary Catalyst driver from AMD or are you philosophically opposed to it? If willing to give it a go, it may solve your video and possibly even mouse problems.

BTW, leave usbmouse blacklisted. This is actually the name of an old mouse driver that was deprecated for a more recent one (can't recall name at moment). It may be necessary to use it, but let's cross that bridge when we come to it.

I would not install driver in the link unless events force you to. This is a new driver designed for the absolutely latest chipsets. It's always better to stick to repository drivers if possible, and your video card is common enough and been around long enough that it should be well tested and supported.

Awaiting your decision on proprietary driver.

If you think you already have proprietary driver installed, please do:```
sudo lspci -vk | grep -iA21 vga | grep driver
```

<edit>
if you are intent on installing the linked driver, it cannot be installed as is. There are a number of critical dependencies that must be installed first. Let's leave that to another thread.
</edit>

---

### Post by Hodevah on 2013-02-20
Hi DuckHook.  :p  

Thanks for getting back to me. 

Firstly, I am not opposed to using a proprietary driver from Catalyst. Though before we possibly begin to navigate towards that route, I noticed something else earlier.

Because I had some trouble booting into the previous kernal mode today(*Linux user-desktop 3.5.0-24-generic*), ---due to the machine not shutting down properly last night which does happen at times. In other words, when this does happen all I see is a hung boot-off image which necessitates for me to hard boot-off the machine. Something which I don't really like doing at all. 

Nevertheless, in using *Linux user-desktop 3.5.0-24-generic *which is that kernal that allows me to manipulate the mouse/cursor, I was unable to boot into that kernal's normal boot mode. Hence I needed to go into safe graphics mode for today.

 Since this is the first time that I have used safe graphics mode(for any kernal for that matter), I should note that when having attempted to boot into the newest kernal, the black border looked very much like this safe graphics boot mode that I have to use at the moment. 

Only just mentioning this as an aid to navigate/observe to, to what the problem looks like that I am experiencing at the moment with the newest kernal release. 

Secondly, I do not believe that I have the above named proprietary driver installed as there was no Terminal response from the given command.

```
user@user-desktop:~$ sudo lspci -vk | grep -iA21 vga | grep driver
[sudo] password for user: 
user@user-desktop:~$
```With respect to installing/using the Catalyst driver, you might have to help me navigate through the Terminal commands properly. 

Finally, I agree with you that perhaps we should just leave to NOT install the proprietary driver from the link I gave earlier. I had only just mentioned it because I was not too sure whether or not it might be prudent to install that as a resolution to the problem. 

One other thing that I would like to bring up here at this point is if your considering that I install the AMD  Catalyst graphics drivers how exactly will that solve the cursor issue? Graphic issues are one thing but cursor issues are another. To be honest, I cant see that being a solution simply that there must be a package in the latest kernal release that fails to recognize a transceiver for a wireless mouse including a wired mouse. This also includes use of a keyboard using any number of key combinations to try to get some kind of response. Both in and outside of the Recovery Mode for that kernal release. 
Anyway, that is my thought on the issue. 

Thanks again DuckHook for getting back to me.   :popcorn:


**EDIT:** I managed to successfully return to the regular/normal boot mode in *Linux user-desktop 3.5.0-24-generic* kernal after using the safe graphics boot mode for that kernal. Now to continue to solve the problem with the latest kernal release.

---

### Post by DuckHook on 2013-02-20
Installing additional drivers is very easy. However, it is important to understand the risks so you can make an informed decision.

You are currently using the community-developed open source drivers that come with Ubuntu. This driver is called *mesa* and was built by reverse engineering the workings of various AMD cards (likely including your own) and trying to duplicate the system calls that are needed to use all of the card's features. Because the reverse engineering process involves little if any input from AMD, this driver will always be less feature-rich and complete than AMD's. The alternate driver developed by AMD, called *FGLRX*, contains closed-source proprietary binaries that the open source community cannot include, but for obvious reasons, is privy to the secret workings and peculiarities of the AMD chipset and should theoretically run with less issues. In practice, this is not so, because such drivers often trade stability for performance. In my experience, they also suffer from the reverse problem: their coders are not familiar with Linux and so, all too often, their drivers also misbehave. This is why you should avoid bleeding-edge drivers like the ones on AMD's site and prefer the AMD drivers in the repositories.

If you replace the open source *mesa* drivers with AMD's *FDLRX*, you will be replacing them system-wide, inclusive of the older kernels that still work with *mesa*. If the new drivers don't work, you will be unable to get to your GUI even with the old kernels. The chances of this happening are very unlikely, but not zero. Even should it occur, there are ways to get to the command line and recover your old drivers, but this involves GRUB and the command line, and you certainly should be aware of the problem potential.

I highly recommend that you back up all important data before installing such a driver (read my signature line).

If you wish to proceed, then:

1. Go to Update Manager>Settings>Ubuntu Software. Make sure "Proprietary drivers for devices (restricted)" is checkmarked.
2. Go to  "Additional Drivers". Click the radio button for "ATI/AMD proprietary FGLRX graphics driver". Then click "Install". The driver is a large download of about 100MB so be patient. After the download is complete, the install process will start which, depending on your computer, can also take a while (but not more than an hour). Do not interrupt it.
3. Once installed, you will be told to reboot in order to switch to the new driver. Do So.

Hopefully, the new driver will solve your display and mouse problems. Let us know how it goes.

---

### Post by Hodevah on 2013-02-22
HI DuckHook. 

I have not yet installed the *fglrx* proprietary drivers, or any additional *fglrx patches* as options to install. 

I am actually quite glad you provided the above education regarding the reverse engineering procedures by Ubuntu coders.  For sure I am not going to install any of the bleeding edge drivers on the AMD website since they are not entirely familiar with Linux coding. 

I fully understand that the chances of not  regaining a past GUI with  older kernals is not zero but still possible, and that any changes incurs system-wide changes to the old kernals, and that having to try to regain the old GUI  involves going through GRUB should I not be able to regain the old GUI for the older kernals. 

Rather than attempt to chance/risk installing the proprietary drivers and _potentially_ having subsequent problems to deal with, I think what I will do is just un-install the new kernal using 

```
sudo apt-get autoremove linux-image-linux-image-3.5.0-25-generic
```And then just wait for a hoped for improved kernal image over the* linux-image-3.5.0-25-generic*. Perhaps an eventual and future *XXXX-26* kernal that might resolve such issues. 

Hopefully, the Ubuntu coders are also familiar with a rash of problems encountered by Ubuntu users of this newer released kernal and release any hoped-for improved kernal image. 

Regardless, I would like to ask one other question. If/when un-installing this newer kernal, does that also remove any and all other updates that came with that kernal. For example, I recall in the details drop-down menu that there were also some compat-wireless updates as well. So in having asked this question would such an un-install also involve removing any or all of the updates that _came_ with that kernal?

In addition, as this newer kernal release ```
linux-image-3.5.0-25-generic                     **3.5.0-25.38 **                              amd64        Linux kernel  image for version 3.5.0 on 64 bit x86 SM 
```being installed on my system and when going to [http://www.ubuntuupdates.org/package/canonical_kernel_team/precise/main/base/linux-image-3.5.0-25-generic ]("http://www.ubuntuupdates.org/package/canonical_kernel_team/precise/main/base/linux-image-3.5.0-25-generic")

I do not really find much to read on what the details were even after doing a Google search on the details of said kernal release. Is there another location that you might be aware of, of where I can go to see what the details were of the *-25 kernal*. All I really read is 

> Also includes the corresponding System.map file, the modules built by the 
packager, and scripts that try to ensure that the system is not left in an 
unbootable state after an update.Also, I read that, that release says it is for Precise. As I am using 12.10 Quantal, does such a release description by default involve Quantal?

**EDIT:** I am curious about something. In determining what might have gone wrong, does this output help to determine what might be conflicting with said newer kernal?

```
**user@user-desktop:~$ sudo tail -n 30 /var/log/dpkg.log**
2013-02-21 07:45:43 purge libvlccore5:amd64 2.0.5-0ubuntu0.12.10.1 <none>
2013-02-21 07:45:43 status config-files libvlccore5:amd64 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:43 status config-files libvlccore5:amd64 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:43 status config-files libvlccore5:amd64 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:43 status config-files libvlccore5:amd64 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:43 status config-files libvlccore5:amd64 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:43 status not-installed libvlccore5:amd64 <none>
2013-02-21 07:45:43 status installed vlc-data:all 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:44 remove vlc-data:all 2.0.5-0ubuntu0.12.10.1 <none>
2013-02-21 07:45:44 status half-configured vlc-data:all 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:44 status half-installed vlc-data:all 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:44 status triggers-pending hicolor-icon-theme:all 0.12-1ubuntu2
2013-02-21 07:45:44 status half-installed vlc-data:all 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:44 status config-files vlc-data:all 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:44 purge vlc-data:all 2.0.5-0ubuntu0.12.10.1 <none>
2013-02-21 07:45:44 status config-files vlc-data:all 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:44 status config-files vlc-data:all 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:45 status config-files vlc-data:all 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:45 status config-files vlc-data:all 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:45 status config-files vlc-data:all 2.0.5-0ubuntu0.12.10.1
2013-02-21 07:45:45 status not-installed vlc-data:all <none>
2013-02-21 07:45:45 trigproc man-db:amd64 2.6.3-1 <none>
2013-02-21 07:45:45 status half-configured man-db:amd64 2.6.3-1
2013-02-21 07:45:46 status installed man-db:amd64 2.6.3-1
2013-02-21 07:45:46 trigproc libc-bin:amd64 2.15-0ubuntu20.1 <none>
2013-02-21 07:45:46 status half-configured libc-bin:amd64 2.15-0ubuntu20.1
2013-02-21 07:45:47 status installed libc-bin:amd64 2.15-0ubuntu20.1
2013-02-21 07:45:47 trigproc hicolor-icon-theme:all 0.12-1ubuntu2 <none>
2013-02-21 07:45:47 status half-configured hicolor-icon-theme:all 0.12-1ubuntu2
2013-02-21 07:45:55 status installed hicolor-icon-theme:all 0.12-1ubuntu2
user@user-desktop:~$
```

These are all from yesterday's date. Any way that I can go back in history to see/post if necessary what might be log results if the above output is of any help even?


.

---

### Post by DuckHook on 2013-02-22
Your dpkg log looks normal but you've shown only a small segment. Please don't post the whole thing because it is massive and I haven't the time to review it.

I find it too heavy going to read all of the changes made from one kernel update to another, and just install them as they come up. Your doing so makes you a keener and a budding guru. Therefore, I can't really help you with your question except to point out that the 3.5.x kernel series was meant for use with Quantal, so I would assume that they would apply.

It's good you are aware that your decision to stick with an earlier kernel means having to go through the same reversion routine with every kernel update. If you are okay with this, then no problem. If feeling especially adventurous, you may wish to pin your old kernel. Instructions are in [this]("http://ubuntuforums.org/showthread.php?t=2073529") thread. However, if feeling this is a pain, then read what follows:

Don't be overly worried about installing the proprietary drivers either, so long as they are the versions in the repositories. These have generally been tested quite thoroughly. Millions use them with no ill effects. For what it's worth, I actually use the bleeding-edge driver from AMD because I am forced to (the older ones in the repositories don't work for one of my new video cards), but I am confident in my ability to recover if something goes wrong. The important thing is to back up properly, all of /home if possible, and you can then afford to experiment. What's the worst that can happen with good backups? You spend 20 minutes reinstalling Ubuntu.

Happy Ubuntuing!

---

### Post by Hodevah on 2013-02-22
I have a partial success to report. Things are looking up after I activated the *fglrx *proprietary drivers via Additional Drivers in Software Sources. 

Upon entering Ubuntu through the newer kernal, graphics were dramatically improved. Graphics were perfect. 

However, cursor/mouse problems remain. 

Solutions I attempted to find a remedy for:

(1) switching USB transievers to separate ports. Both from 3.0 to 2.0 were to no effect. 
(2) switching to a corded mouse to no effect. Switching to 3 separate ports for each mouse to no effect .
(3) ctrl-alt-t to no effect.
(4) random key combos to no effect.
(5) hard boot-off to Recovery Mode for *image-3.5.0-25-generic  *to see if I could effect something through there to no effect. Neither arrow keys, ENTER, ESC, number keys, nor random key combos to no effect
(6) cursor/blinking line for login credentials visible and blinking; however, as stated already unable to move mouse over for effecting any login credentials to no effect. 

At least the cup is half full now, eh?  :D

PS. You were right about the idea of not being overly worried. I just could not help it. Anyway. What ideas might you have next on the issue of the mouse not being able to move now that one of two problems is solved?


EDIT: I have done a bit of research on the issue of cursors not being able to move in Linux and I have not found anything relevant. There was an issue at the LaunchPad Bugs *#1040550 *which had _some _but _not direct or point by point_ resemblance to my problem. That solution offered there was to no effect and I doubt that it would for me as well. 

There does not seem to be a whole lot of Googling available for this mouse problem for Linux. What about a *.conf *file on my system somewhere? Would having to go to a *.conf* file somewhere and editing some lines help? If so, honestly, I don't know where to look nor where to begin. Continuing to research.


.

---

### Post by Hodevah on 2013-02-25
Bump. 
Anyone?

---

### Post by Hodevah on 2013-02-27
I am really quite wanting to get this resolved.

 I had a microsoft mouse that I was using. I went to use a Logitech wireless mouse also with  no effect. 

I think that there must be something wrong with this kernal. Regardless, I would still like to know if there is a way for me to have this resolved. 

Maybe there is some kind of configuration file found in Ubuntu for a user's mouse. 

Anyone?

---

### Post by Hodevah on 2013-03-01
Managed to finally solve this problem on my own. Uninstalled .25. And re-installed .25. Simple. What a crazy problem.:confused:
Nevertheless. It is solved/

---


---
title: "[SOLVED] onother poor noob with compiz peobloms on his laptop... suprize!"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by SchindlerShadow on 2008-07-10
ok well iv have ubuntu for a while on my desktop for quite a while, and now iv just managed to put it onto my laptop, after i found a wireless chip that works with ubuntu iv pretty much got it running good :KS . but i would much appreciate it if some1 could help me get compiz working. :( as usaual it says desktop effects could not be enabled :lolflag: . ahhhhh :mad: , i hate this sentence! its a hp compaq nx9008 thats really all i know about the laptop:confused: . i need some1 to help me getting this to work! thank you! ](*,)

---

### Post by swisscow on 2008-07-10
First step - have you loaded the graphics driver for your laptop?

---

### Post by aktiwers on 2008-07-10
What is your output of:
```
glxinfo | grep rendering
```

---

### Post by iaculallad on 2008-07-10
On your terminal:

```
compiz
```

and post the displayed message/texts.

---

### Post by SchindlerShadow on 2008-07-10
glxinfo | grep rendering says 
direct rendering: Yes 
compiz says: 
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 
and thx 4 posting =) (btw thats not in it lol)
and no the hardwhere drivers say i dount need 1 thx 4 helping tho!

---

### Post by anewguy on 2008-07-10
Post the output of:

lspci


Also, what does it say in your xorg.conf file for the adapter type?

---

### Post by SchindlerShadow on 2008-07-10
lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

hopefully this helps help me! thx for helping! and iidk wat xorg.conf is....

---

### Post by anewguy on 2008-07-10
Try following page 2 in this thread (hopefully the link takes you to page 2 already):

[http://ubuntuforums.org/showthread.php?t=854988]("http://ubuntuforums.org/showthread.php?t=854988")

Page 2 of the thread has 2 fixes - one for your desktop effects, the second for a long delay black screen at boot.

I think this will fix your problem - if not please post back!  :)

---

### Post by SchindlerShadow on 2008-07-10
ummm thats this page.... lol?

---

### Post by aktiwers on 2008-07-10
> **anewguy said:**
> Try following page 2 in this thread (hopefully the link takes you to page 2 already):

[http://ubuntuforums.org/showthread.php?t=854988](http://ubuntuforums.org/showthread.php?t=854988)

Page 2 of the thread has 2 fixes - one for your desktop effects, the second for a long delay black screen at boot.

I think this will fix your problem - if not please post back!  :)

:lolflag:

---

### Post by SchindlerShadow on 2008-07-10
????? help?

---

### Post by anewguy on 2008-07-10
Jeez do I feel stupid!!  I hope of you at least got a good laugh out of my copy/paste error!!  :):)

Now, IF I did it right this time, the 2nd page in this thread, the 3rd entry down posted by wargames should solve your problem. 

Sorry about that other post - I feel like a fool!!  :lolflag:[http://ge.ubuntuforums.com/showthread.php?t=579596&page=2]("http://ge.ubuntuforums.com/showthread.php?t=579596&page=2")

God I hope I got that right!! :)

---

### Post by SchindlerShadow on 2008-07-10
ook.... so... how do i do wat wargames posted? oh and thx 4 fixin that! lol!

---

### Post by anewguy on 2008-07-10
For the first section - getting 3D and compiz working, you will need to edit your xorg.conf file.  Since I don't know how much you know, I'll do this as simple as I can and ask that you forgive me if it is too simple.

(1) Open a terminal window (some call it the command prompt) via:

Click "Applications", scroll down to "Accessories", then over and down to "Terminal" and click.

You should have a window open up with a prompt on it.

(2) Type the following in that window:

cd /etc/X11  <enter>

sudo gedit xorg.conf   <enter>  (Yes, some people will say you should use gksudo, but this has always worked fine for me with no problems).  enter in your normal password when prompted.  The "sudo" stands for "super user do", meaning run the command in the highest permissions mode on the system.  You have to do this with xorg.conf (and other files you may run into later) since you don't "own" that file.

This will have opened the xorg.conf file for editing.

Scan that file, and in particular look for the "Section "Device"" part.  Be sure everything in that section, between Section Device and EndSection matches what is in wargames post.  The easiest way may be to just copy/paste the following directly on top of yours:

Section "Device"
Identifier "Generic Video Card"
Driver "ati"
BusID "PCI:1:5:0"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "true"
EndSection


Next you want to find the Section "Monitor".  It should also be changed to match that from wargames.  Again, the easiest way may be to copy/paste the following directly on top of yours:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Option "LVDSBiosNativeMode" "false"


As mentioned in wargames post, it is important that this section is included as well.  It normally appears at the end of the file - just make sure you have one that matches:

Section "DRI"
Mode 0666
EndSection

Now "Save" the file, exit the editor, and for ease, just reboot.

After the reboot, see if you can get compiz going - try something like the wobbly windows just to start.  You will probably need to add the Advanced Desktop Settings via synaptic - I think it's called "compizconfig-settings-manager".  Once you have installed this it should be easy to try out compiz via "System/Preferences/Advanced Desktop Effects Settings".

Let us know how that works out.  After that part is working, we can move on to the black screen showing for a while at boot.  One thing at a time! :)

Dave :)

---

### Post by anewguy on 2008-07-10
I've GOT to head for bed right now - it's 3:42 a.m. here and I need to be at a meeting by 9 a.m..  I'll check back later Thursday and see how things went.

Dave :)

---

### Post by drmorris on 2008-07-10
I have the same problem as schindlershadow

Compaq nx9010 with the same lspci output for the graphics:

VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

(I have managed to get ubuntu 8.04 with compiz cube working well on my *desktop* P4 with 128Mb nVidia using the restricted drivers, and also managed to get Netgear Wireless card working on this laptop using ndisgtk)

This laptop, however, will not play the game. Envyng does not work either. I have tried some of the xorg edits and had to reinstall ubunut twice after the mess it made

I am a complete newbie but am picking up some lingo. In the output of lshw the *display is UNCLAIMED - does this mean no working driver found?

Is there no driver for this older card to give a little boost? Help appreciated

---

### Post by anewguy on 2008-07-10
Well, the portion I referenced is the main starting point.  Further on in the thread it mentions removing the flgrx driver and some other things.  Follow deeper into that thread and try some of the other things that wargames suggests.  :)

---

### Post by SchindlerShadow on 2008-07-10
> **anewguy said:**
> For the first section - getting 3D and compiz working, you will need to edit your xorg.conf file.  Since I don't know how much you know, I'll do this as simple as I can and ask that you forgive me if it is too simple.

(1) Open a terminal window (some call it the command prompt) via:

Click "Applications", scroll down to "Accessories", then over and down to "Terminal" and click.

You should have a window open up with a prompt on it.

(2) Type the following in that window:

cd /etc/X11  <enter>

sudo gedit xorg.conf   <enter>  (Yes, some people will say you should use gksudo, but this has always worked fine for me with no problems).  enter in your normal password when prompted.  The "sudo" stands for "super user do", meaning run the command in the highest permissions mode on the system.  You have to do this with xorg.conf (and other files you may run into later) since you don't "own" that file.

This will have opened the xorg.conf file for editing.

Scan that file, and in particular look for the "Section "Device"" part.  Be sure everything in that section, between Section Device and EndSection matches what is in wargames post.  The easiest way may be to just copy/paste the following directly on top of yours:

Section "Device"
Identifier "Generic Video Card"
Driver "ati"
BusID "PCI:1:5:0"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "true"
EndSection


Next you want to find the Section "Monitor".  It should also be changed to match that from wargames.  Again, the easiest way may be to copy/paste the following directly on top of yours:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Option "LVDSBiosNativeMode" "false"


As mentioned in wargames post, it is important that this section is included as well.  It normally appears at the end of the file - just make sure you have one that matches:

Section "DRI"
Mode 0666
EndSection

Now "Save" the file, exit the editor, and for ease, just reboot.

After the reboot, see if you can get compiz going - try something like the wobbly windows just to start.  You will probably need to add the Advanced Desktop Settings via synaptic - I think it's called "compizconfig-settings-manager".  Once you have installed this it should be easy to try out compiz via "System/Preferences/Advanced Desktop Effects Settings".

Let us know how that works out.  After that part is working, we can move on to the black screen showing for a while at boot.  One thing at a time! :)

Dave :)

ook... i did this and it made no change watso ever.... it still says desktop effects could not be actavated! help???? :confused:

---

### Post by anewguy on 2008-07-10
Follow my latest post - those changes are a starting point, and you'll want to leave them in.  Read further into the link I sent and you will see such things as being sure the ATI driver is loaded and that the flgrx driver has been removed.  :)

---

### Post by SchindlerShadow on 2008-07-12
so..... can u help me do that? glxgears | grep direct works, so idk y compiz dosent, thire is no 5 min black scren when i boot..... i just want compiz to work.... plz help me some1!

---

### Post by anewguy on 2008-07-12
If you do the following in a terminal window:

ps -e


do you see compiz and compiz-decoration running?

do you have multiple desktops enabled?

:)

---

### Post by SchindlerShadow on 2008-07-12
ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:02 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:01 events/0
    7 ?        00:00:00 khelper
   41 ?        00:00:01 kblockd/0
   44 ?        00:00:08 kacpid
   45 ?        00:00:00 kacpi_notify
  120 ?        00:00:00 kseriod
  158 ?        00:00:00 pdflush
  160 ?        00:00:01 kswapd0
  203 ?        00:00:00 aio/0
 1460 ?        00:00:00 khpsbpkt
 1473 ?        00:00:01 ata/0
 1480 ?        00:00:00 ata_aux
 1483 ?        00:00:00 ksuspend_usbd
 1490 ?        00:00:00 khubd
 1512 ?        00:00:00 knodemgrd_0
 1516 ?        00:00:00 scsi_eh_0
 1520 ?        00:00:00 scsi_eh_1
 2269 ?        00:00:00 scsi_eh_2
 2271 ?        00:00:00 scsi_eh_3
 2519 ?        00:00:00 scsi_eh_4
 2522 ?        00:00:02 usb-storage
 2531 ?        00:00:04 kjournald
 2585 ?        00:00:00 scsi_eh_6
 2586 ?        00:00:00 usb-storage
 2740 ?        00:00:00 udevd
 3135 ?        00:00:00 kgameportd
 3219 ?        00:00:00 kpsmoused
 4557 tty4     00:00:00 getty
 4558 tty5     00:00:00 getty
 4562 tty2     00:00:00 getty
 4563 tty3     00:00:00 getty
 4565 tty6     00:00:00 getty
 4733 ?        00:00:00 acpid
 4770 ?        00:00:00 kondemand/0
 4843 ?        00:00:02 syslogd
 4898 ?        00:00:01 dd
 4900 ?        00:00:01 klogd
 4922 ?        00:00:01 dbus-daemon
 4938 ?        00:00:00 NetworkManager
 4952 ?        00:00:00 NetworkManagerD
 4965 ?        00:00:00 system-tools-ba
 4985 ?        00:00:00 avahi-daemon
 4986 ?        00:00:00 avahi-daemon
 5024 ?        00:00:00 cupsd
 5079 ?        00:00:00 nmbd
 5081 ?        00:00:00 smbd
 5101 ?        00:00:00 smbd
 5162 ?        00:00:06 dhcdbd
 5181 ?        00:00:01 hald
 5184 ?        00:00:00 console-kit-dae
 5246 ?        00:00:00 hald-runner
 5265 ?        00:00:00 hald-addon-acpi
 5277 ?        00:00:01 hald-addon-inpu
 5300 ?        00:00:01 hald-addon-stor
 5303 ?        00:00:06 hald-addon-stor
 5306 ?        00:00:03 hald-addon-stor
 5345 ?        00:00:00 hcid
 5351 ?        00:00:00 btaddconn
 5352 ?        00:00:00 btdelconn
 5366 ?        00:00:00 bluetoothd-serv
 5367 ?        00:00:00 krfcommd
 5397 ?        00:00:00 bluetoothd-serv
 5403 ?        00:00:00 gdm
 5478 ?        00:00:00 atd
 5496 ?        00:00:00 cron
 5586 tty1     00:00:00 getty
 5686 ?        00:00:07 gconfd-2
 5816 ?        00:00:00 dbus-daemon
 5861 ?        00:00:00 gvfsd
 5877 ?        00:00:01 gvfs-fuse-daemo
 5893 ?        00:00:00 trackerd
 5909 ?        00:00:00 gvfsd-burn
 5924 ?        00:00:05 gvfsd-trash
 8053 ?        00:00:02 prboom
 8486 ?        00:00:00 gvfsd-computer
 8988 ?        00:00:00 gvfsd-network
 8990 ?        00:00:00 gvfsd-smb-brows
 8993 ?        00:00:00 gvfsd-dnssd
 9006 ?        00:00:02 gvfsd-smb
19547 ?        00:00:00 dhclient
19986 ?        00:00:00 gdm
20028 tty7     00:10:10 Xorg
20052 ?        00:00:00 gnome-keyring-d
20053 ?        00:00:00 x-session-manag
20176 ?        00:00:00 seahorse-agent
20182 ?        00:00:00 dbus-daemon
20183 ?        00:00:02 gnome-settings-
20189 ?        00:00:14 pulseaudio
20192 ?        00:00:00 gconf-helper
20201 ?        00:00:14 gnome-screensav
20208 ?        00:00:50 gnome-panel
20210 ?        00:00:29 nautilus
20217 ?        00:00:00 bonobo-activati
20222 ?        00:00:00 gvfsd
20239 ?        00:00:00 bluetooth-apple
20242 ?        00:00:09 update-notifier
20245 ?        00:00:00 evolution-alarm
20246 ?        00:00:00 tracker-applet
20250 ?        00:00:00 trackerd
20255 ?        00:00:00 python
20256 ?        00:00:13 nm-applet
20257 ?        00:00:00 gnome-volume-ma
20259 ?        00:00:00 gnome-power-man
20269 ?        00:00:01 trashapplet
20275 ?        00:00:31 multiload-apple
20280 ?        00:00:04 stickynotes_app
20283 ?        00:00:01 gweather-applet
20288 ?        00:00:02 gvfsd-trash
20291 ?        00:00:00 gvfsd-burn
20310 ?        00:00:39 geyes_applet2
20314 ?        00:00:01 mixer_applet2
20316 ?        00:00:01 fast-user-switc
20437 ?        01:20:20 firefox
21214 ?        00:00:00 scsi_eh_7
21215 ?        00:00:00 usb-storage
21314 ?        00:00:00 hald-addon-stor
21322 ?        00:00:00 hald-addon-stor
21324 ?        00:00:00 hald-addon-stor
21326 ?        00:00:00 hald-addon-stor
21805 ?        00:00:03 gnome-terminal
21807 ?        00:00:00 gnome-pty-helpe
21808 pts/0    00:00:00 bash
23453 ?        00:00:09 metacity
23625 ?        00:00:00 gnome-vfs-daemo
23908 ?        00:00:00 winbindd
23909 ?        00:00:00 winbindd
24424 ?        00:00:00 pdflush
24472 ?        00:00:00 gvfsd-computer
25626 ?        00:00:00 pointer-capture
25663 ?        00:00:00 SystemToolsBack
25772 ?        00:00:00 ntpd
26556 ?        00:00:05 python
26576 pts/0    00:00:00 ps

and yes i have 4 desktops enabled.

---

### Post by aktiwers on 2008-07-12
Looks like you are on Metacity.. try this:
```
compiz --replace
```

---

### Post by SchindlerShadow on 2008-07-12
> **aktiwers said:**
> Looks like you are on Metacity.. try this:
```
compiz --replace
```

compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

:confused::confused::confused::confused:

---

### Post by aktiwers on 2008-07-12
> **SchindlerShadow said:**
> compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

:confused::confused::confused::confused:

Ahh well...

Looks like they fix the issue here:
[http://ubuntuforums.org/showthread.php?t=627088](http://ubuntuforums.org/showthread.php?t=627088)

---

### Post by SchindlerShadow on 2008-07-12
can u help me do wat they seaid? cuz i dount get it..... lol?

---

### Post by aktiwers on 2008-07-12
Sure, post the output of:
```
compiz
```

and 
```
fglrxinfo
```

And I will help you..  but I am afk for about 30 mins.. need to go grab some burgers :D

---

### Post by SchindlerShadow on 2008-07-12
> **aktiwers said:**
> Looks like you are on Metacity.. try this:
```
compiz --replace
```

omg sorry! i did it on wrong comp XD :lolflag:

 ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   41 ?        00:00:00 kblockd/0
   44 ?        00:00:03 kacpid
   45 ?        00:00:00 kacpi_notify
  116 ?        00:00:00 kseriod
  147 ?        00:00:00 pdflush
  148 ?        00:00:00 pdflush
  149 ?        00:00:00 kswapd0
  190 ?        00:00:00 aio/0
 1490 ?        00:00:00 ksuspend_usbd
 1495 ?        00:00:00 khubd
 1521 ?        00:00:00 ata/0
 1525 ?        00:00:00 ata_aux
 2431 ?        00:00:00 kjournald
 2634 ?        00:00:02 udevd
 2820 ?        00:00:00 pccardd
 2875 ?        00:00:00 kpsmoused
 4231 tty4     00:00:00 getty
 4232 tty5     00:00:00 getty
 4236 tty2     00:00:00 getty
 4237 tty3     00:00:00 getty
 4242 tty6     00:00:00 getty
 4410 ?        00:00:00 acpid
 4447 ?        00:00:00 kondemand/0
 4521 ?        00:00:00 syslogd
 4573 ?        00:00:00 dd
 4575 ?        00:00:00 klogd
 4597 ?        00:00:04 dbus-daemon
 4613 ?        00:00:01 NetworkManager
 4627 ?        00:00:00 NetworkManagerD
 4640 ?        00:00:00 system-tools-ba
 4660 ?        00:00:00 avahi-daemon
 4661 ?        00:00:00 avahi-daemon
 4699 ?        00:00:00 cupsd
 4789 ?        00:00:02 dhcdbd
 4808 ?        00:00:06 hald
 4811 ?        00:00:00 console-kit-dae
 4873 ?        00:00:00 hald-runner
 4886 ?        00:00:00 hald-addon-inpu
 4895 ?        00:00:00 hald-addon-acpi
 4912 ?        00:00:02 hald-addon-stor
 4955 ?        00:00:00 hcid
 4965 ?        00:00:00 btaddconn
 4966 ?        00:00:00 btdelconn
 4978 ?        00:00:00 bluetoothd-serv
 4979 ?        00:00:00 bluetoothd-serv
 4982 ?        00:00:00 krfcommd
 5019 ?        00:00:00 gdm
 5022 ?        00:00:00 gdm
 5026 tty7     00:19:45 Xorg
 5079 ?        00:00:00 atd
 5093 ?        00:00:00 cron
 5183 tty1     00:00:00 getty
 5304 ?        00:00:06 gconfd-2
 5313 ?        00:00:00 gnome-keyring-d
 5314 ?        00:00:00 x-session-manag
 5409 ?        00:00:00 seahorse-agent
 5413 ?        00:00:00 dbus-daemon
 5414 ?        00:00:05 gnome-settings-
 5427 ?        00:00:13 pulseaudio
 5430 ?        00:00:00 gconf-helper
 5453 ?        00:00:21 gnome-screensav
 5460 ?        00:00:44 gnome-panel
 5461 ?        00:00:24 nautilus
 5468 ?        00:00:00 bonobo-activati
 5471 ?        00:00:00 gvfsd
 5472 ?        00:00:00 bluetooth-apple
 5475 ?        00:00:03 update-notifier
 5479 ?        00:00:00 tracker-applet
 5481 ?        00:00:00 evolution-alarm
 5484 ?        00:00:00 trackerd
 5491 ?        00:00:00 python
 5493 ?        00:00:00 gnome-volume-ma
 5494 ?        00:01:08 nm-applet
 5496 ?        00:00:07 gnome-power-man
 5500 ?        00:00:00 gvfs-fuse-daemo
 5537 ?        00:00:02 notification-da
 5556 ?        00:00:00 gvfsd-burn
 5601 ?        00:00:02 trashapplet
 5610 ?        00:00:03 gnome-brightnes
 5625 ?        00:00:00 gvfsd-trash
 5709 ?        00:00:04 mixer_applet2
 5714 ?        00:00:03 fast-user-switc
 7058 ?        00:07:49 firefox
 7463 ?        00:00:07 gnome-terminal
 7465 ?        00:00:00 gnome-pty-helpe
 7466 pts/0    00:00:00 bash
 7907 ?        00:00:10 gnome-appearanc
 7908 ?        00:00:09 gnome-appearanc
 7952 ?        00:00:05 metacity
 7957 ?        00:00:00 rtl8187
 7997 ?        00:00:00 wpa_supplicant
 8000 ?        00:00:00 dhclient
 8070 pts/0    00:00:00 ps


 compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

compiz
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found


and still desktop effects could not be enabled........... :confused::confused::confused::confused:

---

### Post by aktiwers on 2008-07-12
Okay, what if you:
```
sudo apt-get install xserver-xgl
```Logout and log back in
Still the same? And what ATI card do you have? :)

---

### Post by SchindlerShadow on 2008-07-13
> **aktiwers said:**
> Okay, what if you:
```
sudo apt-get install xserver-xg
```Logout and log back in
Still the same? And what ATI card do you have? :)

i thank you vary much! it works! now i need ur help again... XD my desktop also has a simaler problem, i tried xserver.... but it still says desktop effects could not be enabled! the info i posted up by mistake is this computers info. i would vary like for compiz to work on is comp sense it is much faster than to laptop, compiz would look bettr! thx 4 helping!!!!! :):):) :guitar:

---

### Post by aktiwers on 2008-07-13
> **SchindlerShadow said:**
> i thank you vary much! it works! now i need ur help again... XD my desktop also has a simaler problem, i tried xserver.... but it still says desktop effects could not be enabled! the info i posted up by mistake is this computers info. i would vary like for compiz to work on is comp sense it is much faster than to laptop, compiz would look bettr! thx 4 helping!!!!! :):):) :guitar:
No problem ! Im glad it worked!

Now I need to know what video card you have in this machine?
And again what is your output of:
```
glxinfo | grep rendering
```

Edit:
also this is a good guide to get started with compiz
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by SchindlerShadow on 2008-07-13
ok this is on the desktop btw thx 4 helping me!

glxinfo | grep rendering
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
direct rendering: Yes

and i have no idea what vid card this comp has... XD

---

### Post by Canis familiaris on 2008-07-13
> **SchindlerShadow said:**
> 
and i have no idea what vid card this comp has... XD
To know your video card:
```
lspci | grep VGA
```

---

### Post by aktiwers on 2008-07-13
hmm okay..  can you post the output of:
```
lspci
```

---

### Post by SchindlerShadow on 2008-07-13
hope this helps!

 lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

lol its alot!

---

### Post by aktiwers on 2008-07-13
After doing some research it seams like you are in extrem bad luck. I actually think that it is not possible to run compiz on that card do to bad support from the vendor.

Please someone correct me if I am wrong, but this is what I found everywhere.

Though I did find one person with the same card on Folongs blog that seams to be runnning compiz anyways?
[http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

Im sorry to say I do not know what to do. May I suggest you create a new post with the outputs I asked for, as people tent to skip reading posts with this many posts inside :)

---

### Post by SchindlerShadow on 2008-07-13
dam it..... its just like me to buy the comp w/ the unsupported gc, *shigh* if u really want to know u where my 3ed oppinon! the dude @ lunchpad, and the dude in the forms said that...... awwww oh well, do u know if something like barel will work? well ima sleep now. see u 2morrow! and thx 4 everything! =)

 ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: openchrome driver in use 

Would you like to know more? (Y/n) y

 The openchrome driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y

and no their wasent a proprietary driver......

---

### Post by Canis familiaris on 2008-07-13
@OP: 
I am sorry I cant hlp you with VIA but...
I see you are using Xgl on the other COMPUTER.
Can you play movies?
Do OpenGL apps run correctly?

Before trying this SAVE ALL OPEN DOCUMENTS. 
Go to terminal:
```
glxgears
```

Does glxgears run?
Or does X crash and you fall back to the login screen.

---

### Post by anewguy on 2008-07-13
Sorry taking so long getting back here.  Glad you got help from someone to get your laptop working in the interim.  You do need to know that you can't run compiz or berel desktop effects with the Via S3 IGP, including the "Chrome" series.  These processors simply do not support everything that is needed to do so.  You can get 3D working to some degree using the openchrome drivers.

:)

---

### Post by aktiwers on 2008-07-13
Yep Beryl wont run on that card either. Its not that the card sucks, rather its the Linux driver support from the vendor that sucks. I bet you could run both Beryl and Compiz on that card if it had good driver support.

---

### Post by SchindlerShadow on 2008-07-16
> **anewguy said:**
> Sorry taking so long getting back here.  Glad you got help from someone to get your laptop working in the interim.  You do need to know that you can't run compiz or berel desktop effects with the Via S3 IGP, including the "Chrome" series.  These processors simply do not support everything that is needed to do so.  You can get 3D working to some degree using the openchrome drivers.

:)

to what degree? explane plz? :confused::confused::confused:

hey i herd about something called niswrapper, so that i can use micio$oft drivers.... u think that would work? and if it dose, can u help me do it? ty all 4 ur help!

---

### Post by SchindlerShadow on 2008-07-19
OMG! this is whats happening to me now! go to [http://ubuntuforums.org/showthread.php?p=5420169#post5420169](http://ubuntuforums.org/showthread.php?p=5420169#post5420169)     :mad::mad::mad::mad::mad:

---

### Post by painguin on 2011-09-27
Ok, this is a bit off topic but the closest I could find.  I was stuck in a boot loop and was able to fix it by using the command "sudo chmod a-x /usr/bin/compiz".  So basically I had to remove Compiz to fix my "boot loop" problem.  

Now, however, Compiz is gone even after I reinstalled it.  I ran "compiz --replace" and received the output "command not found".  The only window manager I can use is Metacity, I cannot change it through the compiz fusion icon either.  

I don't know what to do, I've managed to fix one issue with the help of a friend and now this.  Any suggestions???

Thanks, 

PAinguIN

---

### Post by aktiwers on 2011-09-27
This is a really old thread..  you should create a new one with your problem.

Sounds like you either don't have compiz installed or your drivers are not correctly installed.
You should create a new thread - and give the info from the commands earlier in this thread.

---


---
title: "laptop flicker screen"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by maazrizki on 2011-09-10
No matter which version of Linux I use I get flicker screen
following are few variants
LXDE alread installed
Xubunto 10.10 live cd
Crunchbang live cd
Lubuntu 10.10 live cd
etc.
It seem every thing  goes fine till gdm starts (i don't know what is gdm)
I had already disable video expansion.
here is lspic dump
I take this by using "ctrl-alt-f2" keys I learned on internet
this is LXDE debian isntall
 
```
00:00.0 Host bridge: Intel Corporation 82440MX Host Bridge (rev 10)
00:00.1 Multimedia audio controller: Intel Corporation 82440MX AC'97 Audio Controller
00:02.0 VGA compatible controller: Silicon Motion, Inc. SM720 Lynx3DM (rev a2)
00:07.0 ISA bridge: Intel Corporation 82440MX ISA Bridge (rev 01)
00:07.1 IDE interface: Intel Corporation 82440MX EIDE Controller
00:07.2 USB Controller: Intel Corporation 82440MX USB Universal Host Controller
00:07.3 Bridge: Intel Corporation 82440MX Power Management Controller
00:09.0 PCI bridge: Actiontec Electronic Inc Mini-PCI bridge (rev 11)
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rv 80)
01:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
01:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)
```
 
This is a old ASUS Laptop with RAM 192MB Pentium III, PhoenixBIOS 
This laptop works fine with Win2k or Win2k server
No internet connection
 
Does any of you gurus have any tricks up their sleves. :p

---

### Post by maazrizki on 2011-09-12
With same laptop I load old KNOPPIX KDE but New KNOPPIX gives me fliker.
 
MR :confused:

---

### Post by Toz on 2011-09-12
What model of Asus laptop is it?

What video driver is loaded in Old Knoppix versus New Knoppix? Try:
```
lspci -vnn
```
and look for VGA entry.

---

### Post by maazrizki on 2011-09-13
asus m8300 
I could not find VGA entry
 
however just lspci show this
VGA compatible controller: Silicon Motion, Inc. SM720 Lynx3DM (rev a2)

---

### Post by Toz on 2011-09-14
Can you post back the results of the **lspci -vnn** command? Both from when you're running the old knoppix amd the new knoppix? I'm interested in seeing the differences.

---

### Post by maazrizki on 2011-09-14
how do I take dump of lspci

---

### Post by Toz on 2011-09-14
Open a terminal window, and type in the command:
```
lspci -vnn | grep -A 10 VGA
```
Copy and paste the results back.

---

### Post by maazrizki on 2011-09-15
I'll try but remember these laptop is not connected to internet for that matter to even wireless network or wired where do I paste. Plus terminal will open in old knoppix 2 not in knoppix 6. knoppix 6 do not work. However knoppix 2 loads with KDE 3.1

---

### Post by maazrizki on 2011-09-15
may be I can send you screen pictures taken by iPod.

---

### Post by Toz on 2011-09-15
The screen pictures won't help (I believe you).

The results from those commands would. You could try:
```
lspci -vnn | grep -A 10 VGA > lspci.txt
```
and it will redirect the results of the command to a text file called "lspci.txt". Copy this file to a usb key then over to another computer that has internet access.

If terminals don't open, try Ctrl+Alt+F1 to go to full-screen command line. Ctrl+Alt+F7 should take you back to gui.

---

### Post by maazrizki on 2011-09-16
I understand that, see I am windows person, so be patient with me, which folder or which directory this file will be written to. Since everything is running from CD. Plus how do I see usb drive from terminal session? well I am sorry for all these simple questions, but I am kind of new here.
Thanks for help,

---

### Post by Toz on 2011-09-16
Ok. Just downloaded the Knoppix CD. Here's a step-by-step guide:

1. Boot the Live CD.

2. Plug in the usb key. A file manager window should open displaying the contents of the key. Move this window to the side for now.

3. Open a terminal window (3rd icon from the left on the bottom task bar) and execute the following command:
```
lspci -vnn | grep -A 10 VGA > ~/lspci.txt
```

4. Open a second file manager window (2bd icon from the left on the bottom task bar) - it should default to the home directory and you should see lspci.txt. 

5. Drag and drop the file lspci.txt from the window to the other window that opened up when you inserted the memory key.

Do this from both versions of Knoppix - the one that works and the one that flickers. What would be interesting to see, is the difference between the contents of the two files with respect to the drivers that are being used.

Another thing you can try, is when booting knoppix, at the **Knoppix:** prompt, enter:
```
knoppix norandr
```
and press enter to boot.

---

### Post by maazrizki on 2011-09-16
Fisrt the good Knoppix is 3.2
I did everything as written, file was created but when I try to write to USB pendrive dialog box says "Could not write to /mnt/sda1/lspci.txt"
So question how I enable to USB drive to enable to write?
 
For bad knoppix 6 I am going to try knoppix norandr command next
Thanks for helping

---

### Post by maazrizki on 2011-09-16
Finally I figure out how to copy file by mounting pen drive etc.
I am attaching both dumps
lspci.txt is from good running knoppix
lspci2.txt is from bad running knoppix
I hope this will give you some insight what is going on.

---

### Post by Toz on 2011-09-16
After all that, the files are not helpful. Can you do the same, but this time grab the /var/log/Xorg.0.log files?

Did **knoppix norandr** help?

---

### Post by maazrizki on 2011-09-16
okay no problem I'll try,
knoppix norandr did not help, I used it when after cd start and stops at login: prompt thats where I typed knoppoix norandr as soon as I hit enter knoppix went to same starting cycle with end flicker screen and bunch thin vertical lines.
One thing though if I go to tty using alt-f1 or alt-f2 I see prompt where I can use all sort of cli command. It seems linux load properly only graphic card has issue. But old knoppix start with KDE 3.1 what that means.

---

### Post by anewguy on 2011-09-17
Have you installed the driver for the SM720?  See [this]("http://manpages.ubuntu.com/manpages/natty/man4/siliconmotion.4.html")page for more information.  It links to a page you can download from.

This page also describes entried in xorg.conf.  While it says it's for natty (11.04), xorg.conf went away quite a while ago, replaced by a new means of determining things.  However, the information on this page - especially things like interlace - should be included in the appropriate new files.

Without the driver, you won't get far.

GDM that you asked about is Gnome Desktop Manager - the default "desktop"
you will use with ubuntu (others include kde, lxde).  The reason you don't see this until gdm starts is because until that time it is not running X-windows.  When GDM starts up it will use X to manage windows - without the driver for X all kinds of strange things can happen.

I will do some looking around to see if I can find how to include the options on that page in the new way X is configured.  You will still need to download and install the driver.

Dave ;)

---

### Post by anewguy on 2011-09-17
Try this:

sudo gedit /etc/X11/xorg.conf

add the entries as shown on the page I previously mentioned, then save the file.

logout and log in - did it do anything?

Dave ;)

EDIT:  According to [this]("https://wiki.ubuntu.com/X/Config") you should be able to just create an xorg.conf file with only the sections you need to override the defaults.

---

### Post by maazrizki on 2011-09-20
I am attaching xorg.conf file from knoppix 6.2, (the bad one)
 
:(

---

### Post by Toz on 2011-09-21
> **maazrizki said:**
> I am attaching xorg.conf file from knoppix 6.2, (the bad one)
 
:(

> 	# Driver (chipset) autodetect
If you have a chance, can you also post the **/var/log/Xorg.0.log** so we can see what driver was autodetected?

---

### Post by maazrizki on 2011-09-21
here we finally I figure out how to copy it. file was not getting loaded so I zipped it.
 
thanks a lot for help,
 
MR:)

---

### Post by Toz on 2011-09-22
Okay, so the "bad" (problematic) one is running with the Siliconmotion (SMI) driver. Now lets compare this with the older "good" version of knoppix.

---

### Post by maazrizki on 2011-09-22
I tried to look for those two file in older version I could not find them, i.e. Xorg.conf and Xorg.0.log. what was older name for these files or if it should be same where should I look for them.
 
MR :confused:

---

### Post by maazrizki on 2011-09-23
One more thing I found out about Old Knoppix I am using is running KDE 3.1 may be this info can help,
MR

---

### Post by Toz on 2011-09-23
Have a look at the cheat codes listed at this page: [http://www.knoppix.net/wiki/Cheat_Codes]("http://www.knoppix.net/wiki/Cheat_Codes").

Can you try the following and see if they work?
```

knoppix xmodule=fbdev
knoppix xmodule=vesa
knoppix xmodule=svga
```

Did you say that you're also having this screen flickering on ubuntu?

---

### Post by maazrizki on 2011-09-23
Yes also. Can you tell something more what is the differece b/w KDE and GNOME ?

---

### Post by Toz on 2011-09-23
Both are desktop environments (with their own window managers). They are the graphical front-ends that most people use on Linux boxes. There are other desktop environments and window managers, but these two are the most common.

Look here for a description of desktop environments: [http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments]("http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments")

and here for a description of the visual differences: [http://www.psychocats.net/ubuntu/kdegnome]("http://www.psychocats.net/ubuntu/kdegnome").

---

### Post by maazrizki on 2011-09-24
Only Linux which start without any problem is "damnSmallLinux" but it lack features.

---

### Post by Toz on 2011-09-24
Try booting the ubuntu live cd. Once in, run the following command on a terminal window to confirm that the siliconmotion driver is installed:
```
apt-cache policy xserver-xorg-video-siliconmotion
```

You can look at the **/var/log/xorg.0.log** file to see if the live cd is running the siliconmotion driver or another (vesa?).

You can enable the siliconmotion driver by creating an **/etc/X11/xorg.conf** file with the following contents:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "siliconmotion"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Log out and back in to see if it works.

---

### Post by maazrizki on 2011-09-28
out put of apt-cache policy xserver-xorg-video-siliconmotion
xserver-xorg-video-siliconmotion
Installed 1:1.7.3-2
Candidate: 1:1.7.3-2
Version table:
*** 1:1.7.3-2 0
     500 cdrom://[Debian GNU/Linux 6.0.2.1 _Squeeze_ - Official i386 xfce-lxde-CD Binary-1 20110626-15:45]/ squeeze/main io386 Packages
100 /var/lib/dpkg/status
this is same with live CD also, I'll put more stuff later
 
I also changed to xorg.conf

---

### Post by anewguy on 2011-09-28
Just thinking out loud here......

- perhaps the refresh rates need to be specified in xorg.conf

- perhaps, with the limited memory, the newer OS's are taking more memory leaving less for sharing with video.  this could result in flicker as the screens wouldn't be able to be swapped or not nearly as fast.  Damn Small Linux takes up very little memory, so this should leave more for the video, which would explain why there is no flicker there.  I'm sure given the age, etc., that this video adapter uses main memory, not dedicated video memory, so it relies on that window being large enough.  Check your BIOS - see where video memory is set to (like 4 or 8mb) and see if you can increase it in the BIOS, then try Ubuntu again.  You may need to keep allocating more to the video before it works.

Dave ;)

---

### Post by maazrizki on 2011-09-29
I think this is the answer, Video ram is shadow ram 384KB and system ram 640KB, extended momory is 195584KB, so I think it is useless to waste time on this machine. What do you think?
I should some other chanllenge to conqure
Thanks for all the help,
MR :)

---

### Post by maazrizki on 2011-09-29
When I almost gave up I went to I bios as a last attempt and change LCD mode to CRT mode, thinking it will take less memory. When I restarted debian which was on hard drive started working and then I put knoppix 6.2 cd that also start working. thanks for being patience with me.
Now I have another challenge i.e. configuring my PCMCI ciso card with WAP to connect wirless network. Maybe I should start new thread for this.
Thanks for all help,
MR :D
PS I might start linking Linux after all

---

### Post by anewguy on 2011-09-29
Glad you got it working!  I would start a new thread for your wireless, but before you do  - plug the adapter in and do an lspci in the terminal window and post the result back here.  I can get a head start trying to find something so maybe you won't have to wait too long (no promises, though !).

Dave ;)

---


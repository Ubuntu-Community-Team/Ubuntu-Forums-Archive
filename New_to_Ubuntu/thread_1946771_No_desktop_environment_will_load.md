---
title: "No desktop environment will load"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by steigerjb on 2012-03-25
Something really strange and terrible is going on with my Ubuntu.  When booting, I get as far as the LightDM login screen.  No matter what desktop environment I try logging with (Gnome Shell, fallback Gnome, Unity, or 2D Unity), all I get is a desktop wallpaper.  Can't right click or run Alt + F2 command prompt.

Do I have any options to fix besides reinstalling?

---

### Post by bogan on 2012-03-25
Hi!, **steigerj**b,

Have you a dual boot installation with Windows, direct install or wubi? and which version of Ubuntu, 11.10 ??

Do you get a Grub Boot menu?  If so, can you boot into the recovery mode to a Terminal command line login prompt?

Please Post details of your setup including Video Card.

Chao!, [B]bogan.

Edit: PS[/B] What does the 'wallpaper' you get look like ? The Login screen [B]?
[/B]

---

### Post by steigerjb on 2012-03-25
> **bogan said:**
> Hi!, **steigerj**b,

Have you a dual boot installation with Windows, direct install or wubi? and which version of Ubuntu, 11.10 ??

Do you get a Grub Boot menu?  If so, can you boot into the recovery mode to a Terminal command line login prompt?

Please Post details of your setup including Video Card.

Chao!, **bogan.**

Yes, I can see the grub menu.  Yes, I can go into recovery mode but don't know what to do there.  I'm running ubuntu 12.04 and Windows 7.  

Video card is nvidia gtx 580.

---

### Post by bogan on 2012-03-25
Hi!, **steigerjb**,

If you can boot to the terminal option in recovery mode, type your user name & 'Enter',  then your Password - nothing will show -  so be careful to get it right - & 'Enter'.

Then enter:```
 lspci       #  & press 'enter'.  
```Use the Edit menu to 'Select All' & 'Copy'.

Then paste the result ( Ctrl+v) to this Thread 'New Reply'; Select it, ie Highlight it, and click on the '#' symbol in the toolbar of the message edit box.

A lot depends on what CPU you have, if it is an Intel  sandybridge or ATI with integrated graphics as well as the Nvidia GTX580 PCI card, things will get a bit complicated.
Please Post details of CPU or computer and motherboard.

Is there any particular reason for choosing 12.04 ?  which is not yet released and only beta - not for beginners.

**Edit**: You did not say if it is a Direct install or with wubi.

Chao!, **bogan**.

---

### Post by d4m1r on 2012-03-25
Were you doing anything the last time it WAS working that could have screwed it up?

Boot into recover mode and try "sudo apt-get remove gdm" then "sudo apt-get install gdm". Worked for me when I faced a similar issue.

---

### Post by 23dornot23d on 2012-03-25
Could be as simple as running out of space - and the desktop not being able to
start ... need to get to a terminal and do a check .... from safe mode or .... 

If you can - check .... from the terminal mode ( Ctrl + Alt + F2 ) .... 

Type in .....
[B]
df[/B]



if you do not have enough space
on the drive and its 100 % full ...... then try freeing some ....  

**sudo apt-get autoclean**

---

### Post by bogan on 2012-03-26
> **d4m1r said:**
> Were you doing anything the last time it WAS working that could have screwed it up?

Boot into recover mode and try "sudo apt-get remove gdm" then "sudo apt-get install gdm". Worked for me when I faced a similar issue.OP is using 12.04, so it would be: 'lightdm', not:  'gdm'.

Chao!,** bogan**.

---

### Post by steigerjb on 2012-03-26
> **bogan said:**
> Hi!, **steigerjb**,

If you can boot to the terminal option in recovery mode, type your user name & 'Enter',  then your Password - nothing will show -  so be careful to get it right - & 'Enter'.

Then enter:```
 lspci       #  & press 'enter'.  
```Use the Edit menu to 'Select All' & 'Copy'.

Then paste the result ( Ctrl+v) to this Thread 'New Reply'; Select it, ie Highlight it, and click on the '#' symbol in the toolbar of the message edit box.

A lot depends on what CPU you have, if it is an Intel  sandybridge or ATI with integrated graphics as well as the Nvidia GTX580 PCI card, things will get a bit complicated.
Please Post details of CPU or computer and motherboard.

Is there any particular reason for choosing 12.04 ?  which is not yet released and only beta - not for beginners.

**Edit**: You did not say if it is a Direct install or with wubi.

Chao!, **bogan**.

I can't open a terminal in recovery.

I went into Ctrl Alt F1.  Tried installing updates and running

```
compiz --reset
unity --reset
gnome-panel --reset
```

With the "gnome-panel --reset", I got "Gtk-WARNING cannot open display".  Could that be the issue?

I am running 12.04 because I got sucked into being it was stable.  I want to beta test.

Not a wubi install.

---

### Post by steigerjb on 2012-03-26
> **d4m1r said:**
> Were you doing anything the last time it WAS working that could have screwed it up?

Boot into recover mode and try "sudo apt-get remove gdm" then "sudo apt-get install gdm". Worked for me when I faced a similar issue.

Last thing I did was [http://www.tuxgarage.com/2011/10/running-gnome-classic-with-compiz.html]("http://www.tuxgarage.com/2011/10/running-gnome-classic-with-compiz.html")

---

### Post by sandyd on 2012-03-26
> **steigerjb said:**
> Last thing I did was [http://www.tuxgarage.com/2011/10/running-gnome-classic-with-compiz.html](http://www.tuxgarage.com/2011/10/running-gnome-classic-with-compiz.html)
Theirs a reason for the "troubleshooting" section in the guide.

---

### Post by steigerjb on 2012-03-26
> **sandyd said:**
> Theirs a reason for the "troubleshooting" section in the guide.

Wow steigerjb, from the department of duh...

The tutorial didn't work so I decided to revert back.  I put mutter instead of gnome-wm.  We're good now.

3D Unity still won't load (2D will) but I don't really care at this point.  I wanted to beta test Unity, but oh well.

---

### Post by 23dornot23d on 2012-03-26
> 
I went into Ctrl Alt F1.  Tried installing updates and running
You should be able to get a desktop running from here with a little work .... 

because if you can get in with Ctrl+Alt+F1 and install updates then the system is still ok
as long as you are not getting a lot of errors back from the updates and if it was me  ....[B]

Check the graphics drivers are set up .....


[/B]> 
I put mutter instead of gnome-wm.  We're good now.

3D Unity still won't load (2D will) but I don't really care at this point.  I wanted to beta test Unity, but oh well.

[COLOR=Blue]Sounds as if the graphics driver is not set up .... if you can get in 2d mode now .....[/COLOR]

---

### Post by steigerjb on 2012-03-26
> **23dornot23d said:**
> You should be able to get a desktop running from here with a little work .... 

because if you can get in with Ctrl+Alt+F1 and install updates then the system is still ok
as long as you are not getting a lot of errors back from the updates and if it was me  ....

first try 

**startx**

Also what does df show ...... ( just want to know how much room you have on the drive )
[B]
df

[/B][COLOR=Blue]Sounds as if the graphics driver is not set up .... if you can get in 2d mode now .....[/COLOR]

Read my above post.  It's fixed now. :)  Thanks anyway. 

P.S. - I have over 600GB free space.

---

### Post by 23dornot23d on 2012-03-27
Yep sorry ... answered from previous page then saw you were almost there ....

The 3d not working is probably the graphics driver though .....

lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'

---

### Post by steigerjb on 2012-03-27
> **23dornot23d said:**
> Yep sorry ... answered from previous page then saw you were almost there ....

The 3d not working is probably the graphics driver though .....

I think System76's driver needs to be updated for 12.04.

---

### Post by 23dornot23d on 2012-03-27
Ok keep checking the Precise threads .....

I see your Video card is a nvidia gtx 580.

Some are ok others are still having problems though .... Vindsl seems ok with the
7600 gt .....

[http://ubuntuforums.org/showthread.php?t=1945730](http://ubuntuforums.org/showthread.php?t=1945730)


I upgraded - the gt540 is working on Linux 3.2.0-20-generic-pae

**lspci**

> 
keith@keith-K53SV:~$ [COLOR=Red]**lspci**[/COLOR]
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)                
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
**[COLOR=Blue]01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)[/COLOR]**
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
keith@keith-K53SV:~$ **[COLOR=Red]date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils[/COLOR]**
Tue Mar 27 15:04:27 CEST 2012
Ubuntu precise (development branch)
Linux 3.2.0-20-generic-pae
unity 5.8.0
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string:  3.0 Mesa 8.0.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Package `mesa-utils' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
keith@keith-K53SV:~$ 

[COLOR=Black][B]date && lsb_release -sd || cat  /etc/*release && uname -s -r && unity --version  && /usr/lib/nux/unity_support_test -p && dpkg -s  mesa-utils

sudo apt-get install mesa-utils

[/B]then using these commands will show if the driver is also working ok[B]

glxinfo
glxgears

[/B][/COLOR]> 
keith@keith-K53SV:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.275 FPS
300 frames in 5.0 seconds = 59.868 FPS
300 frames in 5.0 seconds = 59.848 FPS
300 frames in 5.0 seconds = 59.802 FPS
300 frames in 5.0 seconds = 59.906 FPS
300 frames in 5.0 seconds = 59.869 FPS



---


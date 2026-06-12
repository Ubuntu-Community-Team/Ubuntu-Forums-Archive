---
title: "LiveCD Demo fails using NVIDIA GeForce 6200 GPU"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by ledbright on 2011-09-18
LiveCD demo for Ubuntu 10.04 LTS runs the Ubuntu splash screen, then dumps to a white background with densely spaced multicolor vertical lines. Searches indicate that the problem is my EVGA Nvidia 6200 GPU's proprietary drivers. Downloaded three possible drivers, save to CD as well. I have no idea how to interrupt the Demo to try the drivers. I've used the "hit any key" during the splash screen to get the graphic interface, with f1-f6 options. No configuration helps. Multiple forum and Google searches have proved fruitless. Has anyone successfully run the 10.04 LTS demo with an Nvidia GeForce 6200?
also
(a) The LiveCD integrity is good, and successfully demos on a friends new laptop using the nouveau drivers
(b) My PC should be adequate, although a dinosaur:
------------------------------------------------------------------------    
Computer Profile Summary - Gateway 2000 PC
Operating System - Windows XP Professional Service Pack 3 (build 2600)
Processor - 1000 megahertz AMD Athlon
    32 kilobyte primary memory cache
    256 kilobyte secondary memory cache
    Not hyper-threaded                 
    Bus Clock: 100 megahertz
BIOS: American Megatrends Inc.
1280 Megabytes Usable Installed Memory
NVIDIA GeForce 6200 [Display adapter]
(c) Unless there's a good reason, I'm reluctant to try the install if I can't get a screen on the demo.

Thanks in advance for any assistance.

---

### Post by Lisiano on 2011-09-18
Put in the disk, boot, select Try Ubuntu, wait a bit, press Ctrl+Alt+F1-F6 and you should see a line like this ```
ubuntu@ubuntu:~$
``` then type ```
sudo /etc/init.d/gdm stop
``` which will stop Gnome. Install the drivers as per the instruction on NVidias page then INSTEAD of rebootin just type ```
sudo /etc/init.d/gdm start
```

You can replace sudo /etc/init.d/gdm with ```
sudo service gdm
``` if you wish. I prefer the earlier.

---

### Post by ledbright on 2011-09-18
Wow! Thanks for the immediate response. Unfortunately, I was unable to get to a point where I could enter code. The events were:
(a) Booted the LiveCD multiple times, having to hit the "any key" to get to the graphic display allowing me to select "Try Ubuntu"
(b) Hit "enter" with "Try Ubuntu" selected, then waited various amounts of time to try "ctrl+alt+f1-f6" using f6 predominately
(c) Screen goes black with small blinking cursor in the upper left screen. No code entry is allowed - the cursor just blinked, CD continued to be accessed, and eventually the same failure screen (white background/colored lines) popped up. Hard shutdown was the only way out.

I have a funny feeling I'm going to say "doh" when I'm finally successful, but this still seems quite a challenge at the moment. More suggestions are sincerely welcome. Thanks.

---

### Post by Lisiano on 2011-09-18
I am no expert on X servers (Seems like this is your problem) so you probably should wait until someone better than me shows up, if I find anything more I'll post here.

EDIT: Before you select Try Ubuntu, do you see it on a window with 2 buttons, "Try Ubuntu" and "Install Ubuntu" or you see it in a menu? If the earlier, we might make it work. IF the later.. Darn to my theory.
Also if you force it into a menu, try leaving it alone, it should go into a graphical prompt and ask if you want to "Try" or "Intsall" and also offer you to set up a WiFi connection.

---

### Post by anewguy on 2011-09-18
Yeah, what needs to be done is probably add "nomodeset" and possibly "VGA=771" to the boot line.  And therein lies the rub.  The LiveCD for Ubuntu comes up with the "graphical" selection and I see no way to edit the boot line.

So, what I would do:

Download the alternate CD - it's not a live CD, doesn't use a GUI but instead the old-style "terminal graphics".  Some call it a command line installation, but you don't really use the command line - just follow the screens.  There will be an option for detecting/setting up your video - definitely do that part - don't skip over it.  It's an interactive setup, so you don't just answer a few questions and walk away.  Also, as far as I know, there is no way to run this in the live test mode.  You may have to use a gparted CD to setup your partitions on the hard disk - I don't remember if the alternate CD asks about partitioning or not.

Dave ;)

---

### Post by Lisiano on 2011-09-18
I remember you can tell it boot options, when you force it into a menu (Pressing any key) you also need to press F6 for Other options, there you can select nomodeset.
Basically when you see something like a keyboard connected to a human, press any key, pick a language, press F6, tick nomodeset, continue with Trying or Installing.
Also yes, the alternative provides partitioning tools but they are not easy to use for average users.

---

### Post by anewguy on 2011-09-19
Guess when I just tried the 11.04 LiveCD before my post I must have pressed F6 in the wrong point in time as I never got any choices.  Oh well, the point is to try nomodeset, and since you have provided the means to edit the boot for the LiveCD and add the nomodeset as I mentioned - let's hope the OP tries that.

Thanks for the info!

Dave ;)

---

### Post by ledbright on 2011-09-20
Thanks for all the help. Sorry for the response delay. I did try the "hit any key" and "nomodeset" in my initial trials, but tried it again. The events are:
(a) "hit any key" and went to graphical screen with f1-f6 options
(b) chose f6 and "nomodeset" then "Try Ubuntu"
(c) Screen goes to small, then larger, blinking cursor on upper left of the screen
(d) Screen then reverts back to UBUNTU splash screen with blinking dots
(e) Screen then goes to alternating text and blank. The text is displayed for milliseconds (Welcome to UBUNTU 10.04 is about all I could glimpse - if that is even correct). The blank screen lasts for seconds.
(f) Hard reboot is required to get out of it.

So, I'll look into the alternate CD as suggested and see if my prospects improve. Thanks for your time and generous help so far. I'm not giving up.

---

### Post by ledbright on 2011-09-20
Well, my first "doh" has arrived. Trying the nomodeset option again, I now see the "Boot Options" line appear and that I can edit. The line is:

"Boot Options file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --"

I can scroll through it, edit it, but I don't know if I can enter multiple lines of code, or just modify this line. I tried adding /VGA=771 after quiet splash, but it went back to the milliseceond text screen mentioned in my last reply. However, this appears to be the line I need to modify in some way. Any ideas?

---

### Post by wildmanne39 on 2011-09-20
Hi, it is very simple most of the time and here is a link to a guide that shows you exactly how to change these options from a live cd.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Yes that is the line and you just try on parameter at a time.
Thank you

---

### Post by ledbright on 2011-09-20
Is this the appropriate modification to the "Boot Options" line to get the Nvidia 6200 to respond? (I'm not sure where to place the code)

"Boot Options file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash/acpi_osi= --"

---

### Post by wildmanne39 on 2011-09-20
Hi, this is a quote from the link I gave you.
> If you press the F6 key, a menu at the bottom will open allowing you to set kernel options with the space bar or enter key. You can close the menu with escape key and resume booting by selecting the option “try ubuntu without installing” (please note that session does allow you to install ubuntu once you found the kernel options cured your problem).

If you need to add kernel options not provided by the F6 menu, you can just type them in at the end of the boot options line.

Before you try any other options work
through the ones that are in the drop down list and you do not need to manually add them refer to the quote.
Thank you

---

### Post by ledbright on 2011-09-21
Thank you for the link. I've been using the f6 options, individually, as described. I either get the "failure" screen (white background/densely spaced vertically colored lines) requiring hard shutdown, or a locked UBUNTU splash screen.....may be I can manually rewrite the "Boot Options" line?..... or may be the answer is that the Ubuntu Demo will NOT work with Nvidia?

---

### Post by wildmanne39 on 2011-09-21
Hi, no that is not the case, I installed 2 weeks ago 10.04 on my laptop with 6150 nvidia card, I think I had to use acpi=off, and the same thing once I installed ubuntu for the first boot then I installed the driver and everything was good. 

I am not sure were it fails at, I will go back and read your post again from the start. 
Thank you

---

### Post by ledbright on 2011-09-22
SUCCESS!! Able to run Ubuntu LiveCD Demo with EVGA Nvidia GeForce 6200 GPU. Method I used:
(a) Booted with Ubuntu Live CD
(b) At initial screen, "hit any key" and went to graphical screen with f1-f6 options
(c) chose f6 and "nomodeset"
(d)* edited "boot options" line, deleting just "quiet splash" leaving:
"Boot Options file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz  --"
* Note: I had to leave (2) spaces after "initrd.lz", or it locked up again, e.g.
"initrd.lz<space><space>--"
(e) Selected "Try Ubuntu" <enter>
(f) Software loading commands listed, then Demo appeared.

I'm sure fluent users can come up with a refined approach, but I'm thrilled it worked. Thanks again for all the help and patience! I installed it - now on to installing the correct NVIDIA drivers

---

### Post by wildmanne39 on 2011-09-22
Hi, your welcome! I am glad you have it working.

Install the driver from restricted drivers and I recommend not installing the recommended one if there is one there older, like my 6150 is support by the 173 driver and the newer driver causes all kinds of problems.

With 10.04 the recommended driver may be okay, I am using 11.04.
 
If I was helpful would you consider clinking on the red link in my signature and supporting me for ubuntu membership? 

Also please mark the thread solved using the thread tools at the top of the page, when you have your driver in stalled.
Thank you

---

### Post by ledbright on 2011-09-24
Oops - marked thread as solved prematurely (doh) - had to re-mark as unsolved.
Thanks again wildmanne39 - definitely posted a note for your membership!

My foibles installing any Nvidia drivers are as follows:

  	 	 	 	pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }a:link {  }  X-terminal Failure when installing NVIDIA GeForce 6200 Drivers
 

 I've been searching the forums and have gotten this far trying to manually install/test my Nvidia drivers.
 Thus far my method is:
 

 (a) Boot Ubuntu into &#8220;failsafe graphics mode&#8221;
 (b) Open a terminal, &#8220;cd&#8221; to directory where drivers are stored,  and enter &#8220;sudo telinit 3&#8221;
 (c) Enter &#8220;sudo apt-get &#8211;purge remove nvidia-*&#8221; to be sure any installed Nvidia drivers are removed (I've not been able to install any &#8211; so this is superfluous at the moment. Oh &#8211; and the initial install of Ubuntu allowed me to select the latest Nvidia driver, which failed, and was then removed)
 (d) Enter &#8220;sudo sh NVIDIA-Linux-x86-173.14.22-pkg1.run&#8221; to install the driver (My guess is that I'll be trying many drivers until I find one that works)
 (e) While the module was "Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 173.14.22........" the following errors appear:
 

 ERROR: You appear to be running an X server; please exit X before             
          installing.  For further details, please see the section INSTALLING    
          THE NVIDIA DRIVER in the README available on the Linux driver          
          download page at [www.nvidia.com]("http://www.nvidia.com/"). 
 

 ERROR: Installation has failed.  Please see the file 
          '/var/log/nvidia-installer.log' for details.  You may find             
          suggestions on fixing installation problems in the README available    
          on the Linux driver download page at [www.nvidia.com]("http://www.nvidia.com/"). 
 

 (f) The problem seems how to exit the X server, and still input commands. When I use forum suggested solutions, such as:
 (i)  &#8220;ctrl+alt+backspace&#8221;, or &#8220;ctrl+alt+F1&#8221; which don't do anything
 or  
 (ii) &#8220;/etc/init.d/gdm stop&#8221; which does stop the terminal, and unfortunately everything locks, including keyboard, requiring a hard reboot. (iii) If I reboot, and try running in &#8220;root&#8221;, I'm lost. I can see anything there, nor &#8220;cd&#8221; to anywhere else. I was trying to use it to line input the commands. (iv) If I go to &#8220;command line&#8221; on boot, I get &#8220;grub>&#8221; and again am lost.  (oh, did I mention I was new to this? ) 

 My feeble understanding is that my terminal is &#8220;gnome-console&#8221; and X server (X Windows?) is required to run all graphics, so how can I disable it and yet do anything?  
 

 Just trying to install a working Nvidia driver. Your help is again needed.

---

### Post by ledbright on 2011-09-24
ignore the previous
"pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom:  0.08in; }a:link {  }  X-terminal Failure when installing NVIDIA GeForce  6200 Drivers"
That was an Open Office cut/past translation

---

### Post by ledbright on 2011-09-24
p { margin-bottom: 0.08in; }a:link {  }  I also tried the following, which prevented me from booting Ubuntu and required me to reload Ubuntu from scratch.
 


  [COLOR=#ff0000]ERROR: Unable to load the kernel module &#8216;nvidia.ko&#8217;.  This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA [/COLOR][[COLOR=#006400]_graphics_[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html#")[COLOR=#ff0000] device(s), or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release.[/COLOR]  
 To fix the above error message use the following procedure
 1) Download Newest Nvidia drivers from [here]("http://www.nvidia.com/Download/index5.aspx?lang=en-us")
 2) Open module blacklist as admin
 [INDENT]gksudo gedit /etc/modprobe.d/blacklist.conf[/INDENT] Add these lines and save:
 [INDENT]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/INDENT] 3) Uninstall any previously installed Nvidia drivers:
 [INDENT]sudo apt-get --purge remove nvidia-*[/INDENT]  4) Reboot your [[COLOR=#006400]_computer_[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html#")

---

### Post by wildmanne39 on 2011-09-24
Hi, so did this last process work for you?

It should have been simple, use the same method to boot the installed version the first time that you used to boot the livecd, then go into additional drivers or restricted depending on the version of ubuntu you are using, that card should use the same driver as mine the 173, even if it recommends a newer one I think the 173 is the best to use in my experience.
Thank you

---

### Post by ledbright on 2011-09-24
Hi again - no, unfortunately none of the three Ubuntu tested drivers worked. (173 was one of them). Two went to the failed/locked screen with multicolored densely spaced vertical lines, and the oldest version (169 if I recall?) went to a locked blank screen but at least had the Ubuntu background color. All required hard reboot to exit. 

And, the automatic install with those three options is offered only at the first boot, then disappears. Since I've reinstalled Ubuntu multiple times, I was able to try all three that were offered. Now, I'm beginning to configure Ubuntu through the failsafe graphics mode and would rather not reload to try them again (and since they didn't work the first time, there would be nothing to gain). 

I had the same problem with XP and had to go to a seriously old driver (84) to get it to function.
So, I'm at the point where I need to manually install different legacy drivers until I can (hopefully) find one that works. This seems to be again a daunting task for a new guy.

I'm still surfing the forums and trying multiple "tricks" but nothing yet works, and I may yet get another opportunity to reload Ubuntu if I'm not careful.

Thanks.

---

### Post by wildmanne39 on 2011-09-24
Hi, also when you install more then one from different sources it does not remove one when you install the other if you can get into fail safe mode you should check and make sure in synaptic that there is only one installed at a time.

It may show only one active in restricted drivers but it only shoes one even if there is more installed, that happen to me.

I went through the same process years ago on my laptop, I can tell you when you install from the nvidia site every time you update the kernel you will have to reinstall the driver.
Thank you

---

### Post by ledbright on 2011-09-24
Yes - I always run
"sudo apt-get --purge remove nvidia-*" as a precaution to make sure no old drivers exist. But, since I can't install any - nothing is there to remove and the command results in the following output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-180-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-185-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-173-dev for regex 'nvidia-*'
Note, selecting nvidia-current for regex 'nvidia-*'
Note, selecting nvidia-libvdpau-ia32 for regex 'nvidia-*'
Note, selecting nvidia-libvdpau1 for regex 'nvidia-*'
Note, selecting nvidia-glx-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-185-dev for regex 'nvidia-*'
Note, selecting nvidia-173 for regex 'nvidia-*'
Note, selecting nvidia-settings for regex 'nvidia-*'
Note, selecting nvidia-185-libvdpau for regex 'nvidia-*'
Note, selecting nvidia-185-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-vdpau-driver for regex 'nvidia-*'
Note, selecting nvidia-96-dev for regex 'nvidia-*'
Note, selecting nvidia-cg-toolkit for regex 'nvidia-*'
Note, selecting nvidia-96 for regex 'nvidia-*'
Note, selecting nvidia-glx-96-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-173 for regex 'nvidia-*'
Note, selecting nvidia-glx-180 for regex 'nvidia-*'
Note, selecting nvidia-glx-185 for regex 'nvidia-*'
Note, selecting nvidia-180-modaliases for regex 'nvidia-*'
Note, selecting nvidia-kernel-common for regex 'nvidia-*'
Note, selecting nvidia-libvdpau for regex 'nvidia-*'
Note, selecting nvidia-current-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-96 for regex 'nvidia-*'
Note, selecting nvidia-glx-180-dev for regex 'nvidia-*'
Note, selecting nvidia-current-modaliases for regex 'nvidia-*'
Note, selecting nvidia-173-modaliases for regex 'nvidia-*'
Note, selecting nvidia-185-modaliases for regex 'nvidia-*'
Note, selecting nvidia-common for regex 'nvidia-*'
Note, selecting nvidia-96-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-173-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-180-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-96-modaliases for regex 'nvidia-*'
Note, selecting nvidia-glx for regex 'nvidia-*'
Note, selecting nvidia-173-dev for regex 'nvidia-*'
Note, selecting nvidia-180-libvdpau for regex 'nvidia-*'
E: Couldn't find package nvidia-*

Again, I run "sudo apt-get --purge remove nvidia-*" every time I try a new "trick" to install a driver just as a precaution. Still not able to install any drivers.

---

### Post by wildmanne39 on 2011-09-24
Hi, try the command this way please:
```
run "sudo apt-get --purge remove nvidia
```

Also you can make one of the nomodeset parameters permanent if you have too, but you will not have 3d effects.
Thank you

---

### Post by ledbright on 2011-09-25
Hello again -
tried[FONT=monospace] "[/FONT]sudo apt-get --purge remove nvidia" with similar results

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-*

....and, tried a slew of other recommended actions which led me to reload Ubuntu multiple times. As for now, I'm running in failsafe graphics until I get some more time to dedicate to this, or get a non-Nvidia graphics card. I applaud Nvidia for providing Linux drivers, and Ubuntu for trying to incorporate them. Unfortunately, I'm out of time for now. Some of the actions I took include, but were not limited to:

  	 	 	 	p { margin-bottom: 0.08in; }p.text-body-indent { margin-left: 0.2in; }h3 { margin-bottom: 0.08in; }h3.western { font-family: "Liberation Sans",sans-serif; }p.list-cjk { font-size: 12pt; }p.numbering-1-western { margin-left: 0.25in; text-indent: -0.25in; }p.numbering-1-cjk { margin-left: 0.25in; text-indent: -0.25in; font-size: 12pt; }p.numbering-1-ctl { margin-left: 0.25in; text-indent: -0.25in; }p.hanging-indent { margin-left: 0.39in; text-indent: -0.2in; }pre.cjk { font-family: "DejaVu Sans",monospace; }h2 { margin-bottom: 0.08in; }a:link {  }tt.cjk { font-family: "DejaVu Sans",monospace; }



------------------------------------------------
 I tried the following, which prevented me from booting Ubuntu and required me to reload Ubuntu from scratch.
 


  [COLOR=#ff0000]ERROR: Unable to load the kernel module &#8216;nvidia.ko&#8217;.  This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA [/COLOR][[COLOR=#006400]_graphics_[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html#")[COLOR=#ff0000] device(s), or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release.[/COLOR]  
 To fix the above error message use the following procedure
 1) Download Newest Nvidia drivers from [here]("http://www.nvidia.com/Download/index5.aspx?lang=en-us")
 2) Open module blacklist as admin
 [INDENT]gksudo gedit /etc/modprobe.d/blacklist.conf[/INDENT] Add these lines and save:
 [INDENT]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/INDENT] 3) Uninstall any previously installed Nvidia drivers:
 [INDENT]sudo apt-get --purge remove nvidia-*[/INDENT]  4) Reboot your [[COLOR=#006400]_computer_[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html#")
 Tried  
 [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual),
 noting the following disclaimer:
 **This is not the recommended way to install the NVIDIA drivers - please see [BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")**** for the supported method**.
 but, started to try it anyway.
 


 This didn't help, and does not seem valid for 10.04.
 (a) The xorg.conf file is different, but already had "nvidia" instead of "nv" in it.
 (b) there is no "/etc/default/linux-restricted-modules-common" file to be modified
 (c) It instructs me to do the following:
 --------------------------------------------------------------------------------------------------------------
 Now that your Xorg.conf is saved, we need to shutdown the X11 server so that we can install the new drivers. To do this, save your work and press ctrl-alt-f1, and log in. Then run the following command to shutdown X11. **Make sure your work is saved, Gnome/KDE is going to shutdown too**.  
  For Ubuntu:  
 sudo /etc/init.d/gdm stop --------------------------------------------------------------------------------------------------------------
 --First, "ctrl+alt+F1" does nothing.
 --Second, "sudo /etc/init.d/gdm stop" in the terminal locks everything (as, I guess, it should)  
 leaving me with no keyboard input and having to hard reboot.
 


 So, I'm still stuck with the error when trying to install an Nvidia driver:
 


 ERROR: You appear to be running an X server; please exit X before             
 installing.  For further details, please see the section INSTALLING   THE NVIDIA DRIVER in the README available on the Linux driver
 


 as for me, I'm still just trying to manually install NVIDIA drivers.......
 ******************************************************
 Moving on to the official installation site:
 [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
 


 The intro includes the text:
 -------------------------------------------------------------------------------------
 Usually you will see a notification and/or an icon in the top panel, reminding you that restricted drivers are available.  
 -------------------------------------------------------------------------------------
 That happens for the first reboot after installation, then disappears for all subsequent boots.
 The next text:
 -------------------------------------------------------------------------------------
 If you are using an older version of Ubuntu, or if you aren't notified about additional drivers, you can launch the installation yourself.  
 
[LIST]
[*]Go to **System -> Administration -> Hardware 	Drivers**
[/LIST]
 -------------------------------------------------------------------------------------
  creates a menu stating "No Proprietary Drivers Are In Use On This System" so still nothing to install.
 


 The remaining instructions assume I've installed a driver, and need to work through driver issues.
 


 This looked interesting:
 **Screen Blanks/Monitor Turns Off**

  Using a laptop with a [GeForce]("https://help.ubuntu.com/community/GeForce") Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not receiving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.  
 The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.  
 This is a [bug]("https://bugs.launchpad.net/bugs/82312") about displays on digital outputs being blank when using NVIDIA driver, and can be resolved by editing your /etc/X11/xorg.conf file:  
 
[LIST]
[*]Switch to the console by using 	ctrl+alt+F1, or reboot and select recovery 	mode from the GRUB menu.  	
[*]Open and edit xorg.conf 	like this: sudo nano /etc/X11/xorg.conf. 		
[*]Find the line that says: 	Section "Screen"  	
[*]Insert a new line that says 	Option "UseDisplayDevice" "DFP". 		
[*]Save the file. 	If you had to restart into recovery mode, type reboot, 	otherwise restart your display using sudo /etc/init.d/gdm restart. 		
[/LIST]
 


 But left me with a dead screen after boot using 173 driver. Had to use the command
 "sudo apt-get --purge remove nvidia-*"
 just to be able to get back to functional failsafe graphics mode.
 
I was able to interrupt the boot (occasionally) using the shift, getting to a command line and load drivers. Some loaded, none worked. The install/remove process seemed fraught with conflicts - ended up reinstalling after this effort.

---

### Post by wildmanne39 on 2011-09-25
Hi, I am not sure what is going on with not being able to install the nvidia driver.

When you hit ctrl+alt+f1 thru f6 it should have taken you out of the desktop envirnoment and to a black screen then you should have been able to enter your log in name and password then you should have been able to run those commands,I have done that procedure my self a few times a long time ago.

It should not have been needed in 10.04 for your card.

I am out of ideas of how to get the driver to install.
Thank you

---

### Post by ledbright on 2011-09-26
Are there any other Ubuntu versions (Kubuntu, Lubuntu etc.) that might be more friendly to Nvidia? (and me?)

---

### Post by wildmanne39 on 2011-09-26
Hi, no they are all based on ubuntu.
Thank you

---

### Post by ledbright on 2011-10-03
Ubuntu 11.04/Nvidia GeForce 6200 Install Procedures:

After great consternation and repeated failures with installing 10.04/Nvidia 6200, tried 11.04/Nvidia 6200. That didn't help, (arrggghhh). Same problems, but these were resolved on 11.04 using the following procedures (which are a conglomeration of very insightful comments on various forums). [My guess is that these might work on 10.04 as well.]

Here goes:

Installed 11.04, then booted into failsafe graphics mode.

Edited grub as follows:

    $ sudo gedit /etc/default/grub

Changed "quiet splash" to "quiet splash nomodeset"

Ran

    $ sudo update-grub

after the edit.

Also, my PC doesn't support "Unity", so I switched to "Ubuntu Classic" using

    System Settings-> Login Screen

I rebooted into failsafe graphics mode.

Next, I ran the following (from Ubuntu forum) to uninstall/reinstall the Nvidia driver:

1) Blacklist the modules. Open the blacklist.conf file.

    $ sudo gedit /etc/modprobe.d/blacklist.conf

add the following modules to the end of the file.

blacklist amd76x_edac #this might not be required for x86 32 bit users.
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

Save the file and exit.

2) Remove all the nvidia* packages

    $ sudo apt-get remove --purge nvidia*

1. Go to NVIDIA website and download the compatible driver for your graphic card series. Make sure its in your home folder (not downloads)
2. Reboot your Ubuntu.
3. Choose the &#8216;Recovery Mode&#8217; on GRUB.
4. Go to the bottom of menu list, choose &#8216;root console&#8217;.
5. Disable the Kernel Nouveau.
#echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf #update-initramfs -u
Reboot to root console again
6. Change to init 3
#init 3
7. Install the NVIDIA driver
#sh NVIDIA-XXXXXX.run (easiest way is to type sh NV then hit tab) make sure you say yes to writing a new xorg and updating the system
8. Reboot your Ubuntu.


(In my case, I used Nvidia driver: "NVIDIA-Linux-x86-173.14.31-pkg1.run")


I then rebooted into failsafe graphics mode, and used the following procedure (from Linux Wiki forum) to fix what appeared to be a suspend problem preventing normal boot:

PROCEDURE:
You should save all your work before trying suspend as it may not wake up during testing. 
Prerequisites 
 
You should run a full update for your installation of Ubuntu to ensure you have all the latest packages installed. 
NVIDIA binary driver 
 
The NVIDIA binary driver is a culprit in a number of suspend issues. Try the following to see if suspend begins to work. Some of these tips will mean that your system will take longer to recover from a suspend, unfortunately there isn't much that can be done about that. 
 
1. Update to the latest NVIDIA drivers. You can follow our Configuring a NVIDIA graphics chip for Ubuntu 7.10 guide on how to do this. 
 
2. Add the following line to your "Device" or "Screen" section (doesn't matter which) in your /etc/X11/xorg.conf file: 
 
Option          "NvAGP"       "1" 
 
It doesn't matter if your card isn't actually AGP. 
 
The end result will look something like this: 
 
Section "Device" 
    Identifier     "Videocard0" 
    Driver         "nvidia" 
    VendorName     "NVIDIA Corporation" 
    BoardName      "GeForce Go 7400" 
    Option         "AddARGBVisuals" "True" 
    Option         "AddARGBGLXVisuals" "True" 
    Option         "NoLogo" "True" 
    Option         "NvAGP"       "1" 
EndSection 
 
You can use your favourite editor to edit this file, with nano you would use: 
 
sudo nano -w /etc/X11/xorg.conf 
 
Reboot before trying suspend for these changes to take effect. 
 
3. Edit your /etc/default/acpi-support file. In this file find the "POST_VIDEO" and "SAVE_VBE_STATE" options and change these values from "true" to "false". 
 
Reboot before trying suspend for these changes to take effect. 
****************************************************************************************************************

Thus, I can now do a normal boot to Ubuntu 11.04 with my Nvidia 6200 GPU. The graphics remain a tad sluggish, and I still think there are kinks in the driver with regard to my system, but now I can boot normally. Finally, this "absolute beginner" can begin using Ubuntu. Thank you to the forum contributors, including

"scampbell70" at "ubuntu.forums.org/showthread.php?t=1742952" et. al.

and from an historical link,

"www.linwik.com/wiki/getting+suspend+and+hibernate+working+in+ubuntu+7.10"

---

### Post by wildmanne39 on 2011-10-04
Hi, I am glad you have it working, sounds like you had a learning experience.

Are you are using classic right? Are you using compiz?
Thank you

---

### Post by ledbright on 2011-10-06
I am not using "compiz." I had to switch to "ubuntu classic" until the Nvidia driver 173 was installed, then I was able to switch back to "unity." And, yes, it has been a learning experience...

---


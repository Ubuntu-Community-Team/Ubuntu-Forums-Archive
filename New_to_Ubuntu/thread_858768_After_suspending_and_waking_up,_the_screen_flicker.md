---
title: "After suspending and waking up, the screen flickers"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by mm823626 on 2008-07-13
Hello,

When ever I start Hardy Heron from the computer being off, the screen is great.  But after I suspend the system, and then wake it up, the screen gets this weird flickering jump that seems to happen more often when starting a program or watching a video.

I have a Gateway desktop that dual boots with Windows.  Anyone know how to solve this?

Thanks,
-Mike

---

### Post by TSS on 2008-07-13
I had this issue in the past using an nVidia driver. Are you using nVidia?

---

### Post by mm823626 on 2008-07-13
Hey, TSS, thanks for the quick response!

I looked in the Hardware Drivers under System, and it did not list anything, it just said "there are no proprietary drivers in use on this system."  IS that where I could tell if I was using nVidia?

I should maybe mention that I was using 1280x768, and after switching to 1152x768 it flickered less, but it still does it.

-Mike

---

### Post by TSS on 2008-07-13
> **mm823626 said:**
> Hey, TSS, thanks for the quick response!

I looked in the Hardware Drivers under System, and it did not list anything, it just said "there are no proprietary drivers in use on this system."  IS that where I could tell if I was using nVidia?

I should maybe mention that I was using 1280x768, and after switching to 1152x768 it flickered less, but it still does it.

-Mike

Yeah, my issue was with a proprietary nVidia driver.  So no luck there. 

Can you post the output of 'lspci' here?

---

### Post by mm823626 on 2008-07-13
lspci said:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)

---

### Post by TSS on 2008-07-14
It looks like someone else with your graphics device has been having a similar problem:
[http://www.nabble.com/Bug-480241:-xserver-xorg-video-i810:-No-console,-bad-flicker-after-suspend-to-ram-td17139876.html](http://www.nabble.com/Bug-480241:-xserver-xorg-video-i810:-No-console,-bad-flicker-after-suspend-to-ram-td17139876.html)

Also here:
[http://ubuntuforums.org/showthread.php?t=701018](http://ubuntuforums.org/showthread.php?t=701018)

It would be helpful to have your xorg.conf, could you post that as well?  Hopefully we can figure out a solution for you.

---

### Post by mm823626 on 2008-07-14
Thanks for the links.  I didn't really understand the advice from the first link.  I tried the advice of the second link, which suggested inserting Driver "i810" into xorg.conf, but after doing this my screen was really messed up after coming back from suspending, so I don't think it worked.

Here's what my xorg.conf originally contained (I've reverted back to this):
Section "InputDevice"
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

Section "Device"
 Identifier "Configured Video Device"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen "Default Screen"
EndSection

---

### Post by mm823626 on 2008-07-26
I am still having the problem, so any help would be really appreciated!!

Here's some more info about the system:

> mm823626@mm823626-desktop:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810
mm823626@mm823626-desktop:~$ glxinfo | grep -i direct
direct rendering: Yes
mm823626@mm823626-desktop:~$ glxinfo | grep -i opengl
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
mm823626@mm823626-desktop:~$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

mm823626@mm823626-desktop:~$ glxgears
1123 frames in 5.0 seconds = 224.438 FPS
1156 frames in 5.0 seconds = 231.000 FPS
1011 frames in 5.0 seconds = 202.089 FPS
1158 frames in 5.0 seconds = 231.482 FPS
1125 frames in 5.0 seconds = 224.857 FPS

---

### Post by governmentproj13 on 2008-08-29
I've been having the same issue, and I'm using NVIDIA.  However, I am using the correct driver, and the most up to date one, and I really hope I don't have to change anything in that department. :(

My X.org does have a few extra lines leftover from when I was first trying to configure my video card, but I didn't think that would do anything negative.  I've heard Everex Stepnotes tend to have issues with suspend and hibernate anyways.

I'm running Hardy on a GeForce 7600.

---

### Post by cek1227 on 2008-08-30
I'm having the same problem on one of my machines. The laptop doesn't suspend worth squat, so it's only the desktop: Dell Dimension 2400, Intel video card, config'd in x.org as generic.

---

### Post by gibberish on 2008-08-31
I have the same problem on my old box: Dell 4500s with standard mobo/video card.

---

### Post by cek1227 on 2009-05-29
Same problem with a Dell Dimension. I suspect it only occurs on CRTs, not LCDs.

---

### Post by OffAxis on 2009-05-29
have you tried to degauss the monitor?

does it have any effect?

---

### Post by sinnadyr on 2009-06-23
Same problem with the Dell xps m1330 at 9.04. Any updates on this?

---

### Post by Laeys on 2009-07-08
I have the same problem on my Dell Dimension.  
I suspect this has something to do with dell or intel.

---

### Post by HeWhoE on 2009-09-13
I have the same problem with my Dimension 4500s.  I have an LCD monitor attached.

lspci output:

> 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by GeneralSpecific on 2009-10-10
Same issue...no solution, but _maybe a start_.

Dell Optiplex gx260
2.6 P4, 256mb RAM
Bios A05
Crt monitor
Xubuntu Jaunty (also tested on Hardy -live CD- same result)

Video card (onboard):
  (same as Mike and HeWhoE)

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

**[COLOR="Red"]SUSPEND[/COLOR]**
[INDENT]I have the screen flicker problem when I return from suspend.
Killing Xorg and starting a new session doesn't help.
It happens with both Fluxbox and Xfce desktops.
The flicker seems to be worse when there is motion on the screen, like the mouse scrolling.

A reboot gets me back to normal.[/INDENT]

**[COLOR="Red"]HIBERNATE[/COLOR]**
[INDENT]When I try hibernate it will not resume...it tries then leaves me with a black screen.  
When I Ctrl+Alt+F1 I see an error that it didn't find any resume image, and is trying a normal boot.  
I can't start X or gdm because it says they are already running.

Pushing the reset button and rebooting gets me back to normal.[/INDENT]

[COLOR="Blue"]I have found one work around I am exploring.[/COLOR]

When use the command:
```
sudo pm-suspend
```

I get the screen flicker problem

When I try:
```
sudo /etc/acpi/sleep.sh
```

_*[COLOR="Blue"]It works just fine![/COLOR]*_  I have tried this numerous times in a row and it always seems to work.

When I try the commands *"pm-hibernate"* or *"/etc/acpi/hibernate.sh"*
I get the same hibernate problem I described earlier.

**[COLOR="Red"]QUESTIONS:[/COLOR]**

Does the *sleep.sh* command work for anyone else with this problem?

I there a simple way to add that sudo command to a fluxbox menu? (for me)
Or other window managers (for others)

Is it a video driver problem?  (All of us who have posted the info about our cards have the same one.)  
Would updating or rolling back the driver help?

Can we remove *[I]**pm-utils***[/I] and go back to only using **acpi**?  (If you try to uninstall them in Synaptic they try to take practically everything with them.)

I hope that someone can take this information and go a little farther with it.


-Ryan

---

### Post by GeneralSpecific on 2009-10-15
I may be the only one still working on this...but in case I'm not...
[COLOR="Blue"]
Suspend workaround:[/COLOR]

When I try the aforementioned _sleep command_:

```
sudo /etc/acpi/sleep.sh
```

It works very well!  At least running **[COLOR="Red"]Fluxbox on Xubuntu Jaunty[/COLOR]**

Though I have found that it _Firefox_ is running when I do this it will not wake up, 
and I have to reboot to get it to work.

I can avoid this problem by making sure to close it before I suspend.


[COLOR="Blue"]XFCE:[/COLOR]
[INDENT]I tried the same thing in my Xfce desktop with no success.
(no error message, I just got my prompt back)

When I first kill the *'gnome-power-manager'* process, 
it will go to sleep with the sleep.sh command and then wake up properly...

BUT.  When I then try to exit, it _crashes_.  
One time giving me a black screen, just like I get when trying to hibernate.

Another time it gave me an error screen saying it couldn't start X
(which seemed odd since I was powering down) and that I should fix
the problem and then restart 'gnome desktop manager' (GDM)[/INDENT]

I am wondering if **GDM** might be causing all, or some of my problems with suspend.

I might try to get rid of it and try a _different login manager_.
Or maybe try to run without any and just login from command line and start X.


[INDENT]*Here is another post I found that may be **[I]helpful to others ***having suspend/resume problems. 

[http://ubuntuforums.org/showthread.php?t=1144999.]("http://ubuntuforums.org/showthread.php?t=1144999.")

I found it informative, even if it didn't help me with my problem.

[/I][/INDENT]


I welcome any other advice.
-Ryan

---

### Post by editrix on 2009-10-27
Hi GeneralSpecific: Thanks so much for your work. I'm having the same problem on Kubuntu Hardy, so I don't think it has anything to do with gdm or anything Gnome. And also, this problem has obviously been around for a long time!

Using the /etc/acpi/sleep.sh works great, except it turns on my ethernet card and I use dialup, so I have to manually turn it off in order to use my modem. So that's yet another bug, I assume.

Sorry I have nothing new to add, except that your post has helped me--and I'm sure others. And this will bump it so perhaps some kind soul will see it and answer your (our) other questions.

---

### Post by GeneralSpecific on 2009-10-28
Thanks editrx!

I am hoping that our problem will be solved with Karmic Koala...

[http://www.ubuntu.com/getubuntu/releasenotes/910overview]("http://www.ubuntu.com/getubuntu/releasenotes/910overview")

I'm pretty sure that our problem ties in with either the **pm-utils** or the **Intel video driver**, BOTH of which are getting an update in Karmic.  

I plan on updating as soon as I can find the time.  I'll post the results here.

Has anyone tired the Karmic RC?  Do they still have this problem?

-Ryan

---

### Post by GeneralSpecific on 2009-10-31
Upgraded to Karmic...

And it **[COLOR="Blue"]FIXED THE PROBLEM![/COLOR]**:guitar:

The upgrade seems to have caused troubles with Xfce (I can't login, but I never use it anyways) 
so I haven't tried it from there yet...but suspend works fine from the _login screen_ and in 
_Fluxbox_ with the */usr/sbin/pm-suspend* command.

The solution most likely lies with the change of the Intel video drivers.

I hope this helps others as well.

-Ryan

---

### Post by nbd on 2009-11-01
Hello,

I just installed Karmic and I'm experiencing heavy screen flickering after resume. I found out that it is somehow linked to my ps2 mouse usage. When I move the mouse as down as it gets, the screen stabilizes, and when moving up, the screen flicker starts, and further, the flicker pattern is directly dependant on the position of the mouse.

And if not enough evidence, I unloaded psmouse module and the screen flickering was gone. Then I loaded it again, and boom, the flickering came back.

I have intel 965G card, and I have used kernel mode setting already with Arch linux and never experienced post-resume flickering there, so this is either kernel related, or Karmic related.

EDIT: 
suspend-resume works without flicker with 'sudo s2ram --force' which gives the output:

Switching from vt7 to vt1
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7

Also about the mouse movement; to be more precise, the mouse at bottom right corner removes the flickering. Anywhere else, it will introduce the flickering. And the virtual terminals (vt1-6) are not showing the console login prompt, but rather some bluish background. But after s2ram, everything is back to normal - no flickering and normal looking vt's.

My gut feeling says that the problem lies somewhere in the framebuffer and how it is not properly initialized after Karmic's own resume code. Arch linux used the same KDE4 'Suspend to RAM' from K-menu. Don't really know what they are doing internally.

---

### Post by moore.bryan on 2010-01-02
Hmm... I just found this thread and it would seem I am suffering the same problems with KSM turned-on and an Intel graphics card running the Xorg-edgers stuff.

Any ideas where I can start a debug?

---

### Post by editrix on 2010-01-02
> **moore.bryan said:**
> Any ideas where I can start a debug?

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

But I bet it's already been started. Nevertheless, you should add to it with as much info as possible.

---

### Post by Chris Edgell on 2010-01-02
I hope I don't seem too totally absurd to say, I had a screen that was flickering and someone told me my CRT could be overheating.  I began shutting down every night and turning the screen off if I were going to be away from it for some hours.

The problem has gone away;  That was an easy fix for me.  (It never happens now.)

---

### Post by moore.bryan on 2010-01-02
> **editrix said:**
> [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

But I bet it's already been started. Nevertheless, you should add to it with as much info as possible.

Yeah, I saw a couple of bugs already reported, but they seemed to be relatively old and as far as I could tell, none were on Karmic using the Xorg-Edgers PPA.

---

### Post by kishanbhat on 2010-04-01
GeneralRepublic,

Thanks to your post - [http://ubuntuforums.org/showpost.php?p=8085657&postcount=4](http://ubuntuforums.org/showpost.php?p=8085657&postcount=4),  I tried "/etc/acpi/sleep.sh" when I saw incessant flickering. The  machine went into suspend mode. I woke it up and the ***flickering is  gone***!! I think lot of users are having this problem and  GeneralRepublic has an easy solution.

Otherwise it was so stressfull in seeing this flicker and keep moving  the mouse to avoid the flickering.

Xubuntu 9.10 + Fluxbox (from ubuntu rep). Compaq nc6220
*-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics  Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0

---

### Post by nbd on 2010-07-23
Hello, I just installed Linux Mint 9 (based on ubuntu 10.4) and the suspend/resume worked fine until I disabled the screen locking on resume (too annoying) from gconf-editor (App->Gnome power manager->Lock) and then the flickering started to appear again.

s2ram --force works fine without flicker

sudo /etc/acpi/sleep.sh didn't suspend, just gave errors:


cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory

---

### Post by nosmokenofire on 2010-10-05
I have this problem on an Acer Aspire 5100 dual boot Vista/Lucid Lynx. I tried a few things from a couple of posts on the subject, but to no avail. 

I ran ```
sudo lshw -C video
```

and got 

> *-display               
       description: VGA compatible controller
       product: RS482 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:17 memory:c8000000-cfffffff(prefetchable) ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff(prefetchable)Thank you for any help?

---

### Post by editrix on 2010-10-05
Hi nosmokenofire:

I hope someone gives you a more positive answer than I can. Ever since I switched to Linux Mint (which is Ubuntu with most of the bugs fixed) I haven't had the problem.

---

### Post by nosmokenofire on 2010-10-06
Thanks editrix,

I hope I get a solution too. I'm just starting to get my head around Ubuntu (and like it) and don't fancy the hassle of changing OS right away, I'll hang on for the meantime to see if anyone else can come up with anything... I need my suspend!!! At the moment I am shutting down after each time I check my email...

Many thanks anyway.

---

### Post by nosmokenofire on 2010-10-10
Can no one offer ideas on this, please...

(please see my previous posts)

If no one can help this time then I'll just give up and live with it... Or change my OS!
Thank you.

---

### Post by johanhartman on 2010-11-11
Don't bother switching to Mint for this. I'm on Isadora and having the same problem for the first time ever. Had the previous to iterations of Mint/Ubuntu on the same laptop with no such problems.

---

### Post by crafter on 2011-06-14
This fixed it for me.

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by billyb351 on 2013-02-22
I ran into this problem on 12.04.2 when using 'rtcwake' through cron to put the file server to sleep when nobody is around or everyone is sleeping and having it automatically wake up right before people get home from work or early in the morning on weekends.  Whenever the computer wakes up from suspend, the screen randomly flickers, generally more when scrolling.

The 'sleep.sh' command doesn't seem to have this problem.  Taking these 5 lines from sleep.sh and adding them to my script right before I call 'rtcwake' seems to solve the problem.

```
. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/device-funcs
. /usr/share/acpi-support/policy-funcs

DeviceConfig;
```I haven't tried to reverse engineer what those 5 lines do yet, but the solution seems to lie in there.  Each of those files it's executing seem to contain various functions that get called through the "DeviceConfig" function, and so one of those functions must do something to the display to cause this problem not to show up.

---

### Post by oldos2er on 2013-02-22
Old thread closed.

---


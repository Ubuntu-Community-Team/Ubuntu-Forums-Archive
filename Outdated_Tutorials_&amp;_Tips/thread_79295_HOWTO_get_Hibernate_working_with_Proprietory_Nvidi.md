---
title: "HOWTO get Hibernate working with Proprietory Nvidia driver (using Suspend2)"
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by chanders on 2005-10-19
First of all I have to give my hats off to Griffin3 without which this howto will not be final. In fact you HAVE to follow his HOWTO for suspend2 and make sure suspend2 is working (using the bundled nv driver) FIRST before you attempt getting the proprietory driver working....

Step1. Remove any proprietory Nvidia driver that you have installed. Either with synaptic or otherwise.

Step2. Make sure the driver you are using in xorg.conf is the 'nv' driver that came with Breezy.

Step3. Follow Griffin3's HOWTO till the end. (In Step 7, you might need to use synaptic to install gcc if the apt-get command did not work)

Griffin3's Howto:
[http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2](http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2)

You should now have a working suspend (really great at that). Test it a few times to make sure it suspends and resumes properly. It should.

Step4. Download the latest driver from Nvidia's website to your home directory.

[http://download.nvidia.com/XFree86/Linux-x86/1.0-7676/NVIDIA-Linux-x86-1.0-7676-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-7676/NVIDIA-Linux-x86-1.0-7676-pkg1.run)

Step5. Logout until you see the login screen. Press ctrl+alt+F1. Login.

Step6. type 

```
sudo killall gdm
```

Step7. type

```
CC=gcc-3.4
```
```
export CC
```
```
sudo sh NVIDIA-Linux-x86-1.0-7676-pkg1.run
``` 

Step8. Before you click 'Accept' press ctrl+alt+F2. Login.

Step9. Type 

```
cd /tmp
```

then type

```
ls -l
```

you should see a list fo all the directories and files there. The installer that is running in console 1 has its files in one of the directories. After doing some searching, you will find one with a directory named NVIDIA-Linux-x86-1.0-7676-pkg1 in it.

cd into the directory, all the way to nv. It would look something like this

/tmp/selfgz7985/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv

you directory name will be different from selfgz7985.... find yours.....

type 

```
pico nv.c
```

then go down to line 3667 (you can tell the line number by pressing ctrl-c)

when you are on that line press enter. You should now have an empty line 3667. Type

```
case PM_SUSPEND_STANDBY:
```

on that line. Press ctrl-o to save the file and ctrl-x to exit pico.

Step10. Press ctrl+alt+F1 you should now be back to the installer page. Click accept and all the other good stuff until it says that it is installed.

Step11. Type sudo pico /etc/X11/xorg.conf and change the driver to 'nvidia' and make sure to add the line

```
	Option 		"NvAgp" 	"1"
```

in the device section. Press ctrl+o then ctrl+x.

Step12. Type sudo pico /etc/hibernate/blacklisted-modules and put a # in front of nvidia. It should now look like 

```
#nvidia
```

press ctrl+o then ctrl+x

Step13. Type reboot. Your machine should now reboot all the way to GDM. (You should have seen the Nvidia logo along the way)

Step14. Login. Test that the hibernate is working by pressing the powerbutton.

Step15.Thats it! Hope you have a working syspend now. Let me know how it goes....

Known Issues:
1. Hibernate does not allow you to use the consloe while it is working. By pressing ctrl+alt+F1 we get a garbled screen, but pressing ctrl+alt+F7 will always get you back to X.

---

### Post by coaxx on 2005-11-24
Hey chanders, thanks a  lot for this howto! 

Before I will step in to this I have a question. Is it possible to easily switch back to the nv driver if something will be not working at the end?

---

### Post by kugar on 2005-12-07
Did you try to make hibernate work with new nvidia 8174 drivers ?
I tried but it didn't work with the same hack as 7676 drivers but I can have forgottent something or have done something wrong.

For information, I have a Sony VGN-S4HP laptop with a GeForce 6200 and hibernate works with 7676 nvidia drivers.

---

### Post by oblib on 2005-12-10
> then go down to line 3667 (you can tell the line number by pressing ctrl-c)

when you are on that line press enter. You should now have an empty line 3667

For version 7174 (legacy) NVIDIA driver, change line 3427 instead of line 3667. Should look like:
```

       switch (state) {

   case PM_SUSPEND_STANDBY:

       case PM_SUSPEND_MEM:
 
            nv_printf(NV_DBG_INFO, "NVRM: ACPI: received suspend event\n");

```
See [http://wiki.suspend2.net/HardwareCompatibility](http://wiki.suspend2.net/HardwareCompatibility)

---

### Post by oblib on 2005-12-13
This doesn't work for me and I don't know why (obviously, why else would I be here?).  When I come back from hibernation, my TV (I'm using TV Out) flicks to some inappropriate frequencies, I assume while the module is loading, and then shows nothing but a solid orange screen. If I kill the Xsession and start again, it works fine. Any ideas?

Also, when I first boot up, it says it cannot find the nvidia module and fails to load X. When I start it manually (startx) it loads just fine.

---

### Post by ashrack on 2005-12-25
It doesn't work 4 me. It goes into hibernation fine. But when I turn the computer on, I get a black screen when it should start GDM. And also CTRL+ALT+F? don't work and gives black screen.

If am using the VESA driver all works great. I can use the original SUSPEND&HIBERNATION aswell as SUSPEND2 without any problems.

---

### Post by ashrack on 2005-12-26
...

---

### Post by ashrack on 2006-01-03
bump

---

### Post by pospeselr on 2006-01-11
I have followed Griffin3's guide to the letter, and the same for this one.  However, whenever I try to compile and install version 7676 of the nvidia drivers using the .run provided, it throws me an error.

```

ERROR:  Unable to load the kernel module 'nvidia.ko'.  This is most likely because
the kernel module was built using the wrong kernel source files.  Please make sure
you have installed the kernel source files for your kernel;  on Red Hat Linux 
systems, for example, be sure you have the 'kernel-source' rpm installed.  If you 
know the correct kernel source files are installed, you may specify the kernel source
path with the '--kernel-source-path' commandline option.

```

I tried doing so and pointing it to /usr/src/linux from which I have just compiled the kernel from (using Griffin's guide).  Hibernate works fine with the nv driver, though I can't get video to go above 640x480.  I have a Geforce4 440 Go 64M on a Compaq Presario r3000 laptop if that makes a difference.  I'm doing this from a server install with just x-window-system-core installed, as well as the various packages mentioned in the guides.

---

### Post by Hydrochloric on 2006-01-12
I just got this to work using the latest nvidia 1.0-8178 driver, using the same technique,
the line number for the "CASE PM_SUSPEND_STANDBY:" line in nv.c for the 1.0-8178 driver has changed from line 3667 to line 3856

so, to get this guide to work with the 8178 driver, be sure to change line 3856 instead of 3667 :D

works great on my compax presario r3309ea :)

---

### Post by lixy on 2006-01-13
Works like a charm on my inspiron 8600! Thanks so much everybody; You just made my day.
Now, few issues with breezy and the 8178 nvidia drivers; I got an error message running Nvidia's installer "```
ERROR: Unable to find the development tool `cc` in your path; please make sure
that you have the package 'gcc' installed. If gcc is installed on your
system, then please check that `cc` is in your PATH.
```
Breezy installs gcc4.0 by default but in order to compile the kernel and the nvidia drivers you need the 3.4. Desinstall gcc-4.0, install 3.4. For some reason, the CC env ironment variable wasn't enough in my case so I had to locate it with a whereis gcc, then put a link in your path to the location gcc-3.4 and call it cc. 
Keep it up:smile:

<EDIT> Alas, this morning, upon the 2nd reboot, X refused to start at all. I must have installed NVidia a dozen times with different methods and that may have screwed it; But that's just a wild guess.
You can reload NV with dpkg-reconfigure -phigh xserver-xorg, if you want. I'm trying a clean install right now before deciding which is vital for me, Nvidia or Suspend2. 
<\EDIT>
<EDIT> Everything's working great now that I did a clean install. Thank again guys! <\EDIT>

---

### Post by pospeselr on 2006-01-15
I've had the exact same problem with the same model laptop using the latest drivers.  Trying with the 7676 version drivers now.  With 8178 all goes well until it starts to load X and it flashes the nvidia splash screen and crashes to console.

---

### Post by pospeselr on 2006-01-15
Does exact same thing with 7676 drivers.  Do you have hibernate and nvidia working together lixy?

---

### Post by deruser on 2006-01-17
I use a Geforce 6800 GT, and I can suspend with the nv driver, but with nvidias proprietary X won't start, even if I quit X and unload the module. The hibernation works and boots back into the console, but X can't start, it says: 

(EE) NVIDIA(0): The NVIDIA kernel module does not appear to be receiving
(EE) NVIDIA(0):      interrupts generated by the NVIDIA graphics device.
(EE) NVIDIA(0):      Please see the FREQUENTLY ASKED QUESTIONS section in the
(EE) NVIDIA(0):      README for additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"

I can load the module with modrpobe fine, dmesg says: 
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-8178  Wed Dec 14 16:22:51 PST 2005

But when I try to start X it doesn't work, dmesg says:
NVRM: RmInitAdapter failed! (0x12:0x2b:1438 )
NVRM: rm_init_adapter(0) failed

If I try to hibernate when running X the screen goes blank and my monitor turns off, but not the computer, seems like it is stuck.

I've tried the patch at [http://www.nvnews.net/vbulletin/showthread.php?t=62021](http://www.nvnews.net/vbulletin/showthread.php?t=62021)
and I've tried the oneliner PM_SUSPEND_STANDBY patch.

This is with 2.6.15 patched with suspend2-2.2-rc16-for-2.6.15 patch.

It all works with the nv driver, but not at all with nvidias own driver :(

---

### Post by ashrack on 2006-01-24
I got it working with NVIDIAs
But in CTRL+ALT+F1 I get garbled screen. 
anyway to fix this?

---

### Post by palomar on 2006-02-19
THis HOWTO doesn't work for me :( After following up all the steps exactly (same driver version) my screen remains blank after rebooting when KDE has to start. With ctrl+alt+F1 I see an error about no screens found and much more... (don't know exactly). At walking through the steps I noticed the placement of "case PM_SUSPEND_STANDBY:" is a little vague. According to the given line number I had to place right in a statement-block.... Later I tried some other positions of this add-on line, but I guess the (mis)placement of this line had not much to do with a blank screen at bootup?

Now hibernate does work with the 'nv'-driver, but i prefer the 'nvidia'. Are there some things I can check?

My specs:
- Kubuntu 5.10
- Nvidia Geforce Ti4200 (NV25)

---

### Post by Greg T. on 2006-03-25
I've tried hibernating twice, and both times it horked my system so badly that I couldn't even get to BIOS on restarting. I had to open my case and clear the CMOS sensor to get it to boot. 

I haven't tried the HOW-TO, and probably won't. I'm so gun-shy of hibernate at this point that I'm going to wait and hope for NVIDIA to come out with updated drivers that handle it better by default. However, it does go to show that if you want to experiment a little and try out this HOW-TO, you're probably not going to make matters any worse than they are right now.

---

### Post by nickthecoder on 2006-07-13
This thread was the top of my google search, but I suggest that the following page is more current (and much easier) :

[http://parrenin.frederic.free.fr/DellLatitudeD800/linux-DellLatitudeD800.html](http://parrenin.frederic.free.fr/DellLatitudeD800/linux-DellLatitudeD800.html)

In summary, all you have to do is :
1) Add this line in section "device" of your /etc/X11/xorg.conf file:
        Option          "NvAGP" "1"
2) Set POST_VIDEO to false in /etc/default/acpi-support

---

### Post by CentralX on 2006-08-03
> **pospeselr said:**
> I've had the exact same problem with the same model laptop using the latest drivers.  Trying with the 7676 version drivers now.  With 8178 all goes well until it starts to load X and it flashes the nvidia splash screen and crashes to console.

Have you tried removing nvidia-glx from /etc/initrd/ ? This script removes some files (TLS links) upon reboot causing your X server to reset (104)

After removing this file and reinstalling the driver everything should be working fine... At least it does on my Debian testing machine.

---

### Post by dragonfyre13 on 2006-11-27
@NickTheCoder

It looks like that is only for the default suspend stuff that comes with breezy. This is for suspend2, something substantially different I gather.

---

### Post by mbradlcu on 2007-05-05
thanks for the guide,, I have a geforce4 420 in my presario R3000, using nvidia driver version 
NVIDIA-Linux-x86-1.0-9631-pkg1.run, Ubuntu 7.40, seems all that's needed to have suspend work is add
Option      "NvAgp"     "1".  I did notice a slowdown on opengl games,, ie quake3, Savage,, etc..

---

### Post by v1cho on 2008-03-24
LOL, this is kinda outdated, moderators  should put it in the archive :)

---


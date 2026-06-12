---
title: "HOWTO Install Xubuntu 8.10 on an HP 2133 Mininote with working Compiz and Video!"
date: 2008-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Big_Nose on 2008-12-17
Okay, this my first new thread and my first tutorial, hope it's helpful and I hope I can give something useful back to the community. Understanding of simple terminal commands (like 'sudo mousepad' for editing text files) is assumed

There's been plenty of tips (and problems) over the last year to get Ubuntu running on the HP 2133 mininote, but IMO the device is just a tad too slow to run gnome smoothly.

So, I recently ditched a slightly dodgy installation of ubuntu 8.10 and went for a fresh install of Xubuntu 8.10.

Installation is basically the same as in Ubuntu 8.10, which there are a few tutorials around, but i'll start from scratch.

**Step 1** - Download the Xubuntu 8.10 ISO  (standard desktop one) from here: [http://www.xubuntu.org/get]("http://www.xubuntu.org/get")
[B]
Step 2[/B] - If you don't have an external CD drive to plug into your mininote, then you'll need to create a bootable USB pen drive. Follow the instructions [here]("http://www.pendrivelinux.com/2008/11/05/usb-xubuntu-810-persistent-install-windows/") to do that under windows.

If you have problems booting, try renaming the folder "ISOLINUX" to "SYSLINUX" on the pen drive.
[B]
Step 3[/B] - Edit the 'Install Xubuntu' line by pressing tab and adding "xforcevesa" (without speechmarks) before the last '--' This will allow Xubuntu to install in safe graphics mode.
[B]
Step 4[/B] - Follow the usual installation procedures normally.

**Step 5** - Upon first boot, you will notice that wireless works out of the box (it does suggest a restricted driver to install, but the default one works fine). You will notice that the screen resolution is wrong.

**Step 5** - Download the VIA graphics driver, the xorg.conf file and the readme file from this tutorial [here]("http://ubuntuforums.org/showthread.php?t=1000966").

*After* installing the drivers by following the steps on the readme file, but *before restarting*, copy the supplied xorg.conf file over.

A simple but crude way to fix the screen resolution problem is to edit the xorf.conf file and do a 'find and replace' where find = "1280x720" and replace is "1280x768".

**Step 6** - Reboot (n.b. a full reboot, not just a Ctrl-Alt-Backspace)

You should now have a working Xubuntu system on the 2133, I noticed a marked improvement in speed compared Gnome in Ubuntu 8.10.
[B]
Step 7[/B] - Video playback does not work out of the box, so to get really smooth video playback (smoothest i've seen so far on the 2133) install VLC and use that, but set 'tools'-'preferences'-'video'-'output' to 'X11 Video output'.

**Step 8** - To enable compiz fusion, follow the steps [here]("http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/").

After installing compiz fusion you will need to edit '/usr/bin/compiz' and change the line 'whitelist' to include 'via' in the list of drivers. Compiz will then start once initiated, and run pretty smoothly, even video still plays smoothly with compiz enabled and whilst your cube is rotating.

A useful tool (available from add / remove or synaptic is 'Compiz Fusion Icon', this provides a clean way of changing window managers, because you won't want to run compiz all the time, it's a bit slow)

Follow the rest of the steps to set up compiz to autorun at startup if you wish.

**Step 9** - To preserve battery life, CPU scaling can be enabled by editing the grub loader using:

'sudo mousepad /boot/grub/menu.lst'

and adding 'acpi_osi="!Windows 2006"' to the end of the first line that begins with 'kernel'.

Hopes this tutorial helps some 2133 Users wanting to go for Xubuntu but put off by the lack of tutorials around. Hope my tutorial was relatively easy to use, like I said, it's my first ever tutorial and I hope it's okay!!

Edit - Webcam and Internal Mic don't work out of the box, I'll post when I've sorted this out on my machine

Please leave feedback and questions if you have any difficulties.

---

### Post by donpaterson on 2009-01-25
Great posting. Always good to see useful real posting.

I still can't get xubuntu to work on my 2133 HP Mini (bios 0.5).
I am trying to install xubuntu 'inside' Windows XP, by mounting the x 8.10 iso in winXP and then install and reboot. It's a dual boot.
The 'xforcevesa' option, on line 2, after the last = only changes it to show the xubuntu splash screen on the install/1st boot but still gets stuck at a blinking cursor.
Anyone else tried this, and got it working?
I have x8.10 running in vmware workstation but speed is not great, as you can imagine.
I have 2GB RAM.

---

### Post by karni on 2009-01-30
> **donpaterson said:**
> Anyone else tried this, and got it working?

I had the same problem as you - it turns out that I had to downgrade my BIOS to version F.04, and now it works ok (well, so far anyway).

You can download the F.04 BIOS boot disk creator from HP's website ([here](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687084&prodNameId=3687085&swEnvOID=2020&swLang=8&mode=2&taskId=135&swItem=ob-64238-1)) - it lets you create either a bootable USB stick or a CD, if you have an external CD drive. Unfortunately the boot disk creator seems to run in Windows only, but apparently it is possible to extract the files from the .exe file in linux. Also, make sure you're plugged into the mains when you boot from the USB stick/CD, otherwise it'll just give you an error and won't change the BIOS (presumably in case the battery runs out half way through).

---

### Post by Glynubu on 2009-06-12
thanks I had mine working for 2 hour then back to the shop where they are putting on Ubuntu (probably using this page) whilst I am paying for the memory upgrade to 2Gb.
When I get it back I'll look at the Video issues again.
Great advice here.  HP made a nice box of electronics but their SUSE version SLED10 installed and failure to add a boot/recovery disk has boosted interest in Ubuntu - silver lining!
Thanks for this tutorial.
Will report on success.
Glynubu

---

### Post by Glynubu on 2009-06-13
Well I've got Ubuntu 9.05 desktop working on my new HP 2133.
The apps run very fast but GNOME crawls. 
Wifi is working after my helpers put the drivers in
CHeese video works and sound works.
Its a KX872AA model with 2Gb memory.
Firefox working well.
Open Office working well and fast.
External VGA output works.
Resolution OK
Youtube has jumpy pics in playback but sounds OK. 
USB works
GNOME takes abou 10 seconds to respond to a click 
Click response instantaneous in the apps!
Really puzzled about the Genome Desktop click response time.

---

### Post by Glynubu on 2009-06-14
The slow running looks like software bloat in the GNOME for notebooks. Disabling unnecessary software e.g. Bluetooth and its etc. manager is speeding things up.  Depends on your user profile as to what is expendible.

---

### Post by spegru on 2009-06-14
Hi Glynubu. I am a little confused. Are you really using Xubuntu 9.04 (Jaunty Jackalope) and the external VGA port works? Reason for asking is because I heard that in Ubuntu 9.04 the VGA port does not work. I would really like to do this.

Please confirm. 

If you can, please also confirm which driver you are using.

spegru

---

### Post by spegru on 2009-06-24
bump

---

### Post by spegru on 2009-07-27
bump

---


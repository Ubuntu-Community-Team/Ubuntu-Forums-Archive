---
title: "Computer does not boot completely in &quot;Try Ubuntu&quot;"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by oostewal on 2013-10-19
I am trying to run Ubuntu on an HP 650 Intel Celeron 1000M,   OS Windows 8 64 bit single lang.   At first did not boot.   Went into BIOS and changed boot priority to DVD drive as first choice.  No other changes- still booting UEFI not Legacy.   Now did get response.   Screen came up asking to choose from 3 options -Try Ubuntu-Install - Check Disk.  Heading was GNU GRUB V 1.99-21Ubuntu3.10.   I was using Ubuntu Disc 12.04.3 desktop AMD64.  Chose Try Ubuntu option after which DVD drive made lots of clicking chattering noises as if reading.  This went on for a long time but screen remains dead.  System not responsive after choice screen.

---

### Post by oldfred on 2013-10-19
Welcome to the forums.

With UEFI booting you get grub menu, but have to manually add boot parameters for many video chips.
What video chip?

Often nomodeset works. At grub menu entry, e for edit, scroll to linux line, replace quiet splash with nomodeset.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some video chiips need other boot parameters.

---

### Post by oostewal on 2013-10-20
Thanks Oldfred.   Some progress - changed to nomodeset and pushed F10 to continue boot as directed by Grub.   Screens full of unintelligible text rolled by for some time ( looked like the old DOS stuff used to).  Last screen ended with "ubuntu@ubuntu:$" .   No further action from OS.  Looked like i was locked into a line editor of some sort.   Had to press power off to get out.   It then gave a few more lines of text, ejected the DVD and asked me to close the tray before it shut down.

---

### Post by fantab on 2013-10-20
Have you turned off 'Fast Startup' in Windows8? This feature keeps Windows in Hibernation and won't let it shutdown completely even if you have shutdown.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by oldfred on 2013-10-20
Removing quiet & splash boot parameters let you see the entire boot process. So that is normal and sometimes useful as it may stop on an error so you know what to fix.
You actually fully booted to command line but did not get the gui or desktop.
What video chip? Perhaps different boot parameter is needed?

With installer it will not matter but after install do not power down computer unless you have to. You want to remember the elephants.
       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by oostewal on 2013-10-20
I dont know if this is what you want.  Device manager tells me that the display adaptor is --Intel HD Graphics--Driver is version 9.17.10.2828 dated 31/07/2012

---

### Post by oostewal on 2013-10-20
Thanks fantab - but it made no difference.

---

### Post by oldfred on 2013-10-20
I have posted this before for Intel. But have no confirmation of which works for which Intel version.

  Older Intel video card: i915.modeset=1 or i915.modeset=0 
newer:  i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

   Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

   Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

### Post by oostewal on 2013-10-21
Tried the first 3 vid card options all with the same result.   About 2 pages of command line looking stuff then much clacking from DVD drive.   I am an old fart and this is probably getting a little above my addled brain.  Think I must cut my losses - go to legacy boot , throw out that useless prog Win8, install XP and then if that is ok install Ubuntu i386.   I dont need 32bit- edge tower is 30 km away and baud rate 1 bit/fortnight.    Thanks for the try and very prompt assistance.   Far better than I have ever managed to get from OEM- if the respond at all.

---


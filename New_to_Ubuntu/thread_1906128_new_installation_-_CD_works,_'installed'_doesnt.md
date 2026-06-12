---
title: "new installation - CD works, 'installed' doesnt"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by baslug on 2012-01-08
hello all, i'm new to the forums, also new to ubuntu/linux.  i built my current machine several years ago, put Windows Vista on it (horrible decision) used it about a year and after i got married (1.5 years ago) left it in a box in the closet.  decided to bring it out, ditch Vista and give ubuntu a spin.  but i'm running into some problems - i've checked the forums pretty extensively, tried a bunch of different solutions and every time i feel i'm on the edge of it working correctly, it doesnt.  here's some details on the machine and what i've tried so far:

machine details:
Motherboard:  ASUS Crosshair
CPU:  AMD Athlon 64 X2 Dual-Core 6000+ 3.0GHz
Video:  PNY NVIDIA GeForce 6600 
HD:  WD Caviar 320GB 7200RPM SATA
RAM:  4x1GB DDR2-800
Monitor:  19" Acer AL1916w

so i downloaded Ubuntu Desktop 11.10 (32-bit) and burned it to a CD.  was able to launch the Live CD using the "nomodeset" option, then ran into some hangups during installation (freezing).  i tried some of the other options and was able to get installation to complete from the Live CD using "acpi=off".  I split the HD into two partitions:  200GB still has Vista on it, and 120GB for Ubuntu.  after it reset, i'd get the Ubuntu splash screen and then it would go black.  i tried going through the various kernel boot options (nomodeset, acpi=off, noapic, etc) by appending the kernel boot line in grub... same thing - a little bit of loading, then black screen.

looked around the forums and i seem to think it's a video card issue.  i've been through the sticky "Graphics Resolution- Upgrade /Blank Screen after reboot" in the "Installation & Upgrades" forum ([http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)) trying just about every troubleshooting line in the first 2-3 pages of the thread.  

trying to boot to a text console (appending "text" to the kernel boot line in grub) doesn't work - same black screen.  somewhere i read to remove "quiet splash vt.handoff=7" from the kernel boot line and replace it with "--verbose single" and instead of the black screen, it actually gives me a command line.  from there, i can switch text terminals using <Ctrl><Alt><F1-6> which are all blank (except for the first which has the command line).  from there, i've tried installing nvidia-current with apt-get ... and it runs... says it's done something, but the GUI still won't start when i run "sudo service gdm start" ... i get a "service does not exist" type message.

the only other command line i can get to come up is when i boot in "recovery mode" and then "drop to root shell prompt"... but i'm not quite sure what to do from there as far as looking for and installing drivers as it doesn't seem to be able to connect to the repositories

at some point, i thought maybe it was having issues with the 32-bit version, so i downloaded and burned a CD with the 64-bit version.  launched the Live CD (again w/"nomodeset"), erased and reinstalled, installation completed w/no problems... reset... and black screen again at the same spot, same symptoms all around.

i'm really confused that i can get it to launch from the CD with only a simple modification, but can't get it to go all the way from the installation.

i don't think i've left anything out that i've tried... been working on this about 3 days now, so i may have forgotten something.  any help would certainly be appreciated... i could be way off base and maybe it's not a video card problem... my brain is about fried though and this box just might go back to the closet :)

thanks in advance.

---

### Post by mastablasta on 2012-01-08
did you install nvidia proprietary drivers?

---

### Post by philinux on 2012-01-08
> **mastablasta said:**
> did you install nvidia proprietary drivers?

He need intructions how to do that from cli.

---

### Post by baslug on 2012-01-08
> **philinux said:**
> He need intructions how to do that from cli.

that's exactly right.  i've tried downloading the proprietary drivers from the nvidia site while in the LiveCD, but i can't seem to figure out how to install them to the 'installed version'... and i can't copy them to folders on the installed version due to permissions.

---

### Post by baslug on 2012-01-31
so i stepped away for a couple weeks to clear my head.  this morning i fired up windows on the same machine with intentions of clearing out another hard drive i have in order to reformat it and run a new installation of ubuntu on it - dont know why it should be any different than installing on the same drive as windows in a different partition, but i thought the fresh start would do me some good.

i noticed in the windows device manager an error with the display adapter for the NVIDIA card - "This device is disabled. (Code 22)"   So i tell the device to enable > restart > and get the same problem i've been having with ubuntu starting:  black screen during startup.  windows does it's blue-screen thing after about 30-45 seconds, i restart to last known good config, and go download the latest nvidia drivers for windows.  restart > everything comes up fine > open device manager > "Windows has stopped this device because it has detected problems (Code 43)".  ugh.    i went through the microsoft support site for a while and came up with no good solutions.

so i'm thinking there might actually be a problem with the hardware in my machine.  either the card itself is bunk... or the bus it's in is janky... not too sure.  i'll have to dig around my "parts box" to see if i have another video card i can use to see if it works.  

any thoughts on how to troubleshoot this?  or even how to get ubuntu to disable my video card and use it in "dumb mode"?  i mean, essentially i thought that's what i did during the install, but can't get it to do the same on the installed version.  

any help is appreciated
~Ben

---

### Post by sandyd on 2012-01-31
> **baslug said:**
> so i stepped away for a couple weeks to clear my head.  this morning i fired up windows on the same machine with intentions of clearing out another hard drive i have in order to reformat it and run a new installation of ubuntu on it - dont know why it should be any different than installing on the same drive as windows in a different partition, but i thought the fresh start would do me some good.

i noticed in the windows device manager an error with the display adapter for the NVIDIA card - "This device is disabled. (Code 22)"   So i tell the device to enable > restart > and get the same problem i've been having with ubuntu starting:  black screen during startup.  windows does it's blue-screen thing after about 30-45 seconds, i restart to last known good config, and go download the latest nvidia drivers for windows.  restart > everything comes up fine > open device manager > "Windows has stopped this device because it has detected problems (Code 43)".  ugh.    i went through the microsoft support site for a while and came up with no good solutions.

so i'm thinking there might actually be a problem with the hardware in my machine.  either the card itself is bunk... or the bus it's in is janky... not too sure.  i'll have to dig around my "parts box" to see if i have another video card i can use to see if it works.  

any thoughts on how to troubleshoot this?  or even how to get ubuntu to disable my video card and use it in "dumb mode"?  i mean, essentially i thought that's what i did during the install, but can't get it to do the same on the installed version.  

any help is appreciated
~Ben
Add "nomodeset" (no quotes) to DEFAULT_GRUB_OPTS (is it named that in Ubuntu? I don't know.).

Run ```
 sudo grub-update
```

---


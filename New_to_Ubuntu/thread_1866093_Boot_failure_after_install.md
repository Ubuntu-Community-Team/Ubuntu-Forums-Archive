---
title: "Boot failure after install"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by rjotoole on 2011-10-20
I've spent quite a bit of time looking through various threads on the forums and the Ubuntu community webpages but can't seem to find the solution to something that I am hoping is simple. I was able to complete the installation of ver 11.10 on a Gateway laptop _only_ after I removed "quiet splash--" at the end of the boot options line _and_ selected** "**[B]acpi=off"
After the restart it failed to boot. It displays the GRUB menu screen with the 4 options that include Ubuntu and Ubuntu (recovery mode). So I see in a help page that I would need to change the boot parameters to match what worked in the installation. I've tried that by pressing "e" to edit the commands and removed quiet splash and adding acpi=off to different locations but I still can't get it to boot up.  It will either begin loading and running scripts and then just hang or go into a blank screen depending where I put the acpi=off command. The last done I get is typically running /scripts/init-bottom
I'm getting frustrated. What am I missing? 
[/B]

---

### Post by oldfred on 2011-10-20
Welcome to the forums.

Sometimes it is your acpi=off plus other settings particularly video.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

If you find the combination of settings that works then you need to add it to /etc/default/grub.

gksudo gedit /etc/default/grub

[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMDLINE_LINUX
    * Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   * This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

### Post by rjotoole on 2011-10-21
I went back and had another look at the commands that it was trying to pass and "vt.handoff=7" was always showing up. Upon deleting that it allowed my system to boot _much_ further. After checking files and blocks it starts up devices and I get OK for all but a [fail] when trying to stop automatic crash report generation. It gets a little further and then stops.
Even though I work in IT and know my way around computers this is taking a lot of time. I've got to wonder if I'd be better off with version 10.04 LTS ?

---

### Post by rjotoole on 2011-10-23
After a lot of trial and error I finally figured out what worked. "nomodeset" was the other option that needed to be added to "acpi=off". Just those two settings for the Gateway laptop I'm using.

---


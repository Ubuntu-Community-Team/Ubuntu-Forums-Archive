---
title: "Can't get Ubuntu to install"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by GrantRS on 2012-07-25
I have 12.04 running on another computer.  I have been trying to install 12.04 on a ACER with Vista.  I am running from a 12.04 Disk which seems to be OK.  It installed on an other computer.  The only way I can get Ubuntu is on the Demo.  But I must use the F6 option with NOLAPIC checked.  Then the Demo will run.  If I try to install Ubuntu alone or beside Vista, it gets to the end and states restart your computer and then will not bring up Ubuntu.  I can get back to Vista using the menu.  Have tried various ISO Disks and still same result.  Any help would greating be appreciated.

---

### Post by oldfred on 2012-07-25
If you needed a parameter to boot liveCD, then you almost for sure need it to boot once installed. With video you may install new drivers that then do not need parameters.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You add it each time you boot with e on the grub menu, add or replace existing parameters of quiet splash. Then when you find the parameter or set of parameters that work, you can edit grub to make it permanent.

gksudo gedit /etc/default/grub:
sudo update-grub

Change this:
GRUB_CMD_LINUX_DEFAULT="quiet splash"
or 
GRUB_CMD_LINUX=
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
> GRUB_CMD_LINUX
    * Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMD_LINUX_DEFAULT="quiet splash"
   * This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 




---

### Post by mapes12 on 2012-07-25
Give the text based installer a try:-

[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

I had a machine a while back that couldn't handle the GUI installer but the text based version got it going.

---

### Post by GrantRS on 2012-07-26
Many, Many thanks.  System is up and running.  Used the NOLAPIC boot option.  Also, used the Alternate 12.04 CD.  Thanks for the speedy response.  By the way, I'm 78 yrs old, can you match that 
Old Fred?

---

### Post by GrantRS on 2012-07-26
Many thanks.  I did not have to use the Text version.  Used the Alternate CD Boot Disk, with the boot option of NOLAPIC.  Thanks for your respond.

---

### Post by oldfred on 2012-07-26
Glad you got that working.

Not really all that old, just a handle. I actually am first year baby-boomer which gives away my age. :)

---


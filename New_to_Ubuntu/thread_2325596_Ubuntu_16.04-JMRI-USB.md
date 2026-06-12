---
title: "Ubuntu 16.04-JMRI-USB"
date: 2016-05-23
forum: New to Ubuntu
---

### Post by JoAnn_Donaldson on 2016-05-23
I have Ubuntu 16.04 installed. I also installed JMRI. When I try to select the USB port in JRMI it says No ports.
So I did a sudo lsusb -c and it found the USB port for the Digitrax PR3.

So how do I setup a USB port so that JMRI will communicate with the PR3?

---

### Post by JoAnn_Donaldson on 2016-05-26
[Solved]
I got this from the JMRI User Group and now it works. I suspect this procedure will work with any USB device.

[COLOR=#000000][FONT=Georgia]Run the following command developed by Dave Heap. Copy and  paste it[/FONT][/COLOR]
[COLOR=#000000][FONT=Georgia]exactly.  When it runs it will display the last 10 /dev entries each[/FONT][/COLOR]
[COLOR=#000000][FONT=Georgia]second.  As you plug and unplug the PR3, a device name should appear and[/FONT][/COLOR]
[COLOR=#000000][FONT=Georgia]disappear.  That will be the name you  will need for JMRI.  Use control-[/FONT][/COLOR]
[COLOR=#000000][FONT=Georgia]c to stop the command.[/FONT][/COLOR]

[COLOR=#000000][FONT=Georgia]while : ;do clear;ls -lt /dev|head;i=$((i+1));echo $i;sleep 1;done[/FONT][/COLOR]

[COLOR=#000000][FONT=Georgia]You also need to make sure that you have assigned the dialout group to[/FONT][/COLOR]
[COLOR=#000000][FONT=Georgia]your user:[/FONT][/COLOR]

[COLOR=#000000][FONT=Georgia]sudo adduser ${USER} dialout
[/FONT][/COLOR]reboot system to take effect.

[COLOR=#000000][FONT=Georgia]The last rule is that you NEVER run JMRI as root.[/FONT][/COLOR]

---


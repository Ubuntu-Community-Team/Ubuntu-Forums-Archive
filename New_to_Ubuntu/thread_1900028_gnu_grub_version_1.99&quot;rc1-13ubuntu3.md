---
title: "gnu grub version 1.99&quot;rc1-13ubuntu3"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by eckzwolfe on 2011-12-25
ok i am a complete newbie and i am having a problem booting up my ubuntu. its going to a black screen stating "Mininmal BASH-like editing is supported etc" any help please?

i have my live usb ready to go as i have seen in previous posts.... jus need to know where to go from there.

thnx for any help in advance.

---

### Post by lolpenguin on 2011-12-25
You went one step too far.
When you turn on your computer, enter the BIOS boot menu (F12, F10, ESC, F8, varies for different manufacturers) and select the USB device, and you will boot into the LiveUSB. If you go to GRUB, the reboot and try again.

---

### Post by eckzwolfe on 2011-12-25
sry if i didnt explain it correctly. i need help getting my ubuntu to boot. everytime i start it,it goes to the black screen with the "minimal bash-like" message.

---

### Post by oldfred on 2011-12-25
Several things to try. If at grub or grub rescue you can try manual boot, or download some apps that can do minor fixes or boot without grub so you can then fix grub.

Boot Repair, both app to download into Ubuntu liveCD/USB or liveCD:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

If that does not work then try these but again use hd0,X and sdaX that is your install's partition - hd0,2 & sda2 shown as example.
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/initrd.img
boot

If none work post boot script output from boot repair.

---

### Post by eckzwolfe on 2011-12-25
i tried the boot repair thing but its not working, and i dont think im getting a grub rescue screen because it looks like this

"[CENTER]GNU GRUB  version 1.99"rc1-13ubuntu3[/CENTER]

Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command complections. Anywhere else TAB lists possible  device or file complections

grub> _"

so i have no idea what to do?.:(

---

### Post by eckzwolfe on 2011-12-26
well i clicked the button to create a boot info script on the boot repair tool, but i can't seem to find it :confused:, so i guess I'm just going to bite the bullet and do a fresh install. :(

---

### Post by oldfred on 2011-12-26
Boot repair gives a link to the location of a web page where it posts the boot info script. There is a copy hidden away somewhere but if booting from LiveCD or USB it will not be saved.

Did you try typing the manual boot commands at the grub> prompt?

If you have nothing to save, reinstall can often be the easiest solution.

---


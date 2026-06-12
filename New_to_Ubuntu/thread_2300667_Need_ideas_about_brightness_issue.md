---
title: "Need ideas about brightness issue"
date: 2015-10-27
forum: New to Ubuntu
---

### Post by bobanco on 2015-10-27
Hey guys

I've been trying to solve the persistent maximum brightness issue on my laptop.

This is the command that works for me: "echo 0 > /sys/class/backlight/acpi_video0/brightness" and it's in the rc.local file so it can be executed on startup. The issue is that the rc.local file doesnt have permission to write in the brightness file.

I tried changing the permission of the brightness file so the script would run anytime, but the permissions are getting restarted on every reboot.


Do you have any ideas how i can work out this problem, except echo-ing my password in the rc.local file ?


P.S the button shortcuts for changing the brightness work flawlessly.

---

### Post by raketax on 2015-11-12
Hello,

You can try this, maybe it will work for you:

sudo gedit /etc/default/grub

 Edit two lines to read as follows: 

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
 GRUB_CMDLINE_LINUX="acpi_osi=Linux"

 sudo update-grub

---


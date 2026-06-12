---
title: "Changing brightness?"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by GalaxyLinux on 2012-04-22
the brightness buttons don't work. When I press them the symbol shows up on the screen to indicate a change in brightness but nothing actually happens.

---

### Post by GalaxyLinux on 2012-04-22
please help

---

### Post by NikTh on 2012-04-22
Hi , 
try to boot with option **acpi_osi=Linux** . Do as follow 
```
sudo gedit /etc/default/grub 
```Then find line **GRUB_CMDLINE_LINUX=""** . Make that line exactly like this  [B]GRUB_CMDLINE_LINUX="acpi_osi=Linux"
[/B]Save and close. 
Then do 
```
sudo update-grub
```and reboot to see if problem fixed.

---

### Post by GalaxyLinux on 2012-04-22
It worked, thanks. Where do you get this type of knowledge to begin with? Is there any documentation on this stuff?

---

### Post by NikTh on 2012-04-22
> **GalaxyLinux said:**
> It worked, thanks. Where do you get this type of knowledge to begin with? Is there any documentation on this stuff?


Of course there is documentation . Actually i am starting to think that here in this forum everything exists. 
Here you are --> [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) . 
This is one of my favorite bookmarks :)
Glad that worked .

---


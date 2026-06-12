---
title: "[all variants] How to splash images in Grub, simple way"
date: 2008-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by dentaku65 on 2008-09-19
Here a simple way to add splash image on Grub menu without make *the ritual of seven virgins* or to make the *sacrifice for the bloody pentacle*.

Install packages:
```
sudo apt-get install startupmanager grub-splashimages
```
Execute startupmanager app.:
```
sudo startupmanager
```
Now you have a GUI interface, choose in sequence:
**Tab Boot options:**
[LIST=1]
[*]Flag the option "Use timout in bootloader menu"
[*]Timeout in seconds "5"
[*]Default operating system "Use the one selected"
[*]Display resolution: "Choose your own" (in my case 1024x768 )
[*]Display color depth: "16 bits" (mandatory)
[*]Misc. Flag all 3 options
[/LIST]
**Tab appearance options:**
[LIST=1]
[*]Under Bootloader themes flag the option "Use background image for bootloader menu", then under dropdown list "Grub background image" choose one from the list, preview is not available (my favourite one is "fiesta")
[/LIST]
Then click on Close button and reboot your box.

You will get a very nice grub image menu

---


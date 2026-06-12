---
title: "Graphics Driver Problem when Booting Installed 11.10"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by Cheeky88 on 2012-02-11
I absolutely need to use 11.10 because the wifi works gloriosly on it (from my experience on the live cd). 

Unfortunately, once I install 11.10 and boot it, I get a glitched purple screen that doesn't go away. I need to be able to:

a) allow ubuntu to finish the installation (if I click "don't ask for password" I assume leaving it on the glitched screen for a few minutes will allow it to finish installing?

b) Somehow install the AMD drivers I downloaded. I believe they are a .run file. Can I somehow boot a text mode and install these from a USB or something? Please help?

I am running an AMD HD 6850 and it hates 11.10, but runs fine on the drivers I installed on 10.04 LTS

---

### Post by oldfred on 2012-02-11
I do not know about AMD drivers. Have you tried nomodeset?

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---


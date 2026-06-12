---
title: "after nvidia driver installation, everything looks bigger on the screen"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by stonecoldjha on 2012-03-18
Hi,
I installed lubuntu 11.10 and everything was working well, including the videos. Then, I installed the nvidia driver through preferences>additional drivers activating the recommended version. But after a reboot, everything looks bigger on the screen, inlcuding all applications, system fonts, the panel, everything, except for the webpages that appear in mormally sized fonts on firefox, and the videos too play fine. What should i do to fix this? Any help appreciated..thanks!!!

---

### Post by mraandtux on 2012-03-18
What is your monitor and desktop size? Also which NVIDIA video card model did you use?

---

### Post by kc1di on 2012-03-18
go to system settings and look for the Nvidia settings manager you should be able to change your desktop resolution there.

---

### Post by NikTh on 2012-03-18
Also you can open a terminal and 
```
sudo nvidia-xconfig
``` then reboot .

---

### Post by stonecoldjha on 2012-03-22
my graphics card is nvidia geforce 6200, and the native resolution of my screen is 1280x1024. I opened nvidia x server settings, and it shows the same resolution to be the current one. i did sudo nvidia-xconfig in the terminal
sonu@sonu-desktop:~$ sudo nvidia-xconfig
[sudo] password for sonu: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

sonu@sonu-desktop:~$
its still the same, even after a reboot.

---

### Post by stonecoldjha on 2012-03-22
i am attaching a screenshot illustrating the problem

---

### Post by stonecoldjha on 2012-03-27
bump!!

---

### Post by U235master on 2013-01-26
I had this same problem, and I think I found a way to fix it. Just reduce the font size of all your system fonts. I think you can do this in Customize Look and Feel for lubuntu

---


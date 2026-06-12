---
title: "How to install NVIDIA drivers on Asus UL80VT?"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by Aees on 2013-03-16
Hello, i installed ubuntu 12.10 (64bits) two days ago, i'm a completely new ubuntu user so i don't know much yet. 
I tried to install the nvidia dirvers but i couldn't. I have a Asus UL80VT with a Gforce G210m. I intalled jockey-gtk but it didn't work, so i download the drivers for linux from nvidia official page and tried this ([http://kuyne.blogspot.com/2012/03/instalar-drivers-de-nvidia-manualmente.html?m=1](http://kuyne.blogspot.com/2012/03/instalar-drivers-de-nvidia-manualmente.html?m=1)) : 

[B]sudo apt-get install build-essential linux-headers-$(uname -r)
[/B][B]sudo apt-get remove --purge nvidia*
[/B][B]sudo apt-get remove --purge xserver-xorg-video-nouveau
[/B][B]sudo gedit /etc/modprobe.d/blacklist.conf

add [/B]this to the file and save:
[B]blacklist vga16fb 
[B]blacklist nouveau 
[B]blacklist rivafb 
[B]blacklist nvidiafb 
[B]blacklist rivatv 

[/B][/B][/B][/B][/B]**sudo /etc/init.d/lightdm stop **
go to the terminal: CTRL+ALT+F1
login with you user
[B]sudo reboot
[/B][COLOR=#444444][FONT=Arial]**sudo sh NVIDIA.run**
[/FONT][/COLOR][B][FONT=Arial][SIZE=3][COLOR=#444444]sudo service lightdm start[/COLOR][/SIZE][/FONT]

[/B][FONT=Arial][SIZE=3][COLOR=#444444]but when i enter[/COLOR][/SIZE][/FONT]**[FONT=Arial][SIZE=3][COLOR=#444444] sudo sh NVIDIA.run [/COLOR][/SIZE][/FONT]**[FONT=Arial][COLOR=#444444]appears this message: 

 [/COLOR][/FONT][COLOR=#333333][FONT=lucida grande]failed to tun "/usr/sbin/[/FONT][/COLOR][COLOR=#333333][FONT=lucida grande]dkms build -m nvidia -v 310.40 -k 3.5.0-25generic": Error! Your kernel headers for kernel 3.5.0-25-generic cannot be found. Please install the linux-headers-3.5.0-25-generic package, or use the --kernelsourcedir option to tell DKMS where it's located[/FONT][/COLOR]

please someone help

---

### Post by mörgæs on 2013-03-16
Moved as this is not specific to Asus. 

Next time please use text colours and fonts sparingly.

---


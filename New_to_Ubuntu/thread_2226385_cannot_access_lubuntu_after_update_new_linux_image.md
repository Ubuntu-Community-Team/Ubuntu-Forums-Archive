---
title: "cannot access lubuntu after update new linux image generic 3.13.0.27"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by Leviata on 2014-05-27
What's going on with this  linux image generic 3.13.0.27? :(

From that before when i install lubuntu 14.04 my linux image was 3.13.0.24
Until today their is a new linux image generic 3.13.0.27 
install my lubuntu while I update my lubuntu software updater
after reboot my screen goes black too long unable to access

until I've to go Advance mode and find out that their is 2 linux images option like this:
[COLOR=#0000ff]linux image generic 3.13.0.27 <<< Black Screen & nothing but garbage.....
linux image generic 3.13.0.27 (Recovery Mode) <<<Helps Nothing
linux image generic 3.13.0.24 <<< Right now I'm online here with this. Seems running well
linux image generic 3.13.0.24 (Recovery Mode)[/COLOR]

What should I do with this linux image generic 3.13.0.27? Is it incomplete install?
Or is my Asus K43TA laptop not support this linux image vesion?
If not what should I do to make it work with lubuntu?
Rightnow I've go to advance mode it's sounds like I've to stay with this old[COLOR=#0000ff] [/COLOR]3.13.0.24 
for eternity & cannot upgrade lubuntu with this new linux image anymore[COLOR=#0000ff].[/COLOR].... this wierd bug is so vexing.[COLOR=#0000ff]
[/COLOR]I've burn my precious 3 day tweak my lubuntu+xfce into win8 nicely but took arrow from the knee by this new linux image.](*,)[COLOR=#0000ff][/COLOR]

---

### Post by sudodus on 2014-05-27
Things like this happen. It is the reason why old kernels are kept instead of being overwritten or deleted automatically. Probably there is some problem with a driver's cooperation with your graphics card. Maybe some other hardware has the problem.

You can try some boot options. See these links

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub](https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub)

add boot options permanently using either of the following entries in the **/etc/default/grub** and run ***sudo update-grub***

***GRUB_CMDLINE_LINUX*** 

[LIST]
[*]Entries  on this line are added to the end of the 'linux' command line (GRUB  legacy's "kernel" line) for both normal and recovery modes. It is used  to pass options to the kernel. 
[/LIST]

***GRUB_CMDLINE_LINUX_DEFAULT=***"quiet splash" 


[LIST]
[*]This  line imports any entries to the end of the 'linux' line (GRUB legacy's  "kernel" line). The entries are appended to the end of the normal mode  only.
[LIST]
[*]To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 
[/LIST]
   
[/LIST]

---

### Post by Leviata on 2014-05-27
Thank you for answering I'll try you reccomend first. I'm not sure if it's going to work but I'll report after try solving it.
Because right now my virtualbox seems to rely on both 3.13.0.27 & 3.13.0.24
So I've to make sure remove/reinstall that linux image to not affect my virtualbox.

---

### Post by Rob Sayer on 2014-05-28
You should know which video driver is in use.  Put this in the terminal:
 
```
sudo lshw -c video
```

I suspect it's the open source one because as a quick search said your machine uses the AMD 780G gpu, which uses the AMD 3xxx series chipset.  This isn't well supported in linux anymore.  I've had this issue with an older Compaq laptop.

If it is an older AMD gpu, do not try to solve this by using "Additional Drivers" or installing the proprietary AMD driver.  You'll definitely bork the video.

Definitely try sudodus's recommendation.  Also try enabling nomodeset when booting into the newer kernel.  It's been a while since I did this so you should do a search.

I don't think this is a kernel bug but frankly poor hardware support on AMD's part.  Assuming it IS actually an AMD gpu, you should be able to get it working but don't expect great performance.

BTW I would consider using an older kernel version just a temporary stopgap measure to get things going again.  Holding back the kernel to an older one may solve that problem.  But it's going to create other ones.

---


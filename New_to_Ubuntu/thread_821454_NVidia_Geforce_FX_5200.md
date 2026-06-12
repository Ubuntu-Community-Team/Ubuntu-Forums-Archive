---
title: "NVidia Geforce FX 5200"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Itsamnaaj on 2008-06-07
Hello Ubuntu community,

I have installed Ubuntu 8.04 yesterday and have been having a blast plumbing its many secrets. There is one problem though: as my Geforce FX 5200 video card hopelessly sucks, Ubuntu can't recognize it (unless I delete the xorg.conf file, GNOME won't run at a resolution higher than 800x600).

I would like to have someone explain to me with tiny baby steps how to set up my Geforce FX 5200 in Ubuntu (including 3D support, so I can even enjoy my games). I have already installed the drivers from the NVidia website, read the manual, manually adapted xorg.conf and tried installing with 'Envy', to no avail. 

I would be very grateful if someone managed to guide me through this mess :)

Thanks in advance,

- Itsamnaaj

---

### Post by lostlinuxkiwi on 2008-06-07
I've got the same card and the first time I installed kubuntu 8.04 it couldn't find the proper drivers for it either and envy didn't help. I still had the right resolution though so I didn't have to go through the xorg drama. Anyway, I later uninstalled and then reinstalled it for various reasons and the second time it picked it up with no trouble. I dont know why

This probly doesn't help much. But if worst come to worst try a reinstall. It shouldn't be too bad if you have only just installed it anyway.

---

### Post by ChameleonDave on 2008-06-07
I have the same card on one of my machines, and it works, with glitches.

You ought to do a search for "FX5200" on these fora first.  Your answer is probably already here.

---

### Post by brigadoon on 2008-06-07
The NVIDIA drivers seems to have an issue recognizing the resolution modes of some monitors. It's a NVIDIA issue, not a Ubuntu or Linux issue. I have an older NVIDIA GForce4 420 Go on a Toshiba laptop. I was able to fix the resolution problem plus several other issues. I have posted my solutions at the following link...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

Some of my fixes may help you out. If my post needs clarification on how to do something post a message and I'll try to help you out. Good luck.

---

### Post by brigadoon on 2008-06-07
> **lostlinuxkiwi said:**
> Anyway, I later uninstalled and then reinstalled it for various reasons and the second time it picked it up with no trouble. I dont know why

There have been two updates very recently for NVIDIA and XORG.CONF related files. It sounds like you got lucky and they fixed a problem for you. The updates didn't work out for me and I had to fix some things to get my resolutions and OpenGL working correctly.

---

### Post by Itsamnaaj on 2008-06-07
Thanks a lot for the swift responses! There's something those expensive Indian help desk employees on Microsoft's pay roll couldn't do. 

I will reinstall first, then go through Brigadoon's walkthrough (I, too, am an avid Neverwinter Nights player).

---

### Post by Itsamnaaj on 2008-06-07
Brigadoon, I tried all the steps in your walkthrough, but I cannot compile an EDID binary file because nvidia-settings **won't even work**. It says I'm not running an NVidia X server.

In other words, I am completely stuck - can anybody help me?

---

### Post by brigadoon on 2008-06-07
> **Itsamnaaj said:**
> Brigadoon, I tried all the steps in your walkthrough, but I cannot compile an EDID binary file because nvidia-settings **won't even work**. It says I'm not running an NVidia X server.

In other words, I am completely stuck - can anybody help me?

I did have the same problem. I found that all traces of the Nvidia driver needed to be uninstalled and you must be in terminal mode to make edits. Try the following step by step...

1) Use Envy to uninstall any traces of Nvidia. All traces of the driver need to be removed. Envy saves a lot of typing and does a good job of flushing out the system. Reboot when asked.

2) Replace the xorg.conf file with a new one. With the recent updates from Nvidia, Xorg and Ubuntu I found that my xorg.conf file had some lines that did not apply any more. You may be suffering from the same problem. I have to make the following statement...

***You proceed at your own risk!!!***

I did the following...

***CTRL+ALT+F1*** "Jumps to the 1st console"
type ***sudo /etc/init.d/gdm stop*** "Stops GDM"
type ***sudo dpkg-reconfigure -phigh xserver-xorg*** "backs up the old xorg.conf file and installs a new one with no switches."
type ***sudo /etc/init.d/gdm restart*** "Starts GDM. You should automatically switch back to the log in of the desktop"

3) Use envy to reinstall the Nvidia driver. The auto detect hardware should work. The xorg.conf file should be updated with any required modifications when the driver installs. With luck this shall fix your problem. If the higher resolution is still unavailable keep going...

4) You should find the Nvidia console in one of two places...

Applications/System Tools/NVIDIA X Server Settings

or

System/Administration/NVIDIA X Server Settings

With any luck you'll be able to access the Nvidia X server console and make a edid.bin file to edit per my other post.

Please keep in mind that the edits in my post are for the monitor on my laptop. The resident display modes of your display may be different.

Hopefully step 3 is all you'll need to do.

---


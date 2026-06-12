---
title: "ati driver question"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by editheraven on 2011-12-05
I have ati radeon hd6770. The propietary driver, downloaded from additional drivers, says that it has only 2d acceleration. i once found that i can install some testing drivers, made for linux. They were meant to suport any nvidia/ati card, but it was highly beta. Still, i want to try them, as i have some problems with the native ones. Where can i find them?

---

### Post by mastablasta on 2011-12-05
you are talking about opensource drivers. they are the ones installed by default. the beta/experimental bleeding edge drivers can be installed via PPA. 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

you need to remove the proprietary drivers first. here is how: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

here is more info on opensource driver.

What you could do is try to download the driver form ATI website and then compile it yourself. you would get the latest version that way.

---

### Post by 2F4U on 2011-12-05
> suport any nvidia/ati card

Thats very unlikely since nVidia and ATI have totally different proprietary drivers since thats their intellectual property. Usually, you can download drivers directly from the manufacturers web site, for example

[http://support.amd.com/us/kbarticles/Pages/AMDCatalystOpenGL42BetaLinux.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalystOpenGL42BetaLinux.aspx)

I don't know if that are the drivers you are looking for, but at least they are beta.

Note that you probably won't get much support for these in case something goes wrong and be prepared that installation probably requires manual interaction.

---

### Post by editheraven on 2011-12-05
I have downloaded the proprietary driver from ati/amd site (the run file) that installed ati catayst and (supposted) driver. But even upon restart, the driver could not be loaded by kernel. So i had to install the ati driver from hardware drivers gui. I hope i will find better 3d performance (no in games, in gnome 3d effects) with edge drivers.

---

### Post by editheraven on 2011-12-06
Hello. I came back.

I have upgraded all my packages, including xorg. I have a lot of xorg related packages, so i'll link a prinscreen to view the version of them : [http://i.imgur.com/cB4di.jpg](http://i.imgur.com/cB4di.jpg) .
If I install ati fglrx, the scrool resumes at "Checking battery state"

If i switch the desktop tty and "sudo xinit" and "start gdm" or "sudo startx" i get this xorg log : [http://www.text-upload.com/read.php?t=8274](http://www.text-upload.com/read.php?t=8274) . Removing the fglrx, i can boot normally.

ps : xserver (xinit) starts without problem, only the gdm won't start (startx).


le : i did this 
  ```
sudo apt-get remove --purge fglrx*   sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon    sudo apt-get install xserver-xorg-video-ati   sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core   sudo dpkg-reconfigure xserver-xorg
```.

I have good 3d acceleration, better that fglrx one.

---


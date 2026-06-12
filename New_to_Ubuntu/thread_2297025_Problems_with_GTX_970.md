---
title: "Problems with GTX 970"
date: 2015-09-30
forum: New to Ubuntu
---

### Post by Amur_Ghose on 2015-09-30
First post here. I recently tried installing Ubuntu to provide an alternative python environment in the PC. However, there were severe issues with NVIDIA drivers ( probably because my card, GTX 970, is a relatively new one ) and I had to start in low graphics mode. I went into the terminal and tried getting nvidia-current , but that provided me with a login screen where upon login I would be redirected back to the login following a black page of crash.

Due to these NVIDIA issues, I went back into Windows, deleted the Ubuntu partitions, ran my Windows 10 disk and repaired the windows boot manager to avoid GRUB. I am now back at square one, and would like to try again.

Does Ubuntu 15.04 have native support for NVIDIA GTX 970 (The version I used was older, 14. something) ? If not, how should I go about the support ? Do I need drivers from nvidia's website instead of getting nvidia-current ? Will the older GRUB cause issues ?

Finally, even though this is the Ubuntu forum, is there a more NVIDIA-friendly distro I can try ? I am open to trying something else if Ubuntu doesn't work out.

---

### Post by oldfred on 2015-09-30
Best to use newest Ubuntu version, or Linux distribution with newest kernel, support software and add a ppa to install newest nVidia driver. Do not install directly from nVidia as that leads to other issues.
While not LTS, it will work better.

 NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

      
 Asus z97-A with nVidia GTX 970 Ubuntu  15.04
[http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896](http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896)

Ubuntu now has a new ppa which will eventually be part of install.

       
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa.

---

### Post by grahammechanical on 2015-09-30
Ubuntu is not unfriendly to Nvidia. And all Linux distributions will depend upon Nvidia drivers for issues like this. And Nvidia drivers are proprietary software and cannot be modified by Ubuntu developers. One of the prime aims of Ubuntu developers is to release stable versions of Ubuntu which is why the Additional Drivers utility does not supply the very, very latest drivers from Nvidia.

There is a new Ubuntu release every six months and with newer hardware it is best to use the latest version of Ubuntu. And at the moment that is 15.04. But you may need Ubuntu 15.10 and that will be released at the end of October. Although pre-release images are available right now.

I am running the development version of 15.10 right now and it is stable. But I cannot tell you what versions of the nvidia drivers are available because the latest Nvidia drivers do not support my old video card and therefore Additional Drivers will not offer them to be installed. I know from experience that installing the very latest Nvida drivers will break my OS.

My advice to you would be to install without ticking the box "Install third party software." Then you will not get a proprietaty driver installed and the restart will run on an open source video driver. Once you have a working desktop then see what Additional Drivers has to offer.

The Try Ubuntu session uses the open source video driver. So, if the live session loads to a desktop, in my opinion, it is sensible to install and run with the open source video driver and experiment with proprietary video drivers once we have a working system.

By the way, the command to install a standard proprietary video driver that comes with a particular version of Ubuntu is

```
sudo ubuntu-drivers autoinstall
```

to see what drivers are available for a video adapter

```
sudo ubuntu-drivers devices
```

To get the latest daily ISO image of 15.10 (wily werewolf). Look for wily-desktop-amd64.iso

[http://cdimage.ubuntu.com/ubuntu/daily-live/current/](http://cdimage.ubuntu.com/ubuntu/daily-live/current/)

Regards.

---

### Post by buzzingrobot on 2015-09-30
> **grahammechanical said:**
> Ubuntu is not unfriendly to Nvidia. 


Agreed. I can't recall a problem using the "Additional Drivers" tool to install or uninstall an Nvidia driver.  

Nvidia.com can be used to learn which Nvidia driver supports a card. That, or subsequent releases, is the driver to use. Canonical's packages.ubuntu.com site can be searched by Ubuntu release to determine which drivers are available in the repos for that release. (I  find this site very useful in general: Dependencies are listed, changelogs are linked, source is available there, and debs can be downloaded for installation.)

On the other hand, if someone doesn't really need the capabilities of an Nvidia card, why tempt fate and install the proprietary driver? I don't, so I stay on Intel Haswell on this machine. (One of my pet peeves is video tearing. That seems to be down to the window manager.  E.g., I see it in XFCE on Intel or Nvidia.  I see it in Firefox on KDE on either chip, and on current 15.10 Mate images. Unity and Gnome, though, are very smooth on the Haswell.)

---

### Post by mc4man on 2015-10-01
For a 970 try the ppa's highest version of nvidia driver

Ot - As it seems the OP has a desktop card, this relates to optimus on laptops,
> **buzzingrobot said:**
>  (One of my pet peeves is video tearing. That seems to be down to the window manager.  E.g., I see it in XFCE on Intel or Nvidia.  I see it in Firefox on KDE on either chip, and on current 15.10 Mate images. Unity and Gnome, though, are very smooth on the Haswell.)

That's why I've never used the nvidia driver via nvidia-prime on linux. Recently have resolved about 99% of the tearing issues so have started using, the [semi-official ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") works best (355 is better than 352). I switch back & forth at times as for some things one is better than the other..

A test build of ubuntu-drivers-common that automatically will correct the tearing when switching from intel to nvidia is here with explain, ect.
[https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test](https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test)

---

### Post by nullsteph on 2015-10-24
Just got a [Clevo P750dm]("http://www.clevo.com.tw/clevo_prodetail.asp?id=810&lang=en") and I've been hearing that the integrated graphics are non functioning on these laptops, and that the graphic card is required.  Once I removed the GPU the system would not even POST, and there's really no graphics BIOS settings to tweak.  Is there any way around this, or am I stuck with Nvidia?

---

### Post by oldfred on 2015-10-25
Most do not have issues with nVidia. And tests show it works well.

 22-Way Comparison Of NVIDIA & AMD Graphics Cards On SteamOS For Steam Linux Gaming Oct 2015
[http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1](http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1)

---


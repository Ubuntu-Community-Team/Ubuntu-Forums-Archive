---
title: "Nvidia 1080ti and Ubuntu 17.10"
date: 2017-11-01
forum: New to Ubuntu
---

### Post by ruzil on 2017-11-01
I have a new PC with an NVIDIA 1080ti video card. I have installed Ubuntu 17.10. I changed the video driver to the NVIDIA binary driver from Software & Updates -> Additional Drivers. After this the screen appears too large for my monitor. I can fix this by going to NVIDIA X Server Settings and changing the Underscan property. Firstly, however, this doesn't persist between reboots. Secondly, this feels like a hack. Is there a problem with support for the latest video cards like 1080 ti and if so, how to resolve this?

---

### Post by grahammechanical on 2017-11-01
What Nvidia driver is Ubuntu 17.10 offering you? The Nvidia website is listing 384.90 as the required Linux video driver. But the release date is 2017 09 21 which may mean that it is too new for the Ubuntu developers to have included it in Ubuntu 17.10. I do not know about that.

[http://www.nvidia.co.uk/download/driverResults.aspx/124222/en-uk](http://www.nvidia.co.uk/download/driverResults.aspx/124222/en-uk)

Regards

---

### Post by oldfred on 2017-11-01
The ppa shows 384 & 387.

       Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)


 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available from ppa in addition
ubuntu-drivers devices 

But if you have already installed one, you must purge before installing another.
      
 #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 


 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


 If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by ruzil on 2017-11-02
Isn't the latest 384.90? I do not see any 387.

---

### Post by oldfred on 2017-11-02
They even show 18.04 already and 387.
This shows what the ppa show then show once installed.

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by ruzil on 2017-11-02
> sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available from ppa in addition
ubuntu-drivers devices

This is what I get as output from ubuntu-drivers devices after adding the ppa repository.

```
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001B06sv00001043sd000085F1bc03sc00i00
vendor   : NVIDIA Corporation
model    : GP102 [GeForce GTX 1080 Ti]
driver   : nvidia-384 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
```

---

### Post by oldfred on 2017-11-03
What does this show?
ubuntu-drivers devices

I think you are looking at what you have installed.
But if changing be sure to purge first.

---

### Post by ruzil on 2017-11-03
Yes, [COLOR=#000000]ubuntu-drivers devices [/COLOR]shows what I have installed.

---

### Post by monkeybrain20122 on 2017-11-03
Are you in Wayland or X? Nvidia driver doesn't work on Wayland. Make sure you choose Ubuntu-xorg in the login screen.

---

### Post by crackleplus on 2017-11-04
At the start I was also facing this problem with GTX 750 OC. but I figured out this problem. [;)]("http://crackleplus.com")

---

### Post by monkeybrain20122 on 2017-11-05
> **crackleplus said:**
> At the start I was also facing this problem with GTX 750 OC. but I figured out this problem. [;)]("http://crackleplus.com")
Care to share how? I think it is really rude to just say you have fixed  your problem without providing any hint.

---


---
title: "resolution problem on HARDY"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by obscur156 on 2008-04-26
Hi guys,i just installed Hardy and envyNG.So i have installed NVIDIA driver and i only have resolution 640X420 and 3?? x 2??.So everything is too big and there is some settings i cant access in nvidia settings like the half of the down screen of nvidia setting because its too big.

Somebody have an idea?

Everything was perfect in Gutsy and i have formatted,i hate my self sometimes cause i wanted to do a separate install and did not...

Thanks guys,best regards.

---

### Post by jgedutis on 2008-09-24
Is that the option if you go to Settings --> Preferences --> Screen Resolution?

When you reboot the system do you get the nvidia splash screen right before X loads?

You probably need to use the Nvidia X Settings tools

I have an nVidia 6200 that was giving me the same problem.  If you use the below command check and see if you have it loaded.  THe package is called nvidia-setttings.

taco@Fusion:~$ dpkg --get-selections | grep -i nvidia-settings
nvidia-settings					install

If you don't you can install if from a terminal by typing

user@Computer:~$ sudo apt-get install nvidia-settings

The you can get to it by System --> Administration --> Nvidia X Server Settings

Give that a shot and see if it gives you more options.  If the driver isn't loaded that utility will give you an error when loading.

---

### Post by jgedutis on 2008-09-24
I had some issues getting the nvidia restricted drivers to work with EnvyNG in Hardy with a Hauppauge HVR 1600 recording card.  You might try and remove additional hardware and disable some onboard devices and see if it loads and you have a conflict like I did.  I have the nvidia card working by not using Envy but just install the below packages.  

I uninstalled all the packages for Envy and nvidia already loaded and ran the below command to create a new xorg.conf file.

user@computer:~$ dpkg-reconfigure xserver-xorg 

follow the on screen instructions and it will create a default xorg.conf file.  Reboot and then load just the nvidia files shown below.  In addition I have xserver-xorg-video-nv loaded.


taco@Fusion:~$ dpkg --get-selections | grep -i nvidia
nvidia-glx-new					install
nvidia-kernel-common				install
nvidia-settings					install

---


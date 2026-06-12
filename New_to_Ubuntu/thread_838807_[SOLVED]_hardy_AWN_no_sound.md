---
title: "[SOLVED] hardy AWN no sound"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by guiliker on 2008-06-23
help! I have no sound!

I've got Hardy with an onboard sound chip which worked ok. I downloaded Avant Window Navigator because I wanted a pretty but functional desktop. I followed the rules getting AWN via Synaptic's ppa repository and deleting all the applets off the gnome panels before deleting the "naked" gnome panels. All worked fine until...I used the volume control applet on the AWN panel to increase the volume on a DVD I had just begun to watch. All sound disappeared along with the volume control icon. After reboot still no sound on any application. Through Windows XP Pro on vmware server according to the "sounds and (something)" option on control panel there is no sound device listed and no sound works on the virtualised OS.

I've done a scan of the forums/google and I can't find anything that helps. I've followed option 2 on [http://ubuntutip.googlepages.com/sound]("http://ubuntutip.googlepages.com/sound") and they all seem "on" except for one the first slider which I just tried to check but got an error?!?! :confused:

What have I done or not done or should do without redoing everything which is my usual solution?!?

in case helps: 
```
user@ubuntu:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0


```

---

### Post by guiliker on 2008-06-27
anyone interested in this have a look at the bug reported i've posted here [https://bugs.launchpad.net/awn-extras/+bug/243017/]("https://bugs.launchpad.net/awn-extras/+bug/243017/")

---

### Post by guiliker on 2008-12-02
Final fixed bug report [https://bugs.launchpad.net/awn-extras/+bug/245242]("https://bugs.launchpad.net/awn-extras/+bug/245242")

---


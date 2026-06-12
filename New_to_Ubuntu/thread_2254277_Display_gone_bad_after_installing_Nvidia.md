---
title: "Display gone bad after installing Nvidia"
date: 2014-11-26
forum: New to Ubuntu
---

### Post by rupjit-chak on 2014-11-26
Hello

Yesterday I installed NVidia drivers in my system (LTS 14.04.1).
After that the display was not displaying anything.
Then I did a bit of snooping and using the terminal I managed to get the display back.
However the resolution is 4:16 and I am not able to alter it.
I would like to bring to your notice the fact that when i purged and installed 
Nvidia drivers, each time at the end i got error status 1. 
I don't know what other information to include.
Please help

---

### Post by sudodus on 2014-11-26
Welcome to the Ubuntu Forums :-)

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will make it easier for us to help.

- Does your computer display better graphics when booted from the Ubuntu install DVD/USB drive? Or is it the same as now?

- What do you mean by the resolution is 4:16? Can you tell us the resolution in pixels (in the width direction and height direction, width x height)?

You can try to remove the nvidia driver. It should make the computer select the built-in free driver (probably nouveau for nvidia graphics).

---

### Post by rupjit-chak on 2014-11-27
Thank you
- Brand name and model : CQ40 604TX (comes preinstalled with Win 7 but I wanted to learn Linux so I replaced it with Ubuntu)
- CPU : Core 2 Duo
- RAM (size) : 2 or 3 GB (I don't remember exactly as one slot is empty)
- graphics chip/card : Ge103M
- wifi chip/card : Broadcomm 802.11 (Not sure)

Does your computer display better graphics when booted from the Ubuntu install DVD/USB drive? Or is it the same as now?
ANS : Yes. But I wanted to play games on my system so I went to the 
Software Update > Additional Drivers and changed it from nouveau to NVidia. Thats when all hell broke lose. Initially display was just a violet screen(my wallpaper) . After this : [http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver](http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver)  , my desktop came back alright but now it is big, very big.

Resolution is 640X480(4:3)
I can remove the nvidia driver but I want to keep it.
Please help.

---

### Post by sudodus on 2014-11-28
I suggest that you try another nvidia drive. Remove the one you use and install another one.

Then, in text mode (or in a terminal window), you should be able to install nvidia graphics drivers. Type

```
sudo apt-get install nvidia-TAB
```

TAB means that you press the TAB key (not that you type the three  letters TAB). You should get a list of available nvidia drivers. Then  make the command complete by adding the missing characters and press  enter to start the command. Reboot after the installation has finished.  If still no go, remove that driver and install another one.

I use nvidia-304 for my nvidia GeForce GT 430 card.

```
sudo apt-get install nvidia-304
```

Try the available drivers - let us hope that you find one driver, that  works well for you, probably another one than what works  for me.

If none of these drivers available in the Ubuntu repositories works, you can try drivers that you download directly from the nvidia web site, but it is more difficult to install them (or at least it was more difficult when I tried some year ago).

---

### Post by rupjit-chak on 2014-11-29
I am unable to make any changes. All settings seem to be be fixed.
On the top left of S/W Settings > Display window "Built in Display" is displayed. I am unable to change screen resolution, NVIDIA driver(revert changes or apply new changes).
Kindly assist

---

### Post by sudodus on 2014-11-29
Do you remember how you installed the nvidia driver?

1. From the repositories?

a. graphically with Synaptic or with the Software Center

b. with the command line

```
sudo apt-get install nvidia-something
``` where something can be 304 or current or ...

2. or from a package downloaded from nvidia's web site?

-o-

The removal will be different depending of the way you installed it.

If installed from the repositories you should be able to remove by

```
sudo apt-get remove nvidia-something
``` where something can be 304 or current or ...

You might be able to indentify the installed version using a combination of the following commands

1. Get a list of available packages by

```
sudo apt-get install nvidia-TAB
```

as described in a previous post and

2. and the following command

```
cat /proc/driver/nvidia/version
```

If installed from a package downloaded from nvidia's web site, you should find the way to remove it in the documentation provided by nvidia (or get tips from someone else, because I don't know).

-o-

If your installed system is new, it might be easier to backup your personal data and start from the beginning and reinstall it.

---


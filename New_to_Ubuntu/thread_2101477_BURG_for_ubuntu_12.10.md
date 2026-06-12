---
title: "BURG for ubuntu 12.10"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by coolbud012 on 2013-01-04
Hey guys I just shifted from win 7 to ubuntu with dual boot. and dont like the looks of grub so would like to install burg..would like to know that burg is compatible with 12.10 or not. And if yes then please let me know exact steps to download it.

Also do I need to make any changes in win 7. Please tell me step wise step, if I have to do anything on win 7 too..

Also is there any way to change the looks of my desktop? 


Thanks

---

### Post by DuckHook on 2013-01-04
Probably more important question is:

What is your own relative computer knowledge? Would you consider yourself a novice, typical or power user? This is the critical issue because people bork perfectly good systems all the time trying to fine-tune or achieve functionality while overreaching.

If a beginner, then I must point out that the worst problems for beginners are boot/partition problems. These make all of your installs inaccessible and have the real potential to wipe out all of your data. i.e. disaster.

So my recommendation is this:

1. Unless your grub install is completely broken (you can't boot up a critical OS) then leave well enough alone and live with it. If it's just a matter of aesthetics, you really don't want to be messing around with a bootloader until you are thoroughly well trained in bootloaders and partitions. And you want to train yourself on an unimportant machine, not your production one.

2. If you simply must fiddle with it, then back up all important data to external drive first and be prepared to lose every install on your HDD. It may not come to that, but you must plan for the worst.

3. Follow the instructions [here]("https://help.ubuntu.com/community/Burg").

Based on hints in your original post, I would discourage you from changing your bootloader.

P.S. The recent introduction of UEFI boot processes to replace BIOSes has only made matters worse and more complicated. Unless you know which boot methodology you used to install, you are only asking for trouble. Moreover, some threads have warned that BURG is not the best maintained project in Linux-space though I am first to admit that I have no basis for such conclusion except rumour. Proceed at your own risk.

---

### Post by audiomick on 2013-01-04
+1 DuckHook on point 1.

If the thing is working, leave it alone. You only see grub for a couple of seconds. If you want to mess around with the bootloader, get a second machine to practice on.

---

### Post by coolbud012 on 2013-01-05
Nopes I am not a beginner, but new to ubuntu .  Also I have faced this similar situation earlier while installing ubuntu for the first time.  So what would you suggest?

---

### Post by Pjotr123 on 2013-01-05
I suggest to make Grub itself look better, like this:
[https://sites.google.com/site/easylinuxtipsproject/beautifygrub](https://sites.google.com/site/easylinuxtipsproject/beautifygrub)

The Grub menu can be good-looking as well.... :)

---

### Post by grahammechanical on 2013-01-05
What is it about the look of the Grub menu that you do not like?

If you search from grub2-splashimages in the Ubuntu Software Centre you can download a set of images designed to be background images for the grub menu.

You might be able to find the images in /usr/share/images/grub folder.

Just copy an image into /boot/grub folder and run the command

```
sudo uppdate-grub
```

and the next time you boot it will be the Grub background image.

Do you want a larger text size? You need to edit a configuration file.

run

```
gksudo gedit /etc/default/grub
```

Look for the line that says

> #GRUB_GFXMODE=640x480

remove the hash ( # ), save the file and the text size will be at 640x480 resolution.

you may need to run

```
sudo uppdate-grub
```

again.

Regards.

---

### Post by coolbud012 on 2013-01-05
> **grahammechanical said:**
> What is it about the look of the Grub menu that you do not like?

If you search from grub2-splashimages in the Ubuntu Software Centre you can download a set of images designed to be background images for the grub menu.

You might be able to find the images in /usr/share/images/grub folder.

Just copy an image into /boot/grub folder and run the command

```
sudo uppdate-grub
```and the next time you boot it will be the Grub background image.

Do you want a larger text size? You need to edit a configuration file.

run

```
gksudo gedit /etc/default/grub
```Look for the line that says



remove the hash ( # ), save the file and the text size will be at 640x480 resolution.

you may need to run

```
sudo uppdate-grub
```again.

Regards.

Hi thanks for your reply... Aand is there any way to remove all the other entries from there... I just want win 7 and ubuntu in the options there... Also is there any way to make the selection graphical like burg do... But I must say your reply was really helpful..

Hey I just tried it and I am not able to copy the images into the grub folder in the boot directory and can I get more images?
Thanks

---

### Post by Pjotr123 on 2013-01-05
update-grub, not uppdate-grub.... :)

---

### Post by oldfred on 2013-01-05
Burg has not been maintained for a while, not sure if it even works with the new sub-menus.

       Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm  & post #28 for grub2 2.00
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

    
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---


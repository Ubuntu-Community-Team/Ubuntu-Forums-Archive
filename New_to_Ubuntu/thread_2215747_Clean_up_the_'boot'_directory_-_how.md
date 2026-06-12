---
title: "Clean up the 'boot' directory - how?"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by GarlicxSauce on 2014-04-08
Hi everyone,

I switched to ubuntu last month after too many years wasted on win and i'm happy about my choice. I've just encountered my first problem, i've looked it up in the past threads, but i could find a solution so here i am. 
I'm running Ubuntu 13.10 on a HP Pavillon g6 Notebook. So far i could update all the times it was needed ( when the auto update window was popping up), but since 2 days i can't update anymore and if i try, that's the message that comes up :

                         'The upgrade needs a total of 76,3 M free space on disk ' /boot'. Please free at least an additional 36,9M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.'

I've tried running that command, but it doesnt solve the problem. Also, i've installed Ubuntu just recently and my hard drive is quite empty so i dont really understand what is wrong. I've read in past threads NOT TO manually remove anything in the 'boot' section so i haven't.

Any help is greatly appreciated, many thanks in advance!

---

### Post by slickymaster on 2014-04-08
Hi [COLOR=#000000]GarlicxSauce, welcome to the forums.
[/COLOR]
You have several distinct ways to do it, but since you're starting in the *buntu ecosystem I would advise to use a graphical method, which basically consists on using a software called Ubuntu Tweak.
Ubuntu Tweak is an easy-to-use graphical tool that let you tweak ubuntu, and also, into the "Janitor" section you can clean the system, as well as remove older kernels. You can take it from here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

If you don't like this graphical tool you can do it manually. First check your kernel version, so you won't delete the in-use kernel image, running the following command at a terminal window:```
uname -r
```Now run this command for a list of installed kernels:```
sudo dpkg --list 'linux-image*'
``` and delete the kernels you don't want/need anymore by running this:```
sudo apt-get remove linux-image-VERSION
```Replace VERSION with the version of the kernel you want to remove.

When you're done removing the older kernels, you can run this to remove ever packages you won't need anymore:```
sudo apt-get autoremove
```

And finally you can run this to update grub kernel list:```
sudo update-grub
```

There's a pretty good tutorial on the subject over [here]("http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu-or-free-sp").

---

### Post by Impavidus on 2014-04-08
I read that on 13.10 simply running **sudo apt-get autoremove** would already remove old kernels. Just running that command may be enough. Else, use slickymaster's idea.

You may have plenty of hard drive space in total, but your hard drive has been partitioned in several pieces. One of them, the /boot partition, if full. The /boot partition is where your kernel images are stored. It has to be cleaned once in a while. Most users don't have a separate /boot partition, but if you encrypt your whole drive you'll get one automatically.

---

### Post by ibjsb4 on 2014-04-08
> **Impavidus said:**
> I read that on 13.10 simply running **sudo apt-get autoremove** would already remove old kernels. Just running that command may be enough. Else, use slickymaster's idea.

I have also read this about autoremove and 13.10 and on.

There is also a one the one line command for removing old kernels.

[http://tuxtweaks.com/](http://tuxtweaks.com/)

---

### Post by anaconda on 2014-04-08
To me, your problem sounds like you have a too small /boot partition.
If you have a big disk, and lots of free space, then you could easily have big enough boot partition too.  
Kernels are not that big. Even 1GB /boot partition would be big enough for you for many years. Without the need to remove old (unnecessary) kernels.

And if you remove kernels, be careful not to remove the kernel you re using. Type:
uname -r
in terminl to find out your current running kernel version... It is not 100% sure that it is the nevest kernel. Propably is though..

---

### Post by mörgæs on 2014-04-09
It's not only a rumour that **autoremove** removes old kernels. It actually works.

```
sudo apt-get clean
``` is also useful.

---

### Post by GarlicxSauce on 2014-04-10
Thank you so much everyone, i've tried with Ubuntu Tweaks and it worked just fine, but i'll keep in mind also the **sudo apt-get autoremove **command for the future.

It's great to have such a supporting community when you have tech issues, thanks :P

---

### Post by Double.J on 2014-04-10
Hey there, welcome to the forums!

Glad to read that your issue has been solved. I would just add a quick plus one to anaconda's advice about maybe having a bigger boot partition. If you've only had the system a month and successive images have filled boot, causing you to have to remove all but the current image, you'll A) have to perform this maintenance fairly regularly, and B) not have many back up kernels. Say an update came out that broke something, you would only have the latest kernel and the previous one. If the issue were in both, it'd be a pain. I'll admit this is very unlikely, I think i've had to boot from an old kernel in ubuntu once since lucid, but it's better safe than sorry.

All the best with you're *buntu journey! 

Jj

---


---
title: "VirtualBox is crazy!!"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by MongooseCage on 2008-05-08
Ok, I fiddled around pulled all the plugs on the net to get this XP thing working. Its working, well not so great, no sound,no graphics(i get a corrupt error), just plainly dead.

The problem, the minute I started getting the Virtual Box modules, my sound and my wireless died blatantly on me. So now I am running off of Ethernet. So how do I fix this? Nothings working properly anymore. Also my Avant Window Navigator wont pop up under maximized windows for no apparent reason, it has nothing to do with it. 

BTW, is it possible to get the graphics working well on XP? Because it would be nice to not have to restart everytime I want to play a game for a second or two...

I need it to work or I am going to have to boot in to Windows at school to get my wireless working. And you know how bad Windows is with Wireless in general when it is working. Ubuntu is awesome when its working but its a pain if its not.

---

### Post by MongooseCage on 2008-05-08
Oh yeah, now after a reboot it hangs at videos. Like everything just stops working all together. What is going on???

---

### Post by MongooseCage on 2008-05-09
> **MongooseCage said:**
> Oh yeah, now after a reboot it hangs at videos. Like everything just stops working all together. What is going on???

After I booted again I noticed that I had a second Ubuntu in there the same Hardy but another copy. It follows the same direction because it doesnt have Virtual Box too (after I uninstalled it). Strange...

But it atleast works, wireless and sound. Virtual Box is some crazy device. Has anyone had issues as such?

---

### Post by bumanie on 2008-05-09
I run windows in virtualbox and have never had an issue apart from one version precluded me from grabbing the virtual mouse-pointer. May be you should wipe that install (+ virtual hdd's) and start again.

---

### Post by sam123 on 2008-05-10
The same thing happened with me when I installed the virtualbox-ose-modules-386 package instead of the virtualbox-ose-modules-generic package. 

Check the kernel version you're running with cat /proc/version. If the version ends in 386, you'll need to uninstall the 386 version of the linux-image package and reboot.

---

### Post by MongooseCage on 2008-05-19
Thanks, Virtual Box is nuts though

---


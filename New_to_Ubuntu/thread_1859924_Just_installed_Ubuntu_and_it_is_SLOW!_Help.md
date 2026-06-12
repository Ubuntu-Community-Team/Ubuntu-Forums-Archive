---
title: "Just installed Ubuntu and it is SLOW!?? Help?"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by Druski on 2011-10-14
Well - I had just upgraded my Wife's computer, and this left me with a spare machine that I figured... why not dabble a bit with Linux, after all it don't need as much machine as windows... and perhaps I got a bit of life left in this machine etc..

Oh - and I am Linux challenged - so bare with me...

Ok - I installed Ubunto 11.10 32 bit from the Burned ISO CD I made. the install went pretty well, I used all defaults. I did have a problem with GRUB2 failing to install during the installation... and followed the instructions on the Ubuntu Wiki for re-installing (chroot method etc..) - seemed to work fine and Ubunto boots fine now.

Anyway this computer runs Windows XP fairly well, it came with XP... and it is not to slow or anything (until you start adding all the service packs and millions of emails etc...) HOWEVER with the fresh default install of Ubuntu this thing crawls along, disk thrashes a lot, and is graphically "chunky" etc... with the simpliest application like Firefox on a reasonably static non graphically challenging webpage - it is downright slow.

the System I am using is;

Dell Dimension 2350 computer
Intel P4 Processor 1.80 GHz
1 Gig of RAM
120 Gig ATA 133 Hard Drive
Standard IDE CD BURNER (no DVD)

I am using the standard onboard video (which at the moment I do not remember what it is)

is Ubunto 11.10 requirements for a smooth operating enviroment more than that PC?

---

### Post by aeiah on 2011-10-14
apparently ubuntu 11.10 is even more demanding than previous versions. you might want to consider trying out a lighter version on that hardware unless you really want the unity desktop stuff.

xubuntu should run fine, lubuntu will be even lighter but you may feel its a bit too bare

---

### Post by ubiquitin.jf on 2011-10-14
Have you tried booting into the Unity 2D environment? It'll be much easier on the machine and should run much faster.

---

### Post by achase79 on 2011-10-14
the graphics drivers is one of the first problems you should check.  Also you could do a little better by going for something a little leaner like Xubuntu.

To check your graphics driver you should hit alt-f2 and type in jockey-gtk and see if your graphics is listed.  Enable it (requires internet connection) and then restart.  If nothing to enable you will have to use a terminal command to list your hardware.

alt-f2 then type gnome-terminal gets you into the terminal.  then type lspci then press enter this will give a listing of hardware.  look for anything that says ati, nvidia or graphics.  You can post that information here to get a more detailed plan.

---

### Post by snowpine on 2011-10-14
Welcome to the forums Druski!

It is normal for Ubuntu to be a little slower than XP, especially on older hardware like yours. (XP was released almost 10 years ago, when desktop computers were much less powerful.)

You can try a lightweight desktop environment like LXDE or Xfce; these can be installed through your Software Center and then selected from the login screen.

Frankly though, if performance is as bad as you say, that points to some kind of problem, which is good because problems can be solved. 

One possible culprit is your video card; if you don't have the correct drivers installed, then certain tasks (like rendering web pages for example) will be very, very slow. Try going to the Restricted Hardware Drivers application (jockey-gtk) to see if anything is available. If you need help figuring out which video card you have, you can open a Terminal and:

```
lspci | grep VGA
```

This will display information about your video chipset, you can then use the forum Search feature to look for answers.

Of course, video drivers is just an educated guess. There are many possible explanations for why Ubuntu is running slowly on your computer. I suggest using the System Monitor application (or the terminal command 'top') to see which applications/processes are bogging down your CPU.

---

### Post by Jacobonbuntu on 2011-10-14
> **aeiah said:**
> apparently ubuntu 11.10 is even more demanding than previous versions. you might want to consider trying out a lighter version on that hardware unless you really want the unity desktop stuff.

xubuntu should run fine, lubuntu will be even lighter but you may feel its a bit too bare


Just a guess, but I believe it might be the video performance. I run 11:10 on a stone-age asus motherboard (8 or 9 yers old) but I don't use the onboard videocard anymore. It really runs pretty fast! faster than it did on XP (its original OS)

---

### Post by Druski on 2011-10-14
> **achase79 said:**
> the graphics drivers is one of the first problems you should check.  Also you could do a little better by going for something a little leaner like Xubuntu.

To check your graphics driver you should hit alt-f2 and type in jockey-gtk and see if your graphics is listed.  Enable it (requires internet connection) and then restart.  If nothing to enable you will have to use a terminal command to list your hardware.

alt-f2 then type gnome-terminal gets you into the terminal.  then type lspci then press enter this will give a listing of hardware.  look for anything that says ati, nvidia or graphics.  You can post that information here to get a more detailed plan.


Thanks for the speedy replies...  got the videocard info..

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

I did a search for that card - and found a a bit of info... however the drivers are a royal pain to try and install :(   

Perhaps I should look at xubuntu for this machine. :confused:

---

### Post by collisionystm on 2011-10-14
> **Druski said:**
> Well - I had just upgraded my Wife's computer, and this left me with a spare machine that I figured... why not dabble a bit with Linux, after all it don't need as much machine as windows... and perhaps I got a bit of life left in this machine etc..

Oh - and I am Linux challenged - so bare with me...

Ok - I installed Ubunto 11.10 32 bit from the Burned ISO CD I made. the install went pretty well, I used all defaults. I did have a problem with GRUB2 failing to install during the installation... and followed the instructions on the Ubuntu Wiki for re-installing (chroot method etc..) - seemed to work fine and Ubunto boots fine now.

Anyway this computer runs Windows XP fairly well, it came with XP... and it is not to slow or anything (until you start adding all the service packs and millions of emails etc...) HOWEVER with the fresh default install of Ubuntu this thing crawls along, disk thrashes a lot, and is graphically "chunky" etc... with the simpliest application like Firefox on a reasonably static non graphically challenging webpage - it is downright slow.

the System I am using is;

Dell Dimension 2350 computer
Intel P4 Processor 1.80 GHz
1 Gig of RAM
120 Gig ATA 133 Hard Drive
Standard IDE CD BURNER (no DVD)

I am using the standard onboard video (which at the moment I do not remember what it is)

is Ubunto 11.10 requirements for a smooth operating enviroment more than that PC?

good effort... but in this case I would say XP is the winner for the faster OS.

Linux is not always the best choice. Alot of time windows is just slow from age and just needs a re-install to get back up to speed. Hard drives also slow down as they age and create a 'slowness' in your operation of the os. I also suggest blowign the dust out of the computer case to increase the speed a little.

If you have your heart set on linux, try something lighter like xubuntu. You just wont have all the bells and whistles that you see on ubuntu.com ...

---

### Post by snowpine on 2011-10-14
> **Druski said:**
> Thanks for the speedy replies...  got the videocard info..

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

I did a search for that card - and found a a bit of info... however the drivers are a royal pain to try and install :(   

Perhaps I should look at xubuntu for this machine. :confused:

I am not familiar with that specific graphics card, but it's good that you found some how-to's.

Xubuntu is simply Ubuntu with the Xfce desktop environment. You can install Xfce through your Software Center and give it a try. It will not solve your graphics problem, but because Xfce has less "eye candy" than Unity, you might not mind the lag as much.

---

### Post by Druski on 2011-10-14
Well - I just wiped the Ubuntu install and went with the latest Xubuntu and WOW - what a difference! It's like Night and Day! 
 
Xubuntu is running like a dream... fast, no lagging, fast boot... Firefox loads pages mighty quickly... very nice!
 
Thanks all forthe suggustions etc.. :p

---


---
title: "Instant Shutdown initiated"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by grtwhiterhyno on 2008-08-04
I have NO idea what is going on.  I was browsing around, not changing things, just looking to get familiar with my brand spanking new OS <Ubuntu 8.04 Hardy Heron> <first time user> .  I found the screen saver utility and was going down the menu checking them out, yet when I got to what I believe is called flashlight or something, the screen locks very briefly, goes black, then screens worth of nice color bars, pixels and static.  It then shuts down.  Yay :(  So I turn it back on and think "Well I guess I cant do that one for some reason but I want to see the rest"  Start up the screen saver utility and whattaya know, blasted thing shuts down again.  :confused:  What the h e double crapola!  Please help out an absolute moron.
I have done a few updates, struggling with flash.  I'm on a very VERY old E machine with an onboard video/sound card.

---

### Post by Linux_Man on 2008-08-05
That has happened to me once when I was looking at screen savers on my EEE. I think it could be due to a few things A) An underpowered graphics card (I doubt it because on my EEE at least, it runs better than my old Dell which has an older card and runs screensavers fine) or B) Not including any swap. 

Basically, what I think has happened was X got overloaded and caused it to crash somehow, though I don't know how it would take the entire system with it. So did you enable swap?

---

### Post by grtwhiterhyno on 2008-08-05
I dont know what that is, so I'm going to go with no.  <total noob>

---

### Post by hotrod6657 on 2008-08-05
Swap acts sort of like Window's virtual memory.  It's a separate partition that Ubuntu calls upon when it needs.  It's not essential, but most people use it just because it's only about a gig of space and worth it if it saves you from issues.

I don't know how you can enable or setup your swap if you didn't originally, but i can tell you how to check.

In the terminal (go to applications, accessories, terminal) and type:  ```
sudo fdisk -l
```

It will ask for your root password, enter that and it will display your harddrive's partition table.

If one of the entries says Linux Swap then you do in fact have swap.

---

### Post by grtwhiterhyno on 2008-08-05
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           4       32098+  de  Dell Utility
/dev/sda2               5        2434    19518975    5  Extended
/dev/sda5               5        2341    18771921   83  Linux
/dev/sda6            2342        2434      746991   82  Linux swap / Solaris

This was the return.  Could you tell me exactly how to read it please?  Does that equate to like 750 megs of swap <virtual> memory?

---

### Post by hotrod6657 on 2008-08-05
> **grtwhiterhyno said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           4       32098+  de  Dell Utility
/dev/sda2               5        2434    19518975    5  Extended
/dev/sda5               5        2341    18771921   83  Linux
/dev/sda6            2342        2434      746991   82  Linux swap / Solaris

This was the return.  Could you tell me exactly how to read it please?

Okay, i'm no expert but i'll give it a shot.

This is basically a list of all the partitions on your computer.

You seem to have 4.  The first one, the Dell Utility should be your computer's recovery partition.  It's what they do now instead of giving you CD's with your operating system on it.  The second one "extended" I'm not sure about.  The last two are the ones that pertain to Linux.  There's the one that's is says just Linux, which is your actual Ubuntu OS, and the other which is your swap partition.  

(I think your Extended is just saying that your linux is installed on an extended partition)

The numbers refer to the size of the partitions.  There has to be a better explanation of this somewhere.  I'm not a big partitioning buff.

The important thing is that you do in fact have a Swap partition.  I'll have to let some more experienced members help you figure out if increasing it's size would help matters or not.  I usually make my swap partitions about a gigabyte in size.

---

### Post by grtwhiterhyno on 2008-08-05
Well despite not yet knowing the problem, thanks for showing me more about my new and increasingly complicated OS

---

### Post by grtwhiterhyno on 2008-08-05
bump bitty bump

---

### Post by grtwhiterhyno on 2008-08-05
anyone?

---


---
title: "Error after 12.04 install/update: &quot;Kernel panic - not syncing: VFS: Unable to mount&quot;"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by Abras on 2012-05-19
Hello everyone,

A frustrated perennial newb here. After installing 12.04 on a section of my hard drive, it seemed to work. I was able to get into the OS (without the GRUB screen coming up) and I installed all the updates and the nvidia drivers.

But when I restarted it, I got a black screen with "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown lock (0, 0)

blah blah blah...

I'd write the rest but my laptop's dying. The posts I found on other sites were completely unhelpful. Like I said, I'm a beginner, so I need it explained to me, step by step.

Argh! This is frustrating. Things always seem to break when I upgrade...

Thanks for your help, in advance.

---

### Post by gordintoronto on 2012-05-19
What is your video card? There appears to be a set of Nvidia cards which behave very badly with the 295.40 driver, which I am using.

Holding the shift key after turning on your computer, should get you a Grub menu. You can go into the command-line verson of Ubuntu and remove the driver, but I don't know the details off the top of my head. I have also read that newer, working, drivers can be installed if you have the appropriate incantations. Google is your friend.

---

### Post by Abras on 2012-05-20
You were on the right track, Gord. The long and the short of it is: I uninstalled the nvidia drivers and everything's working again.

I love the new features, especially Unity (It's been a long time since I've upgraded to the latest version...) I just hope it keeps on working!

Thanks for your reply!

PS Could someone remind me how to mark this thread as "Solved"? Thanks

---

### Post by Lisiano on 2012-05-20
The thread tools, or press this link [http://ubuntuforums.org/solved.php?do=marksolved&t=1983072](http://ubuntuforums.org/solved.php?do=marksolved&t=1983072)

---

### Post by gordintoronto on 2012-05-20
If you have installed Synaptic Package Manager, you could keep an eye on "nvidia-current." If it turns into 295.49 or 295.53, you could give it another try.

---


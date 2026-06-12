---
title: "Swap partition"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by ArheoTip on 2011-10-24
Hy,

I'm completely new to Linux, but I've decided to get away from Windows. So I choose Ubuntu and installed it a couple of minutes ago. As a noob, I've choose automatic installation and ended up with a 1 gb swap partition. 
I was wondering if there is any possibility to 'recreate' swap partition, giving it 1gb from the main partition? Without formating the main partition, of course.

Tnx a lot,

D.

---

### Post by nothingspecial on 2011-10-24
Is there a problem having a swap partition?

To answer your question, you can delete your swap partition and create a swap file, but I'm not sure if you actually want to be doing that.

---

### Post by ArheoTip on 2011-10-24
Sorry, I wasn't clear enough...

I want to give it one more gb, to have 2 gb swap.
Can I do ih with GParted without formating the whole drive.I have two partitions - one main and one swap.
If it can't be done, ok. I probably should make at least one more partition for some of the data.

---

### Post by nothingspecial on 2011-10-24
You would need to do it from a live cd.

Just shrink your / partition by 1gig and make a 2 gig swap partition using the existing one and the free space.

Bear in mind that the swap partition may be inside a container.

Also make a backup of your data before messing about with partition editors.

---

### Post by ArheoTip on 2011-10-24
Here it goes....

I'll let you know how it went!

Tnx

---

### Post by nothingspecial on 2011-10-24
You may also need to correct your /etc/fstab

But maybe not. We'll get to that if we need to.

---

### Post by ajgreeny on 2011-10-24
If you only installed a couple of minutes ago, now one hour and a couple of minutes it may even be worth reinstalling following the information at [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")  I think this will do exactly what you are asking about, and may be quicker in the long run.

This will mean that you set up partitions manually during the installation and will be able to set up a root, / partition, a /home partition and a swap partition, all of the sizes you want and prefer.

I would suggest:-
/ (root) = 10 - 20GB.
swap = 2 - 4 GB.
/home = the rest of available space.

---

### Post by F.G. on 2011-10-24
if you resize/move your swap partition you will probably need to reset the memory reference you root partition uses for the swap (basically tell it that there is a change).
here's a thread that tells you how to do that:

[http://ubuntuforums.org/showthread.php?t=1811742](http://ubuntuforums.org/showthread.php?t=1811742)

also, if you run the command 'top' from a terminal it should tell you what you swap usage is / if it is being used.

if you don't do this, you may find that your computer is running fine, it;s just not using the swap partition.
good luck.

---


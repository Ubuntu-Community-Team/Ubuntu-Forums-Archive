---
title: "Resize Partition - Make Windows Smaller Help"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Devi 710 on 2008-10-31
Hi,

I dual boot with Ubuntu 7.10 and Win XP and I want to make the XP partition smaller because I never really use it. 

Just so I am clear and don't make any mistakes from what I've read on here, I should just:

1.)Back up all my important data
2.)Defrag my Windows partition (maybe several times)
3.)Boot up with a Live CD, run Gparted, and choose to resize my windows partition which will give more room to my Ubuntu partition

Does all this sound correct? Am I missing anything?



(I've attached a photo with gparted open)

---

### Post by drs305 on 2008-10-31
Yes, what you have outlined will work. Just remember you will have to expand the linux partition from the livecd, gparted cd, sytemrescuecd or something similar and not from within ubuntu.

And just to be sure, you should back up your linux data as well as windows data since the linux data will definitely be moved, whereas the windows data may actually remain untouched.

---

### Post by Devi 710 on 2008-10-31
OK, so say I make the Windows partition 75GB smaller, I also need to increase the Linux partition by 75GB?

And will the Ubuntu 8.10 Live CD work (I noticed the option to resize was available from gparted in a live session) or should I download a Gparted Live disk?

---

### Post by Teabicky on 2008-10-31
I installed Ubuntu (Hardy) from within windows and when I look on Gparted there is no partition.  Is there anyway to separate Ubuntu from windows or do I have to re-install from scratch?

---

### Post by reg4c on 2008-10-31
Perhaps a bit offtopic but, 

I installed Ibex and did not make a swap partition. Do I have to reinstall or can I make a partition now that would serve as swap, and how would I do it?

Cheers
PS: Alright a lot offtopic.

---

### Post by Devi 710 on 2008-10-31
reg4c:

I would suggest starting your own topic and someone might be able to help you. I thought a swap partition was required so I wouldn't know how to set one up post install.

Teabicky:

I am not too sure what you mean by "separate Ubuntu from windows" They can't exist on the same partition (unless you use virtualization like VMware). You should look at the "Wubi" section as that is the method you used to install. I boot from the live CD and install it from there.

Anything else I should worry about before I take the plunge?

---

### Post by reg4c on 2008-10-31
Naah, its not mandatory, especially since I have plenty of RAM
Thanks though

Cheers

---

### Post by supwest on 2008-10-31
@Teabicky

You can separate Ubuntu from Windows, here is the thread that explains how to do it.

[http://ubuntuforums.org/showthread.php?t=438591&highlight=lvpm]("http://ubuntuforums.org/showthread.php?t=438591&highlight=lvpm")

I recently did something similar from a Wubi install like you have. I did have some trouble installing the partition manager software from the link in the post (I think it's outdated). So I got it from the Parted Magic site and followed their instructions

Partedmagic site:
[http://partedmagic.com/wiki/PartedMagic.php]("http://partedmagic.com/wiki/PartedMagic.php")

Sorry to hijack your thread Devi :)

---

### Post by Devi 710 on 2008-11-01
haha

Yeah it's kind of gone off in another direction.:-? No biggy. People are still getting help, so that is good.

---

### Post by Teabicky on 2008-11-01
Oops sorry, should have started my own thread, got carried away with my own issues.  It's kind or relevant though.

---

### Post by dazzlindonna on 2008-11-01
devi, yes, once you make the win. partition smaller, you'll need to expand the linux one to use that new space.  keep in mind that it may take hours for that part to happen as it moves stuff around.

---


---
title: "Problem with drive names"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Hoelmkjaer on 2008-10-10
Hello.
Just for the record - I'm new here :) 
So... Hi everyone

To the point: 
I have two internal hard drives. I had Windows XP on one, and Vista on the other one, but since I only really used Vista, I decided to format the XP drive and use it for general storage instead. 
I didn't think things through, so before I knew it, the windows boot manager was gone. Good job, I know.
Anyways - I saw this as a good opportunity to install Ubuntu instead and use Grub. Problem is, I can't figure out how to add Vista to Grub :(
I found a few guides and they're easy to understand 'n all, but it doesn't work. It shows up in Grub, but it just goes to the "starting up" message then halts. I know absolutely nothing about it, but I think it may be the root command that's messed up, since I'm far from sure what to call it and can't seem to figure it out. When I run sudo fdisk -l all I can see is that it's called sdb2... What would that be in (hd*,*) ? 

Thanks

---

### Post by SunnyRabbiera on 2008-10-10
actually you may want to give super grub disk a shot, as sometimes the Grub for ubuntu doesnt do its job correctly.
Now for your vista drive, did you defrag it before installing ubuntu?

---

### Post by Hoelmkjaer on 2008-10-10
Ubuntu works fine. I installed it on the XP drive that was wiped. Unfortunately the boot manager was on the XP drive, so it was deleted, too, which is why I installed Ubuntu + grub. Now I just can't add the right hard drive (the vista drive) to grub so that I can dual boot the two.

---

### Post by SunnyRabbiera on 2008-10-10
Hmm are you sure you have a dual boot set up or did you by mistake erase vista?
How much space is your ubuntu partition taking?

---

### Post by Hoelmkjaer on 2008-10-10
I'm sorry but I think you misunderstood something... I'm pretty confused myself, so no hard feelings. 

I have 2 hard drives. One has got Ubuntu installed and the other one got Vista. Each drive is 160gb. 

I need to know how to make a boot entry for the Vista drive so that I can choose it from the Grub menu. 

I'm using [this]("http://www.pronetworks.org/forum/about78184.html") guide to do that, but I don't know what I should enter in the (hd*,*) or (sd*,*) place. When I run sudo fdisk -l it tells me the drive is called sdb2... Does that translate into (sdb2,0) or...? 

I'm not into the idea of experimenting anymore, since so far it's only made things worse.

---


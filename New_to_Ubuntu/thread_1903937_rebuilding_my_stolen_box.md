---
title: "rebuilding my stolen box"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by turguz on 2012-01-03
I had a house break-in and my Ubuntu desktop was stolen among other things.  All I'm left with is the clone of the original hard drive.  
Which components would I have to match exactly in order to rebuild the desktop to a working condition?  The hard drive is the exact same model as the original.

thanks

---

### Post by fdrake on 2012-01-03
> **turguz said:**
> I had a house break-in and my Ubuntu desktop was stolen among other things.  All I'm left with is the clone of the original hard drive.  
Which components would I have to match exactly in order to rebuild the desktop to a working condition?  The hard drive is the exact same model as the original.

thanks
you can  put the hdd in any computer , the kernel should take care of the rest. Of course you have to make sure it is in master position.

---

### Post by 1clue on 2012-01-03
If you had a 64-bit installation before then you MUST have a 64-bit system now.  Presumably you're using Intel.  If you had a Mac before and don't get another Mac, or vice versa, you might have some hoops to jump through.

Your graphics card drivers, if you installed them after the fact, will need to be re-installed if you don't go with the same graphics chip family (nVidia, ATI, etc) and maybe age of driver.  This is not critical, chances are whatever card you have will work with the Open Source drivers included with Ubuntu.

You will probably have to reconfigure a few things, but it's not likely to be a big pain.

---

### Post by 1clue on 2012-01-03
That said, if you change processor family dramatically you might run into issues too.  I'm not sure what Ubuntu does under the covers, but most distros I've used recently can be tuned to specific hardware.

I'm under the impression Ubuntu does not do that by default.

Also, the amount of SWAP is generally calculated based on the amount of RAM during installation.  If you dramatically change the RAM then there might be issues, but not likely.  If you jump your RAM up a bunch then chances are you won't be using swap as much.

---

### Post by turguz on 2012-01-03
I was planning on getting the same processor i7-2600k and the same amount of ram (16GB) I just cant find the same model mobo anymore. And maybe beef up the video card. (Thank you renters insurance)

---

### Post by 1clue on 2012-01-03
Are you using a virtualization technology like VMware or KVM?  If so, then there may be motherboard considerations such as a wonky bios.  Make sure that's at least as compatible as your previous one.

If not using virtualization, what the heck are you using that thing for?

---

### Post by turguz on 2012-01-03
I'm using VirtualBox as that is what is required by my employer.

---

### Post by Rasa1111 on 2012-01-03
Damn, I feel for you man.
Had similar things happen to me in the past.
Sucky, sucky feeling. 

Did the scumbag who did it ever get caught?

Good luck man. <3

---

### Post by turguz on 2012-01-03
The scumbag is still free...

---

### Post by 1clue on 2012-01-03
This might offer some inspiration:

[http://www.youtube.com/watch?v=U4oB28ksiIo](http://www.youtube.com/watch?v=U4oB28ksiIo)

It is certainly relevant if you have a few minutes to spare, and I find it extremely funny.

---

### Post by Rasa1111 on 2012-01-03
> **turguz said:**
> The scumbag is still free...

Dang.

Karma will take care of it. ;)

---


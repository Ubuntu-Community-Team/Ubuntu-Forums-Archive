---
title: "Server Kernal... don't remember doing that..."
date: 2008-10-21
forum: New to Ubuntu
---

### Post by conway.federico on 2008-10-21
I seem to be running the server kernel on my laptop.. (.21) ... is there any way to fix this to generic or rt?  Might it be behind Nvidia compiz / screensaver problems?

---

### Post by stephanvaningen on 2008-10-21
I read in other posts that you created that you have more than one problem, also you installed the 64-bit version of the OS?

I would therefor suggest to re-install and take the 32-bit desktop edition. Since I read that you tell us you're quite new to Ubuntu, the 32-bit version is far more easier for newcomers (for me too, and I'm using it for a few years now): 64-bit has sometimes issues with plugins for firefox too, because they require to be available as 64-bit compiled too...

Re-installing from scratch with 32-bit-desktop to start with could give you a better start-point I assume.

---

### Post by conway.federico on 2008-10-21
yeah I really wanted to take advantage of my AMD Turion 64, but as I've been reading, the difference between 32 and 64 seems to be pretty subjective... So far I haven't had many problems outside of the video card stuff, and that was figured out for a while... I just got ambitious and tried to install the latest Nvidia drivers and have had woes ever since... I can't even get back to my previous settings, but for a while compiz and my sound were working great... 

But if a total re-install would be the best way to fix the Server Kernel problem then I'll consider it...  I'll have to read more about 64 vs 32.  Does anybody recommend some sort of definitive ruling on bit architecture?  I do have processes (I use my laptop primarily for audio recording and graphic website design) that might benefit from more processor power... In what I have read,I haven't noticed any opinions willing to take a stance...

---

### Post by stephanvaningen on 2008-10-21
I don't want to consider myself as 'a big specialist' on processor technology, but I think the 'PC world' is just not yet ready enough to run on more than 32 bit OS.

If you would go to [PowerPC]("http://en.wikipedia.org/wiki/POWER4") and specialised OS-es for that (like [i5/OS]("http://en.wikipedia.org/wiki/IBM_i") ([IBM i]("http://en.wikipedia.org/wiki/IBM_i"))), than you can take full advantage of the 64-bit, but a *lot* of code in the 'house-hold'-computing is just not yet ready for it.

What it could be used for I think is a 64-bit processor-server with a hypervisor (like Xen on Ubuntu-server) and then running a few 32-bit guests on it, which run 'end-user applications', where the Dom0 (Hypervisor) takes full advantage of 64 for managing the DumUs...

---

### Post by conway.federico on 2008-10-30
Wow... I am so in over my head... this is how we learn no?  Next install ill consider 32 bit, for the time being I seem to find enough 64 bit tutorials for what I need. Thanks man.  Though maybe thats whats causing my sudden wicd problems.....

---


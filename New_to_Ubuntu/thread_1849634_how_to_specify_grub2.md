---
title: "how to specify grub2"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by pkthunder7 on 2011-09-24
hello,

I have a CD of ubuntu 11.04 64-bit and am about to install it onto a drive that shares a partition with OSX86.  I want to install grub2 into my root folder and not the MBR so that it won't interfere with chameleon.  Can I do this form the CD I made, or do I need to do a more custom install somehow?

Thanks!!  I am really excited to start using linux!

Paul

---

### Post by bodhi.zazen on 2011-09-24
At the step where you install grub, select the advanced options, and install it into your boot (normally the same as / or root) partition.

[img]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step6.png[/img]

---

### Post by alegomaster on 2011-09-24
> **pkthunder7 said:**
> hello,

I have a CD of ubuntu 11.04 64-bit and am about to install it onto a drive that shares a partition with OSX86.  I want to install grub2 into my root folder and not the MBR so that it won't interfere with chameleon.  Can I do this form the CD I made, or do I need to do a more custom install somehow?

Thanks!!  I am really excited to start using linux!

Paul

By OSX86 you mean Mac OSX on a regular non-apple hardware, Is that correct? 

In this case the CD will by default overwrite the MBR. I am not sure how to change that, or if it will even work the way you want it, but I recommend using virtual box instead. You won't have to worry about any of this boot loader setup and you can still use it to run linux.

Of course this setup tends to be slower than using it non-virtualized, but it is worth a shot to try. This will be better if your hardware specs are good, so can you please tell me your specs so I can figure out if it will be fast in virtual box.

---

### Post by pkthunder7 on 2011-09-24
Thanks alego, I am going to first go with what bodhi told me about how to place it.  If it doesn't work, then I will try the virtual box.  I am running a system right now with a quad core intel chipset, 8GB RAM, and a EVGA GeForce 512MB DDR3 graphics card.  So it reasonably speedy.  Though I'd rather not run things through virtual box if I can avoid it.

---

### Post by alegomaster on 2011-09-24
> **pkthunder7 said:**
> Thanks alego, I am going to first go with what bodhi told me about how to place it.  If it doesn't work, then I will try the virtual box.  I am running a system right now with a quad core intel chipset, 8GB RAM, and a EVGA GeForce 512MB DDR3 graphics card.  So it reasonably speedy.  Though I'd rather not run things through virtual box if I can avoid it.

That should be fast enough for virtualbox to run smoothly. However if you do run it, make sure virtualization is enabled in the BIO's (If you have it, I don't care about OSX86 so I have no clue if you have BIOs) or else virtual box is going to be slow.

Have fun with Linux! It has rough patches, but It is my favorite OS. Especially after all of this BS that Apple and Microsoft are doing with their software and OS's

---

### Post by pkthunder7 on 2011-09-28
Thanks, you two.  I successfully installed ubuntu  11.04 - 64-bit onto the other partition of my HDD that shares osx, without the use of virtual box!  I  had to make a 16GB swap area also, which I didn't do the first time, but  I just reinstalled and did it over again.  Thanks again.

---


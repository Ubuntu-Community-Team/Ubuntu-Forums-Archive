---
title: "Could I maybe come to Hardy from SLED?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by LewisR on 2008-04-26
Hi everyone,

As you may know from my previous post, I am an "absolute beginner" and you guys and gals have been awesome and helpful.

I've been dabbling with Novell SuSE because I wanted to jump in with something very stable and commercially-supported. While I have been impressed with the system (particularly KDE - yummy!) I have grown increasingly frustrated by my inability to get Desktop Effects working. (I successfully installed the proprietary ATI drivers for my Radeon X1300 - no small task - and glxgears looks great  - but Desktop Effects is a non-starter.) Judging from my research, this is a common problem that goes far back and has few, if any, easy solutions.

Moreover, I continue to be impressed by the amazing community support around Ubuntu, whereas much of what I've found online seems to focus on openSUSE versus SLED (which is not to say that Novell's support hasn't been great; it has.)

So I am afraid I have yet more newbie questions for you:

1) I am currently dual-booting into SLED and Vista via GRUB. Works really well. If I were to install Ubuntu, would it recognize SLED and Windows already being there and add itself as an option? Where would it pull partition space from? 

Note that I'd NOT like to uninstall SLED if at all possible because, well, I paid for it, and because I want to keep learning on it too.

2) Has there been success (generally speaking) with enabling desktop effects using the genuine ATI drivers with Ubuntu?

3) Any other pitfalls of which I should be aware?

To the extent that it is helpful, my main goal for installing a Linux distribution is to brush up on  my UNIX skills. I work on the business side of things in the Internet space, and I've always found that I can do a better job if I understand the underlying technology.

Thank you!!

---

### Post by mister_pink on 2008-04-26
1) I have a feeling that ubuntu will overwrite the SLED bootloader, _but_ will put in opions for all three when it does so. At least this is what I've found usually - I have win xp, ubuntu and a currently empty partion that I use for installing random linux distros to try out, and it always seems to sort itself out.

2) I'm doing it at the moment :) It can be a real pain, but there's lots of guides about, and if you google around, especially on this forum (add site:ubuntuforums.org to the search) you should be able to get it going!

3) Its difficult to say - if you look at the forums at the moment you'll see there's lots of unhappy people having issues, but for every one of them theres dozens of others that are having no trouble at all. The best thing to do is download the iso, burn it and try out the liveCD. This will give you a pretty good idea of if all your hardware is going to behave itself.

---

### Post by LewisR on 2008-04-26
Thank you for taking the time to reply. If I may just beg your indulgence once more, if I were to install Hardy as a third partition, where would the space come from? When I installed SLED, it came from me shrinking the volume in the Vista tools, the remainder of which SLED grabbed. How/where would I partition even more space?

Thank you once again!

---

### Post by mister_pink on 2008-04-26
I guess this depends on where you have the most free space available. Vista wont be able to resize the SLED partition. I'd do it from the liveCD, and I would say take a bit from both but this could involve moving an awful lot of data about, which is a risky operation. I'd start by loading up the liveCD, click system -> Administration -> Partition Editor. This will let you look at your partitions and see where you've got space, then make the changes. I'd try not to move too much stuff about as it takes forever and can corrupt data - so anything really important I'd back up too!

Edit: I should add, with a complicated set up like this, I'd select the manual partitioning in the installer to make sure things go right. You just have to select the space you've already made for ubuntu (as above) and tell it to mount as "/".

---


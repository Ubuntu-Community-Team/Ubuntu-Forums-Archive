---
title: "To slow to handle"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Toegang on 2008-06-26
Hi

The xubuntu drive became to small. So I made a live cd  of GParted, took some space from my \home partition, moved the swap partition into the empty space and finaly enlarged the xubuntu partition.

So far so good

Next day Xubuntu did a normal start up, but then almost immediately with no warning at all it turned to slow to handle. Only way out was a hard reset.

After each hard reset, it seems like it waits until an other application is started and there it stops again.

What could it be (since there are no viruses in the Linux world). How to resolve it????

Please help me,
Toegang

---

### Post by Inxsible on 2008-06-26
That happened to me as well. But for me the culprit was update manager. everytime I started update manager, i could do nothing but hard reset.

Anyway, I have never found a solution to it. I moved to Debian soon after I had that issue with Xubuntu.

Sorry, couldn't be of more help.

---

### Post by collinp on 2008-06-26
Have the xfce task manager open, then open something you know causes the lag. If you see anything eating a ton of cpu power, that is your problem. Also, if you don't have the Xfce task manager installed, it is in the repos.

---

### Post by Hospadar on 2008-06-26
you can also (hopefully) go to text mode (Ctrl-Alt-F1) and use the "top" or "htop" (if you like pretty colors) command to monitor perfomance and resource usage of different proccesses.  To get back to xfce, you can Ctrl-Alt-F7.  I would see if you can get into text mode after the slowdown starts, and if not, if the slowdown will happen once you have already switched to text mode (by monitoring top or htop)

---

### Post by Toegang on 2008-06-28
Hi,

I did enter into text-mode just before the slowdown. But no extensive cpu use was visible, just a splitsecond 98% for 'console kit dae' For the rest the biggest consumer was 'apt-check' with less than 10%. Instead of cpu could it be something with the memory?

Now I tried just to wait until the update warning showed up. Started it, the udate window did show up but did not continue . . . .

---

### Post by Toegang on 2008-06-28
Would it be an option to download a xubuntu iso and do a (re-)installation of Hardy Heron? What would I lose?

\home is mounted on a separate partition.

---

### Post by lazyart on 2008-06-28
With \home seperate, all you would lose is installed software.  Once you reinstalled that software you would be back to the way you were.

---

### Post by Inxsible on 2008-06-28
I would also recommend that you try installing Debian with either the core (business card iso) or use the Debian-xfce. Its much faster than Ubuntu, IMO

---

### Post by Toegang on 2008-06-28
It looks like I resolved the problem. Almost to ashamed to say. I did a startup in the recovery mode, tried a update. After two times I succeeded!
Now it looks ok, I'm writing in Xubuntu mode again!

@Inxsible
I've got a PIII, 800MHz, 256Mb Less than the minimum requirements I found for Debian. Later on when I'm in the possession of a more up to date pc, I'll try anyway.

@hospadar
Thanks for the textmode option, that one was new to me.

---

### Post by Inxsible on 2008-06-28
> **Toegang said:**
> ...[snip]@Inxsible
I've got a PIII, 800MHz, 256Mb Less than the minimum requirements I found for Debian. Later on when I'm in the possession of a more up to date pc, I'll try anyway.....[snip]
That will run a Debian core + Xfce just fine. Of course some other Window manager like Fluxbox will run even faster. The requirements that you read for Debian might have been for the Gnome or the KDE desktop.


I run Debian core + Xfce4 on my PIII, 1.13 GHz, 256MB RAM. and it runs like a charm.

---

### Post by Toegang on 2008-06-29
Unfortunately the happiness  didn't last long, one day. Although it is less extreme and I found a super trick on an other post Alt + SysRq + R E I S U B. It looks like there's nothing happening, but you're shutting down the system step by step. Now you can force a proper reboot without having the chance of damaging the system.

So my quest still stands. Perhaps if everything else fails I'll have to  fall back on Inxsible his advise.

@Inxsible
1. Just out of curiosity: Why are you on this forum if you're not an Ubuntu user anymore?
2. Why would one want to hop over to Debian instead of Ubuntu, they both offer xfce & fluxbox. Convince me :)
3. What about the apps & help for Debian you can get on the internet?

---

### Post by Inxsible on 2008-06-29
> **Toegang said:**
> ...[snip]
So my quest still stands. Perhaps if everything else fails I'll have to  fall back on Inxsible his advise.

@Inxsible
1. Just out of curiosity: Why are you on this forum if you're not an Ubuntu user anymore?
2. Why would one want to hop over to Debian instead of Ubuntu, they both offer xfce & fluxbox. Convince me :)
3. What about the apps & help for Debian you can get on the internet?
1) I started out with Ubuntu as my first distro. And I love the forums here. So I am still here. Also, Ubuntu is based on Debian, so I am not very far off.
2) Use Debian once and you will see why. Its not just about offering xfce and fluxbox. Those are offered by EVERY linux distro. You can install those window managers/desktop environments on any distro. Debian, IMO is much more stable than Ubuntu. There are a few things that you would have to do manually, like installing video drivers. But if you can do that, you will find that Debian is much faster and works on older machines where even Xubuntu stutters.
3) There is a Debian sub forum on ubuntu forums itself. Lots of good help there. There is also the official debian forums which offers pretty good help although not as fast as here.

---

### Post by Toegang on 2008-06-29
I'm really impressed by the response time of this forum!

> . . . There are a few things that you would have to do manually, like installing video drivers. But if you can do that, you will find that Debian . . .


The Debian apps, are they not that wide spread as the Ubuntu ones (at least those with GUI)? Can one use the apps of Ubuntu?

One of the reasons I chose for the Ubuntu family was its relative simplicity and the vast community. Although the Debian seems to be a bit harder and the community smaller I think I'll give it a try.
I'll let you know when I tried it out.

---

### Post by Inxsible on 2008-06-29
> **Toegang said:**
> I'm really impressed by the response time of this forum!



The Debian apps, are they not that wide spread as the Ubuntu ones (at least those with GUI)? Can one use the apps of Ubuntu?

One of the reasons I chose for the Ubuntu family was its relative simplicity and the vast community. Although the Debian seems to be a bit harder and the community smaller I think I'll give it a try.
I'll let you know when I tried it out.Good Luck. I am sure you won't regret it. And the Debian community is not smaller....just widespread. and they are not as active on the forums - giving you an impression that the community is small.

---

### Post by Toegang on 2008-07-01
> Originally Posted by Inxsible
*Good Luck. I am sure you won't regret it.*

I did try,    and finally installed Debian + xfce.  At the end it couldn't convince me (yet). Perhaps after another meltdown and being more experienced, I'll try it again.

Thx anyway

---


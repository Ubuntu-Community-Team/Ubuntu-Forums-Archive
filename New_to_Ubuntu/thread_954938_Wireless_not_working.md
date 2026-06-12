---
title: "Wireless not working"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by cake1988 on 2008-10-21
Hi,
This is the 1st time I've posted on here, so here goes.
I got an Acer Aspire One with Linpus on it. I didn't like it. So I hitched up my external cd-rom to it and installed Ubuntu. Clean install, no problems. Then it came up with a message for restricted drivers for my on board wifi. Thought nothing of it  as all I wanted to do was install it and I'd think about drivers in the morning. Booted up next day and it said that the drivers were enabled but I couldn't find a way to connect it to the router, other than a cable. Then I tried going through the forums, started following some instructions and to cut a long story short, I messed up. Now the drivers are no longer shown in the Hardware Drivers bit and I'm stuck with using a cable. 

The card is a AR242x 802.11abg Wireless PCI Express Adapter.

I know by searching through the forums, other people are having problems with this card.

Any ideas?

Keep it simple as my linux experience is basic at best.

---

### Post by phidia on 2008-10-21
Take a look at the guide (download the text file from the 1st post) [here]("http://ubuntuforums.org/showthread.php?t=795984&highlight=AR242x+802.11abg").
That should get it going Atheros cards will work in Ubuntu.

---

### Post by cake1988 on 2008-10-23
Didnt work, I think I must be doing something wrong. I been at this for a while now and the file wont install. I'm positive i typed it in correctly. 

Sudo sh NVIDIA-Linux-x86-169.12-pkg1.run 

Just wont go past it. I had to reboot and now it wont even go into the command prompt.

It gets so far in loading then just stops.

Ne ideas?

---

### Post by Yoke &amp; Chung on 2008-10-23
Try this forum, there are many guides on installing Ubuntu on Acer Aspire One:

[http://www.aspireoneuser.com/forum/](http://www.aspireoneuser.com/forum/)

---

### Post by Yoke &amp; Chung on 2008-10-23
> **cake1988 said:**
> Didnt work, I think I must be doing something wrong. I been at this for a while now and the file wont install. I'm positive i typed it in correctly. 

Sudo sh NVIDIA-Linux-x86-169.12-pkg1.run 

Just wont go past it. I had to reboot and now it wont even go into the command prompt.

It gets so far in loading then just stops.

Ne ideas?

Are you installing this on Acer Aspire One? It is not using nVidia card.

If it is for another PC, use the driver from nVidia site only as a LAST resort. Ubuntu will detect you nVidia card and will prompt you on whether you want to use the nVdia driver automatically on your first boot. If not, go to "System" --> "Administration" --> "Hardware Drivers" to activate the nVidia driver.

---

### Post by prematurebaby on 2008-10-23
That's a tough one. The simple way to do this is to buy a repeater. But who pays for things anymore:). Or just find some random driver on the intratubes. Otherwise I'm stumped on how to fix it.

---


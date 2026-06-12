---
title: "[SOLVED] Upgrade from Gutsy to Hardy from CD"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Michael Dooley on 2008-04-29
How do I upgrade from Gutsy to Hardy using the Live CD? I have inserted the CD and Nautilus shows the contents of the CD but strangely I get no viable (or useable) options to upgrade when using either Synaptic or Upgrade Manager.

I'm sort of baffled at this. I figured that it would be obvious but it hasn't been.

Thanks for reading my request for help.

---

### Post by scragar on 2008-04-29
I think you can only run the distribution upgrade from the alternate CD, not the liveCD, although I could be incorrect about this, and your problem could be something else.

---

### Post by Cypher on 2008-04-29
**scragar** is correct, you will need the Alternate CD to do a distribution upgrade or use the Update Manager to do the upgrade. The Live CD will only re-install..

---

### Post by Michael Dooley on 2008-04-29
Thanks for the information. I couldn't find anything about this on the Ubuntu forums so I had to ask. 

My connection to the world wide wait is via modem so I imagine that I'll have to completely wipe out everything and install over my previous version or ask a friend to download the alternate CD iso and burn it for me.

Just as an afterthought, where did you folks find this information?

Thanks go to both of you for your patience and helpfulness.

---

### Post by Cypher on 2008-05-01
In my case, I was running Gutsy and when Hardy was released, I downloaded the LiveCD as a force of habit and quickly realized that it doesn't upgrade an existing OS. So I downloaded the Alternate CD and when I put that into the PC it came up with the "Do you want to upgrade" dialog..

Of course, it helps that I have a good connection and can download the CD's in about 15-20 mins to try it out..

---

### Post by SlappyPappy on 2008-05-01
> **Michael Dooley said:**
> Thanks for the information. I couldn't find anything about this on the Ubuntu forums so I had to ask. 

My connection to the world wide wait is via modem so I imagine that I'll have to completely wipe out everything and install over my previous version or ask a friend to download the alternate CD iso and burn it for me.


I'm on a dialup system as well but it is possible to download the CD, I downloaded the Gutsy LiveCD in Windows using an old program called NetVampire. The thing is great at picking up where you left off if you get disconnected. I think it took about two days for me to download Gutsy.

Good luck, BTW thanks for the thread because I'll be upgrading the same way you do, from a disk.  :)

---

### Post by bodhi.zazen on 2008-05-01
> **SlappyPappy said:**
> I'm on a dialup system as well but it is possible to download the CD, I downloaded the Gutsy LiveCD in Windows using an old program called NetVampire. The thing is great at picking up where you left off if you get disconnected. I think it took about two days for me to download Gutsy.

Good luck, BTW thanks for the thread because I'll be upgrading the same way you do, from a disk.  :)

If you are on dial up, you may want to consider the minimal CD :

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It is a 10 Mb (or less) download, boot it, it installs a minimal OS. You then boot and apt-get ubuntu-desktop (or stay light if you want).

The advantage ? It is all net install, so you do not DL a CD / DVD only to have to upgrade 100's of packages post install. Not a critical the first week after a release, but after a few months it will save you ...

---

### Post by nowshining on 2008-05-01
or you can order a FREE CD, shipit.ubuntu.com for ubuntu or shipit.kubuntu.com for kubuntu and go from there. also a programm called wget can resume downloads, the GUI for it is Gwget as wget should be installed by default.

---

### Post by phr0ze on 2008-05-01
> **Michael Dooley said:**
> Just as an afterthought, where did you folks find this information?
.

It's on the very bottom of the Hardy upgrade instructions here:
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---


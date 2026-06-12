---
title: "recomendation on a stable distro that doesnt require much hardware"
date: 2019-03-03
forum: New to Ubuntu
---

### Post by jay-c33 on 2019-03-03
i have an old pc with a petium 4 3.00GHz /1gb of ram 
i have tried xenailpup however i have never been able to fully install it without requiring the usb, full wipe/install sda1(internal hard drive) saved the session just to come back too my initial boot wont boot without the usb. 
so i gave up on puppy. i need to know if there is an older version of ubuntu like the live os cd distros that are supported?
i would like to have an updated browser to it. thanks in advance.

---

### Post by Autodave on 2019-03-03
Xubuntu or even lighter Lubuntu.  Xubuntu runs here on a lesser machine that what you have.

---

### Post by kc1di on 2019-03-03
I would second xubuntu or Lubuntu, they are both great on low end machines.

---

### Post by oldrocker99 on 2019-03-03
I also want to recommend Ubuntu MATE, which is also lightweight, but more (ahem) full-featured.

---

### Post by jay-c33 on 2019-03-03
thank you guys, i will be testing them. i appreciate it.have
good day now.

---

### Post by jay-c33 on 2019-03-03
I installed Xubuntu 18.04 LTS i386, nice distro. I realized this version requires a bit more hardware since it has a bit of lag to it; up to what version early version i should consider installing that are still supported?

---

### Post by oldrocker99 on 2019-03-03
You should always use the most recent LTS (Long-Term Support) release, which is 18.04. 

According to this link, [http://www.linuxandubuntu.com/home/5-lightweight-linux-desktop-environments](http://www.linuxandubuntu.com/home/5-lightweight-linux-desktop-environments), Lubuntu is even lighter-weight than Xubuntu or Ubuntu MATE. Give it a shot.

You can also just install it thus:```
sudo apt install lubuntu-qt-desktop
```
This will install the complete Lubuntu desktop. Log out, select the Lubuntu desktop and log back in, and you'll be using as lightweight a desktop as you can get.

And one of the many great things about Linux is that you can install different desktops.

---

### Post by mastablasta on 2019-03-04
> **jay-c33 said:**
> I installed Xubuntu 18.04 LTS i386, nice distro. I realized this version requires a bit more hardware since it has a bit of lag to it; up to what version early version i should consider installing that are still supported?

older won't make it faster. the issue could the the GPU chip or old hard disk. if this is not a laptop, then it might be possible to upgrade it with a used GPU card.


there are also other options such as using only a windows manager (e.g. IceWM, openbox...).

a good light weight distro (debian based) is AntiX. Also Debian in general is often lighter on resources usage, but that is because they could be missing a thing or two that Ubuntu has setup out of the box. this is fine if oyu do not actually need that thing that is missing and needs to be installed.

a light, nice Ubuntu based distro is Bodhi linux or Peppermint (which i think also uses LXQT or LXDE).

Another Debian based one to try out is Tori linux which was made specifically for users of very old PCs.

---

### Post by webaake on 2019-03-04
Yes, a used Nvidia GPU-card and 1 more GB of RAM would do a lot. Check Ebay.

---


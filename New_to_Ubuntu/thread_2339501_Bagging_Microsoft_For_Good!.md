---
title: "Bagging Microsoft For Good!"
date: 2016-10-09
forum: New to Ubuntu
---

### Post by tpelle2 on 2016-10-09
I am really getting fed up with Microsoft!  Every update that they push down seems to make things more annoying than the last.  Things that I could do with one click last week now take two or three, and the user interface looks more and more cell-phoneish than the last.

I used to have Linux on my Toshiba notebook running in an Oracal Virtualbox, but this last update seems to have killed it.  I think I'm going to go to Best Buy or somewhere and buy a reconditioned name brand notebook and try my hand at getting an Ubuntu machine running without having to mess with partitioning my hard drive, dual-booting, etc.

Way back when, I used to run FreeBSD as my OS on my desktop PC.  I used to use Window Maker as my X11 window manager, and see that Window Maker is back being developed again.  I believe I would like to go that way again, as I would like to get away entirely from that "Windows look" - it really bugs me that so many Linux user interfaces are trying to look like Windows.  Basically 99% of what this machine would be tasked with doing would be surfing the 'net and participating in forums.

Which "version" of Ubuntu would be best suited for getting Window Maker up and running?

---

### Post by sudodus on 2016-10-09
If you want a very light-weight system, you can skip the full desktop environments of standard Ubuntu and the flavours (Kubuntu, Lubuntu ... Xubuntu). Instead you install a text based system either from the Ubuntu mini.iso or Ubuntu Server iso file, and a simple window manager (you know Window Maker, I have used **Fluxbox**, **JWM**, and **Openbox**), plus the most necessary program packages, for example ***xinit*** and ***xterm***. Then you can gradually add program packages.

I didn't know if there is a debian package with Window Maker, or if you have to compile it yourself from source code, but the window managers, that I mentioned are easily available from the Ubuntu repositories.

So I searched the internet for ***Window Maker deb package***, and found **wmaker**, which can be installed with

```
sudo apt-get install wmaker
```

If you get **Lubuntu**, you will get plain Openbox automatically, and you can select it at the log in screen. You get a plain grey background, and if you right-click (somewhere on the background) you will get a menu, where you can select different tools, for example xterm.

By the way, if you want something really old and light-weight, I think you can still install **twm**, an old windows manager from unix.

-o-

On the other hand, standard Ubuntu with Unity looks and works quite differently from Windows, and it seems that recently Microsoft has made Windows look more like Unity ;-)

---

### Post by bearlake on 2016-10-09
Hi,

Openbox is worth checking it but you have many options.

Then again, try them all.

---

### Post by tpelle2 on 2016-10-09
Openbox looks good - similar to Window Maker without the "clip", it appears.

Does LUbuntu have all the necessary features such as network printer support?  Ability to run something like the KDE office suite?

Were I to install a "full blown" Ubuntu, such as the one that comes with the Unity desktop, can I still install Window Maker for an alternate look and feel?

---

### Post by deadflowr on 2016-10-09
> Were I to install a "full blown" Ubuntu, such as the one that comes with the Unity desktop, can I still install Window Maker for an alternate look and feel?
Of course you can.
You can install any alternate desktop you want.
Just choose to log into it at the login screen.

Most window managers and desktop environments will be listed.
Worst case is you would need to create an xsession .desktop file for it.

---

### Post by mastablasta on 2016-10-10
> **tpelle2 said:**
>  Ability to run something like the KDE office suite?

it will pull a lot of KDE libraries in. why not just use KDE? you can set it up to look as you want. almost.

yes, Lubuntu has all the stuff you mentioned.

---

### Post by monkeybrain20122 on 2016-10-10
Since you are getting a notebook I would do some research about the hardware first and make sure that secure boot can be disabled before I worry about which DE (or that Ubuntu live usb can boot from it ad erase windows, in theory it should be able to even with secure boot on but hardware manufacturers might have monkeyed around with the implementation) Cosmetic things are trivial. If machine works for one flavour of Ubuntu chances are it will work for all (and most Linux distros)

---

### Post by HermanAB on 2016-10-10
As mentioned above, if you want to have a light weight system, install the server version and then add the desktop environment(s) you want.

Alternatively, if you want a screaming fast super light weight system, then you got to install Slackware, but that is not for the faint of heart.

---

### Post by Kris_M on 2016-10-11
I suppose if I had to get a laptop I would look at a win7 (just checked - MC has 39 of them starting at 229) one and then either install to dual boot or just wipe the disk and single boot Linux.  To me, the key is a BIOS system rather than a UEFI (as 8.0, 8.1, and 10 are) - much simpler to change things like partitions and boot/mbr partitions, and motherboards. I have a laptop that I keep as spare that has win7sp1 on it. it gets no use.  I run this which is a desktop with win7 and Ubuntu16.04.1 dualboot.  Ubuntu may look a bit like win7, but to me, win10 looks like the failed windows phones.  I tried them all and backed off to win7 and then started running Ubuntu.  MS is changing the win update to rollups and then there's the spying stuff etc (I've removed about 8 KBs so far and do NOT autoupdate) so I am faced with dealing with that if I want to use windows.  That's why I like Ubuntu - frequent security etc updates that work.  Key: they work.  I back up my SSD and my Linux partition with Clonezilla so I can endure catastrophic with little effort. I use Ubuntu 99.9% of the time.  I ran win7 today only to make sure it would work with the new (to me)(open box) graphics card. Huge waste of time. Google and the folks here help me find answers to all my questions.  Love it!

---

### Post by NM5TF on 2016-10-13
> **HermanAB said:**
> As mentioned above, if you want to have a light weight system, install the server version and then add the desktop environment(s) you want.

Alternatively, if you want a screaming fast super light weight system, then you got to install Slackware, but that is not for the faint of heart.

If you want a really fast, cutting-edge, fully customizable OS then go with ARCH.....which is REALLY not for faint of heart...but you
will learn a LOT about how Linux works...\\:D/

---


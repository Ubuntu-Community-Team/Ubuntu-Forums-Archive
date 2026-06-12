---
title: "How to update Ubuntu?"
date: 2005-03-14
forum: Repositories &amp; Backports
---

### Post by theChauvinist on 2005-03-14
I'm pretty much a complete noob, as you can tell by the question. I recently installed Fedora, and easily updated it with up2date.

However, now I've installed Ubuntu 4.10, I'm at a loss as to how to update it...

I'm guessing perhaps it has something to do with apt-get, but I don't even know what that is  :-s .

I have looked for info, but I can't find any, and my brains melted after hours wrestling to get Ubuntu online.

Thanks in advance!

---

### Post by jdong on 2005-03-14
There's a program called "Synaptic Package Manager" in the Administration menu. Have fun with it!

---

### Post by theChauvinist on 2005-03-14
Thanks a lot, it's downloading now.

To update from Warty to Hoary do I need to fiddle with the repositories list?

Also, are the updates on there generally delayed? (I don't think it found a more recent version of Firefox than 0.9.3 but that could just be me).

Cheers :grin: .

---

### Post by jdong on 2005-03-14
To upgrade to Hoary, you need to replace all instances of "warty" with "hoary" in the repositories list ("sources.list") and run a **smart upgrade**. Make sure you set aside some free time to fix little issues that pop up here and there.


As far as version updates, they are held off until the next release. When Warty was released, 0.9.3 was the newest version of firefox that was stable (1.0PR1 was available at the time, but it would randomly segfault and close down). As a result, it'll stick until Hoary, which has Firefox 1.0 with Debian GNOME integration patches...


If you'd like to see newer software in the meantime, I suggest that you look at the unofficial **Ubuntu Backport Project** ([http://backports.ubuntuforums.org)](http://backports.ubuntuforums.org)), started & managed by me. Currently, the Hoary Firefox is available for Warty under Backports, along with about 5GB of other various updates, include WINE, Abiword, GAIM, xchat, and so much more.

---

### Post by theChauvinist on 2005-03-14
Aaah, it's much clearer now  ;) .

Thanks very much, I'll try and upgrade to Hoary tomorrow.

---


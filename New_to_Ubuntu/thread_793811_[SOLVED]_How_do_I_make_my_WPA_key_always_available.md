---
title: "[SOLVED] How do I make my WPA key always available?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Cadmus on 2008-05-14
Hopefully this should be an easy one, my HTPC is working happily on wireless, and set to auto-login. However each time I log in I'm prompted for my password in order to order to unlock my saved WPA key.

I've taken a look at Hardy's new permissions thingy but I can't seem to find anywhere where I can make the key always available. Can it be done? If so where?

---

### Post by PartisanEntity on 2008-05-14
You mean you are prompted to give the networking application access to your keyring?

What networking application are you using? Network manager?

As far as I know, this issue with NW was fixed and the annoying request to unlock the keyring stopped appearing in the previous version of Ubuntu (Gutsy)?

---

### Post by Cadmus on 2008-05-14
I am using Network Manager under Hardy.

---

### Post by PartisanEntity on 2008-05-14
Okay, did a Google search, apparently this happens with WEP.

Solution:

You should install the libpam-gnome-keyring package and then log out of your system and in again. You will be prompted to unlock your keyring with an option not to ask again or something like that.

From: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/125075](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/125075)

---

### Post by Cadmus on 2008-05-14
Champion! I'll give that a go when I get home.

---

### Post by Cadmus on 2008-06-16
Having some time this weekend I finally got a chance to look it up, the real solution is to remove the password on your login keyring in the keyring manager.

---


---
title: "Which version of ubuntu do I have?"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by Carnivorum on 2012-03-08
Bs'd

How can I see what version of Ubuntu I have?

---

### Post by jerome1232 on 2012-03-08
(on newer versions) Click the gear symbol in the top right, click system settings, click system info

(on older versions) you can click About->Ubuntu (my phrasing may be off, it's been a long time since I've used gnome2)

on the cli

```
lsb_release -rc
```

---

### Post by Carnivorum on 2012-03-08
> **jerome1232 said:**
> (on newer versions) Click the gear symbol in the top right, click system settings, click system info

(on older versions) you can click About->Ubuntu (my phrasing may be off, it's been a long time since I've used gnome2)

on the cli

```
lsb_release -rc
```

When I go to "About Ubuntu" he says:

Thank you for your interest in Ubuntu 9.04
                - the Jaunty Jackalope - released in April 2009.

So I want to upgrade, is that an option, or do I need a whole new installation?

Can I install all new from an USB stick?

---

### Post by jerome1232 on 2012-03-08
Unfortunately 9.04 is very old and has run to it's end of life (ended in october of 2010) so you can't just upgrade using the repositories. 

With that being said one method to upgrade is you can download the iso of an alternate install disc of the next release, 9.10, once you get the iso you can use it to upgrade. You would then need to repeat to get to 10.04, which is still supported, you can stick with that version or do network upgrades via update manager until you get to the current version.

Unfortunately Ubuntu.com doesn't seem to host 9.10 iso's anymore and I don't know if you can upgrade from 9.04 directly to 10.04. If I were you I would just install a newer version.

If you do manage to find an alternate cd iso of 9.10, To upgrade using an iso you need to first copy the iso to your desktop, rename it altinstall.iso, mount it, then run the upgrade.

```
sudo mount -t iso9660 -o loop ~/Desktop/altinstall.iso /mnt
sudo /mnt/cdromupgrade 
```

---

### Post by bronquel on 2012-03-08
you can find old versions here:
[http://iso.linuxquestions.org/ubuntu/ubuntu-9.10/](http://iso.linuxquestions.org/ubuntu/ubuntu-9.10/)

---

### Post by gordintoronto on 2012-03-08
If you have an older computer, you might find that the current Lubuntu works better than the current Ubuntu. How much memory is in your computer?

My suggestion: backup all your data, at least twice. That includes email and browser bookmarks, which require special processing. Then install a current version. However, you might find it preferable to wait until late April, when a new long-term release arrives.

---


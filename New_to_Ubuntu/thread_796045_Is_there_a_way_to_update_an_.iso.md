---
title: "Is there a way to update an .iso?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2008-05-16
i'm downloading an .iso of the Hardy DVD and was wondering if there is a way to update the .iso so i don't have to install then spend three hours downloading updates right after.

what i'm asking is if there is a way to do to an ubuntu iso what i did when i slipstreamed SP2 and an XP SP1 disk to make a SP@ install disk

---

### Post by dstin1 on 2008-05-16
don't worry about there really isn't really that many updates yes even if you are on dial up you should be able to get them without waiting too long.

---

### Post by Bubba64 on 2008-05-16
> **Sonic Reducer said:**
> i'm downloading an .iso of the Hardy DVD and was wondering if there is a way to update the .iso so i don't have to install then spend three hours downloading updates right after.

what i'm asking is if there is a way to do to an ubuntu iso what i did when i slipstreamed SP2 and an XP SP1 disk to make a SP@ install disk

If you download a daily ISO you will get the up to date download short of any updates that day or maybe the day before. You can install that and if you add additional repositories, they should be the only extra downloads besides any packages to enable all the media stuff you might want. Just Google daily ISO hardy and choose the desktop CD or alternate CD depending on what you think is best. I don't personally know if you can update an ISO I doubt it but get the daily. Since I left this message I realized I had the daily hardy desktop not the alternative CD link in my bookmarks here it is.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Nice dudes idea is a good one though so do what works for you.

---

### Post by nicedude on 2008-05-16
You can't update the ISO per se but there is a solution for your question. You will need to install hardy onto a machine and then update it and add anything extra you want as standard software the same way you do this now. Then get a software called remastersys I believe it is available from the repositories if not a ubuntu deb will be easy to find, so get it and install it along with anything else it requires. Then remaster can build you a custom ISO with all the updates and extra software included on it. Then you can burn that to a CD or DVD ( In case you added a bunch of stuff ) and then install to additional systems with everything pre-updated to the level when you made it.

Hope this helps you out as I am about to make one myself for installoing on PC's with dialup access.

GOOD LUCK BUDDY

---

### Post by Sonic Reducer on 2008-05-16
that would be a good idea if i was installing everything on a bunch of pc's, but i'm just installing it on my desktop, thats more trouble than really worth

---

### Post by Golem XIV on 2008-05-16
There's also **aptoncd** (in the repositories) that can create a CD with all downloaded updates.  Note that I haven't used it myself, so I can't help you much with it :-P

<edit> Doh! I forgot how I did this earlier.  All the things that you downloaded from the repositories (including updates, drivers and software) will be in /var/cache/apt/archives

You can copy this entire directory to an external drive and after reinstallation copy it back to where it was:
```
sudo cp -rfv /var/cache/apt/archives /media/disk/path/to/backup
reinstall
sudo cp -rfv /media/disk/path/to/backup /var/cache/apt
sudo apt-get update
```
now the system will read the updates directly from cache and it won't need to download them from the repos.
</edit>

---


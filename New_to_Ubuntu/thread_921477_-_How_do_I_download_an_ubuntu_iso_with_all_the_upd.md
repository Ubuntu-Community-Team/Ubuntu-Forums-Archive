---
title: "- How do I download an ubuntu iso with all the updates included?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by CostaRica on 2008-09-16
Hi.  I have several machines I want to install, but I do not want EVERY machine to have to download the tons of updates to this day.  -Is there a way to download the up-to-this-day ubuntu 8.04?  Thanks!

---

### Post by iaculallad on 2008-09-16
One option for you to do is to fully update a single PC and use AptOnCD to create a CD repository for you to use on other PC's.

```
sudo apt-get install aptoncd
```

---

### Post by tangibleorange on 2008-09-16
> **CostaRica said:**
> Hi.  I have several machines I want to install, but I do not want EVERY machine to have to download the tons of updates to this day.  -Is there a way to download the up-to-this-day ubuntu 8.04?  Thanks!

hmm not really but you have a couple of options:

Ubuntu 8.04.1 has a lot of updates included - you shouldn't have to download much (but I make no guarantees)

You could download a mini .ISO (from [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")) and then install on all your computers. This CD downloads all the current packages and so there is no need for upgrades once installed, but you have to download all packages for every computer - you will end up using more bandwidth if you install on lots of computers.

Finally, there exists the possibility to use option 2 on 1 computer, and then create an CD image of that PC's installation and use that CD to install on other computers. There is a tool to do this, but I can't remember its name off the top of my head.

EDIT: The tool has been posted above :)

---

### Post by OffAxis on 2008-09-16
you could also try an apt-mirror on the network.
[https://help.ubuntu.com/community/Installation/LocalNet#Advanced:%20Network%20install%20using%20apt-mirror](https://help.ubuntu.com/community/Installation/LocalNet#Advanced:%20Network%20install%20using%20apt-mirror)

---

### Post by snowpine on 2008-09-16
Remastersys is the name I believe you're looking for TangibleOrange.

CostaRica, for various reasons, the Ubuntu project "freezes" the Ubuntu ISO at particular release points (8.04, 8.04.1, etc) rather than providing a completely up to date ISO. Some distros (like Debian unstable I think) provide daily builds but it's just not a project on which Canonical chooses to spend their resources.

---

### Post by zvacet on 2008-09-16
If you want to install Ubuntu on several comps I believe that you want all of them to be updated.Read [this]("https://help.ubuntu.com/community/Apt-Cacher-Server") to see how to do it.

---

### Post by philinux on 2008-09-16
At least start of one machine with the latest build.

[http://cdimage.ubuntu.com/hardy/daily-live/current/](http://cdimage.ubuntu.com/hardy/daily-live/current/)

---

### Post by CostaRica on 2008-09-16
Thank you, everybody.  Got more and better answers than expected :guitar:

---


---
title: "Broke firefox..."
date: 2008-07-23
forum: New to Ubuntu
---

### Post by kdb424 on 2008-07-23
I accidentally broke firefox, then tried to uninstall and reinstall it, and now I can't find it. I tried apt-get, and the built in package manager to uninstall, and then reinstalled with both and I don't see it. I do have a backup computer if I need to get files for it from the internet (in a browser) for it.

---

### Post by rockstarrem on 2008-07-23
Try this:

```

sudo apt-get purge firefox-3.0
sudo apt-get install firefox-3.0

```

If I'm right the package name is firefox-3.0, not firefox. Obviously for version 3 :D.

---

### Post by kdb424 on 2008-07-23
Alright. I'll try that out right now. If it works, I'll reply from ubuntu not mac, lol.

---

### Post by kdb424 on 2008-07-23
Fixed it. Ubuntu died, and I'm installing Kubuntu right now. On the same machine. I love live CD's. I know it's a change of topic, but can I install and use both desktops?

---

### Post by Tim Sharitt on 2008-07-23
Yes, you can install both desktop environments. Since you say you are installing Kubuntu I will assume you want to install gnome. There are a few ways to do it, all with varying numbers of utilities and applications.
This-
```
sudo apt-get gnome 
```
is probably the easiest way, but I believe it installs the most "stuff." Before doing anything, I would recommend getting some advice with more advice on the subject. Posting a thread in the "Desktop Environments" forum for just this may be a good idea. Searching Google and the forums may also yield the answers your looking for.

---

### Post by steveneddy on 2008-07-23
I think it's

```
sudo apt-get install ubuntu-desktop
```

---

### Post by kdb424 on 2008-07-23
> **steveneddy said:**
> I think it's

```
sudo apt-get install ubuntu-desktop
```

I think both work, but I'm trying yours. I said screw reading. I learn best by breaking stuff. My stupid windows partition is marked as linux on my rEFIt but I'll figure it out. Might be the bootloader. Thanks for all fo your help!

---

### Post by RomeReactor on 2008-07-23
> **steveneddy said:**
> I think it's

```
sudo apt-get install ubuntu-desktop
```

Hi. Whenever you want to install another desktop, it's better to do it with Aptitude instead of Adept, Synaptic, Add/Remove or Apt-Get:
```
sudo aptitude install ubuntu-desktop
```
If you want to remove it later, you can do it like this:
```
sudo aptitude purge ubuntu-desktop
```
Otherwise, you would need to [paste a long command]("http://www.psychocats.net/ubuntu/purekde.php").

---

### Post by kdb424 on 2008-07-23
Thanks. I was told that by a utorial that I looked at but if I would loose one, it would be the KDE. I got a Kubuntu disk from shipit today and checked it out, but it's no Ubuntu... Can I try out the Xbuntu desktop this way too?

---

### Post by rockstarrem on 2008-07-23
Yep, you just run the LiveCD and it should run. You can burn it yourself as well if you need to: [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by kdb424 on 2008-07-23
I mean can I try out sudo apt-get install xbuntu-desktop

---

### Post by RomeReactor on 2008-07-23
It would be best if you used Aptitude:
```
sudo aptitude install xubuntu-desktop
```
See my post on the previous page.

---

### Post by kdb424 on 2008-07-23
Thanks!

---

### Post by steveneddy on 2008-07-25
> **RomeReactor said:**
> Hi. Whenever you want to install another desktop, it's better to do it with Aptitude instead of Adept, Synaptic, Add/Remove or Apt-Get:


I had forgotten about that.

I have been down that path before.

---


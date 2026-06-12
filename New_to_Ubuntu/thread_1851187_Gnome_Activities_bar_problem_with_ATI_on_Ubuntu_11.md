---
title: "Gnome Activities bar problem with ATI on Ubuntu 11.10"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by pvjlieuthier on 2011-09-27
Hello everyone,

I know I shouldn't be discussing Ubuntu 11.10 problems, once it's still in development. Specially when it involves Gnome Shell. But I think you can help me with my problem. Well, I don't know how to describe it so I will send an screenshot.

As I said, I'm using Oneiric with Gnome 3, and open source drivers for an ATI card. Well, it's all 99%. As you can see in the screenshot, the standard Unity top bar is behind the activities bar. It does not affect anything, it is just very annoying... I've already removed Unity and I don't want to wait to Ubuntu 11.10's final release.

I'm looking forward to hearing from you!

--- EDIT ---
Never mind! I updated the system and everything is pretty now! Thanks!

---

### Post by schorem on 2011-09-30
I've got the same, it looks all wierd. I cannot even take a screenshot of it... it's all grey, somehow.

---

### Post by pvjlieuthier on 2011-09-30
I was only able to take screenshots with the app [Shutter]("http://shutter-project.org/").

```
sudo apt-get install shutter
```The default app did not work. If you have an ATI card, I recommend to uninstall the ATI driver and install the open-source one, using the [xorg-edgers]("https://launchpad.net/%7Exorg-edgers") ppa.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

---


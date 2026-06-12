---
title: "Installing notify-sharp"
date: 2008-10-26
forum: Programming Talk
---

### Post by mashcaster on 2008-10-26
Hi,

I am trying to install notify-sharp so I can use it with one of the programs I am trying to code.  However, I have no idea how to install this.

Can someone please help?

I am using Ubuntu 8.04

---

### Post by twisted_steel on 2008-11-18
The package in 8.04 is called libnotify0.4-cil.  The documentation (monodocs) to go with it are monodoc-notify-sharp-manual.  I think they are from the 'universe' repository, though I may have pulled them in through a different PPA install.

To get both, just do:
```
sudo apt-get install libnotify0.4-cil
sudo apt-get install monodoc-notify-sharp-manual
```If this fails, let me know and I can try to determine the source of my packages.

---

### Post by mashcaster on 2008-11-19
> **twisted_steel said:**
> The package in 8.04 is called libnotify0.4-cil.  The documentation (monodocs) to go with it are monodoc-notify-sharp-manual.  I think they are from the 'universe' repository, though I may have pulled them in through a different PPA install.

To get both, just do:
```
sudo apt-get install libnotify0.4-cil
sudo apt-get install monodoc-notify-sharp-manual
```If this fails, let me know and I can try to determine the source of my packages.

I'll try to give this a go tonight if I get a chance.  Thanks for the reply.

---

### Post by mashcaster on 2008-11-19
I get a message saying that the package libnotify0.4-cil
 could not be found.

---

### Post by twisted_steel on 2008-11-19
> **mashcaster said:**
> I get a message saying that the package libnotify0.4-cil
 could not be found.

I think I found two potential candidates of where it came from: the Banshee and GNOME Do PPAs.

Banshee: [https://launchpad.net/~banshee-team/+archive]("https://launchpad.net/%7Ebanshee-team/+archive")
GNOME Do: [https://launchpad.net/~do-core/+archive]("https://launchpad.net/%7Edo-core/+archive")

Both have notify-sharp listed, though it may actually install as libnotify0.4-cil.  This might be a good opportunity to try out Banshee and/or Do while solving your problem :)

I would just install either Banshee or GNOME Do, which should pull it in.

---

### Post by mashcaster on 2008-11-20
> **twisted_steel said:**
> I think I found two potential candidates of where it came from: the Banshee and GNOME Do PPAs.

Banshee: [https://launchpad.net/~banshee-team/+archive]("https://launchpad.net/%7Ebanshee-team/+archive")
GNOME Do: [https://launchpad.net/~do-core/+archive]("https://launchpad.net/%7Edo-core/+archive")

Both have notify-sharp listed, though it may actually install as libnotify0.4-cil.  This might be a good opportunity to try out Banshee and/or Do while solving your problem :)

I would just install either Banshee or GNOME Do, which should pull it in.

I'll give gnome do a go tonight.

---

### Post by mashcaster on 2008-11-20
Finally got it installed.  How do I make use of it?

---

### Post by twisted_steel on 2008-11-20
> **mashcaster said:**
> Finally got it installed.  How do I make use of it?

I really have no idea actually.  I was trying to find out how to use it when I came across your post.  I did install the monodoc file for notify-sharp, but a ton of sections are just missing.  I also haven't been able to figure out the base location of the library.

---

### Post by mashcaster on 2008-11-21
> **twisted_steel said:**
> I really have no idea actually.  I was trying to find out how to use it when I came across your post.  I did install the monodoc file for notify-sharp, but a ton of sections are just missing.  I also haven't been able to figure out the base location of the library.

No prob.  I'll try putting some time into this on the weekend and will post back here if I figure anything out.

Thanks for the help.

---


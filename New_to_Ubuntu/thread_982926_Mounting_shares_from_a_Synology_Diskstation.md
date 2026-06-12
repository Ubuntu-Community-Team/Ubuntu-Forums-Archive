---
title: "Mounting shares from a Synology Diskstation"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by krolben on 2008-11-15
Hi all

I'm kinda new to Linux, having just installed Ubuntu 8.10.

I'm trying to figure out what the best way of mouting shares from my Synology Diskstation is.
One problem is that the Diskstation will often be on "snooze" when I start up Ubuntu. From first connect attempt it takes about 10 seconds until drives can be found.

How can I mount the shares at boot time so I always have access to them?

By just browsing to "network" -> "diskstation" and mounting a drive from there I also find that some applications (like Banshee) won't allow me to load files from there.

---

### Post by mapes12 on 2008-11-15
Try Pysdm which allows you to decide which drives to mount or unmount during startup. Pysdm is a GUI application and therefore easy to use.

To install it

```
sudo apt-get install pysdm
```

To run it after install

```
sudo pysdm
```

Home page: [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

### Post by krolben on 2008-11-16
Hi mapes12

Thanks for your reply.
I couldn't see the desired shares in Pysdm. I guess it's because it's a network drive so my system doesn't know anything about those shared when running pysdm.

I managed to set up mounts in /etc/fstab. I haven't tested it when starting Ubuntu while the Diskstation is in sleep mode. That'll be interesting :)

---


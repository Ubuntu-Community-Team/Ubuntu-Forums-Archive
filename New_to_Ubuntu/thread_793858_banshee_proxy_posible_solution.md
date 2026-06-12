---
title: "banshee proxy posible solution"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by farueulogy on 2008-05-14
I like to use banshee for my music and also like to use it for last.fm and podcasts. The problem is it is yet to use the gnome proxy or have the option to enter a proxy.

I have technically temporarily "solved" this with running from terminal:

```
export http_proxy=http://my.proxy:port
banshee --play-enqueued --enqueue %U
```
*where my.proxy is my proxy number and port is my port number*

But now I would like to write a script for this so I can make a nice clean launcher and not have a terminal window open.

So far I have tried creating bansheeproxy.sh

```
#!/bin/sh
export http_proxy=http://my.proxy:port
banshee --play-enqueued --enqueue %U
```

But this (and variations of *#!/bin/bash* and *banshee*) come with a DBUS error. It wants me to "run banshee through DBUS launch".

I have no idea what this means. Also my music library doesn't load, nor do my preferences.

Help

---

### Post by farueulogy on 2008-05-15
bump

---

### Post by ZabiGG on 2008-05-15
Question:

Why did you post this in Absolute Beginners?

Just curious ;)

---

### Post by farueulogy on 2008-05-15
Because I am a begginer in my head pretty much - can someone move it please?

---

### Post by ZabiGG on 2008-05-15
I would if I could... General Help Questions sounds nice. What say you?

Cheers,


Z.

---

### Post by y-lee on 2008-05-16
I don't use banshee so don't know much about this issue. But you could try putting [dbus-launch]("http://linux.die.net/man/1/dbus-launch") in front of the banshee command in the script.

---

### Post by farueulogy on 2008-05-17
Ok, I edited the script to

```
#!/bin/sh
export http_proxy=http://my.proxy:port
dbus-launch banshee
```

and executed it without sudo (changed permissions etc)

and it works :eek: - thanks y-lee

It means that last.fm and art work are now working through the proxy. However, I've only been using it for the last little while and it mights not be that stable.

For example - radio plugin doesn't work on it and when I tried to use it banshee crashed. However, last.fm recommended and neighbors works fine.

I'll keep messing around.

---

### Post by farueulogy on 2008-05-19
Update - Generally banshee has been quite good running behind the script and deals well with scrobbling tracks to last.fm. However, it doesn't do so well with larger amounts of data such as listening to the radio or podcasts. I can generally manage it but does occationally crash.

---

### Post by ptg21 on 2008-09-23
Great tip!  Many thanks.

Setting 

alias banshee='dbus-launch banshee-1' 

in .bashrc works fine for me after setting up the cache using System->Preferences->Network Proxy.  

Both last.fm and internet radio then work fine.

---

### Post by s.kaniff on 2009-08-26
Hi,
"dbus-launch banshee-1" works great. But my multimedia keys have stopped working with banshee. Anyone know's how I can fix this?

They work perfectly without the dbus-launch but internet radio was buffering too much without dbus-launch. Now internet radio works great bu multimedia keys are gone.. :(

---


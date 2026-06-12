---
title: "Share connection xbox 360 LIVE"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by JJX90 on 2008-04-25
Hey, I'm trying to connect to xbox live through my laptop. My setup is this: 360 is wired to laptop, which is connected wirelessly to my LAN.

I can't get it to work, can someone help me?

---

### Post by Joeb454 on 2008-04-25
You need to bridge the 2 connections :)

```
sudo aptitude install bridgeutils
``` that will get you started, I had a script somewhere. I'll find the post

---

### Post by Joeb454 on 2008-04-25
Ok I found my old post.

Can you try this for me. You may need to make the scripts executable, and then you will likely need to edit the script (can be done in any text editor) to use wlan0 instead of eth1 or something.

[Original Post]("http://ubuntuforums.org/showpost.php?p=4159986&postcount=8")

---

### Post by JJX90 on 2008-04-25
> **Joeb454 said:**
> You need to bridge the 2 connections :)

```
sudo aptitude install bridgeutils
``` that will get you started, I had a script somewhere. I'll find the post

I got this error:

[PHP]
Couldn't find any package whose name or description matched "bridgeutil"
No packages will be installed, upgraded, or removed.[/PHP]

---

### Post by Joeb454 on 2008-04-25
you're missing an 's' off the end of the package name ;)

---

### Post by JJX90 on 2008-04-25
> **Joeb454 said:**
> you're missing an 's' off the end of the package name ;)

Tried both ways, still found nothing.

update: nevermind, missing a "-" going through your old post now, thanks.

---


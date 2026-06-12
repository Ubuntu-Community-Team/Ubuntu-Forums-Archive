---
title: "[SOLVED] Startup now takes FOREVER"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by CJ Master on 2008-11-05
Hey,

My ubuntu used to start up in 13 seconds ago (round a week ago.) But now, it boots up, and while loading it gets stuck on the 95% part of the load bar. It stays like that for like 20 seconds, then goes to this command prompted where its saying something about about booting up this mail thing, that takes 30 more seconds then it boots up normally.

I seriously don't think I did any action that would cause this, I've never really had this problem before.

...oh and yes, it has been happening for a few days now, so its not anything a simple restart will fix. =[

---

### Post by Cypher on 2008-11-05
Is it by any chance waiting on "Sendmail" if so, until Sendmail is properly configured, it's going to stall there for a little while.

If it is indeed "Sendmail" that's stalling, you can safely remove it as it's mainly a program used on Linux server to send mail from the server. You can continue to recieve mail into your Linux desktop using any of your mail programs (Evolution, Thunderbird, etc).

Remove "Sendmail" with
```

sudo apt-get remove --purge sendmail

```
See if removing that speeds up your boot again. You were booting up in 13 seconds? That's quite impressive, how fast is your machine?

---

### Post by CJ Master on 2008-11-05
Well, I recounted, about 17 seconds from logo, my mistake >.< My machine is pretty fast though, I'm happy with it. =]

I tried it. didn't work. Here's what it was stuck on:

```
Mail Transport Agent (MTA) sendmail
```

---

### Post by CJ Master on 2008-11-06
BUMP
rbre
iusr
nn.r
gt y
 u !

---

### Post by CJ Master on 2008-11-07
Bump again :]

---

### Post by CJ Master on 2008-11-09
Bump, still loads super slow. =-(

---

### Post by CJ Master on 2008-11-09
*coughcoughhackcoughhaaaackwhezecough*

---

### Post by CJ Master on 2008-11-12
Bump again.... :confused:

---

### Post by CJ Master on 2008-11-13
BUMP, this problem is really annoying...

---

### Post by bobyy on 2008-11-13
Ciao try to tke a look at your conf:
 $sudo nano /etc/network/interfaces

and do `it like this .. put a coment in front of auto eth0 and iface eth0

  # The primary network interface
  #auto eth0
  #iface eth0 inet dhcp

if you have inside just lo/eth0 interfaces
After upgrade to Ibex it was also my issue and this solve the problem.

---

### Post by starcannon on 2008-11-13
Hi there, I just found the solution for your situation in this post:
[http://ubuntuforums.org/showthread.php?t=822493](http://ubuntuforums.org/showthread.php?t=822493)

You seem to have the same exact problem that person was having, give that a go, I think it will fix you up.

GL and keep it fun.

---


---
title: "Synaptic won't start..."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by .:PiXi²:. on 2008-04-30
Hi

I'm using Ubuntu for a few months now, and haven't got any problems till now. I made a fresh Ubuntu installation since Hardy came out, so 6 days ago and I was thinking about going 100% Ubuntu. But suddenly, this problem came up. Synaptic just won't run any more. In any way, I can't add/remove packages, update language files, etc.

When I run:
```
synaptic
```
I can't make any changes, and when I run:
```
gksu /usr/sbin/synaptic
```
nothing happens.

Any help is welcome...
Thanks in advance.

---

### Post by Kobalt on 2008-04-30
Hello,

When you pull up a simple command like the following in a Terminal, what do you get in result ?
```
sudo aptitude update
```

---

### Post by daverich on 2008-04-30
hmm

I wonder if this is coincidence.

It happened to me also.

Go into SYSTEM/ADMIN/NETWORK and click on hosts.

your desktop should look like -

buffy-desktop

if it has more after it then edit it and take out the . and whatever follows.

That fixed it for me.

Kind regards

Dave Rich

---

### Post by .:PiXi²:. on 2008-04-30
Thanks for the quick reply.

To Kobalt:
```
sudo aptitude update
```
and
```
sudo apt-get update
```
returned the same thing: **SUDO: unable to resolve host ....** or something

To daverich:
Your trick solved the problem, thanks!
I think it was caused by the setup of a Samba server, the dot was followed by my workgroup name.

Thanks again! And sorry for my bad English.

---

### Post by zedascouves on 2008-05-18
Hi!

I'me having the same problem, and if I do as Daverich said, when I close the window, it turns back to what it was before.

So right now it's like "Tuor.home", where Tuor is the computer name and "home" is the (windows) workgroup name. Any suggestions?:confused:

---


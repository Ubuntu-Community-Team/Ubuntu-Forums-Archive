---
title: "Intel Centrino Wireless-N 6150 Issue"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by peckpeck20 on 2012-04-11
Hello guys
I am new to Ubuntu,Great OS.I think the best out of all if you ask me.Recently I bought a new laptop a sony Vaio VPCEG37FM/W.
I was going to install ubuntu 11.10 but during the installation process I noticed I couldn't manage to connect to my Wireless network.I cancelled the instalation and started ubuntu as a usb Live. Once in I still could not get my wireless to work,it says my wireless is disabled and when I "enable" it,It still wont show up networks.When I run backtrack  5 R2 my wireless works just fine.
I am running a intel i5 2.5 ghz 6gb RAM intel HD Graphics 3300 640 gb Hdd
My wireless card seems to be a : Intel Centrino Wireless-n 6150 with wimax connectivity.

Hope you guys can help me to get things up and running.;)

---

### Post by Daveth on 2012-04-11
Halo. Welcome to the Ubuntu Forums. There seems to be a bug fix for your problem, and it is here, although it looks a little "involved"...
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2325](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2325)

If this means nothing to you, let us know, and I am sure someone can guide you through it.
Pleased you are enjoying Ubuntu, issues aside:p

---

### Post by peckpeck20 on 2012-04-11
> **Daveth said:**
> Halo. Welcome to the Ubuntu Forums. There seems to be a bug fix for your problem, and it is here, although it looks a little "involved"...
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2325](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2325)

If this means nothing to you, let us know, and I am sure someone can guide you through it.
Pleased you are enjoying Ubuntu, issues aside:p

Hey there!
thanks for the quick reply,I went to the link u posted but it seems I am a total noob and I really dont understand how to do it Dx
If you know someone or yourself would be willing to guide me though the process would be much appreciated.
Thanks Again,
  Peckpeck20

---

### Post by Daveth on 2012-04-13
I think we need more help here! The fix works on 3 series kernels, and I do not know if it is relevant or works on older ones. To find yours type
```
uname
```
into a terminal, and if it spits out a number string starting with a 3, then we might be in business.
The fix goes
```
rmmod iwlwifi
modprobe iwlwifi bt_coex_active=0
```

typed/ pasted into the same terminal over 2 lines. It seems to remove the wifi module and then probe for it.

I am nervous about you doing this however until we get more technical help, so help guys!!!

---


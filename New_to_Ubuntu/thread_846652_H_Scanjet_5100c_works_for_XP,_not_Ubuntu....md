---
title: "H Scanjet 5100c works for XP, not Ubuntu..."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Shobuz99 on 2008-07-01
I'm still a beginner, and I still have questions.
I tried to figure this out myself, and I'm stumped.

I'm dual-booting XP and Ubuntu 8.04 on separate drives.

My HP Scanjet 5100c works fine while connected to the printer port,
and used from XP.
My printer is an HP 5700 and it's connected through USB. It works fine
in both XP and Ubuntu 8.04.

When I restart and go to Ubuntu 8.04, Ubuntu doesn't recognize that my scanner is there. No device is available when I run XSANE.


Do I need to something in root? If so, what do I do?

Thanks for your help..:)

Rick (shobuz99)

---

### Post by kansasnoob on 2008-07-01
Do you have hplip installed?

Just go to synaptic and search for > hplip, if not installed then install it.

---

### Post by khelben1979 on 2008-07-01
Maybe you should try Debian instead?

---

### Post by Shobuz99 on 2008-07-01
Yep, I have hplip installed.
I ran the the hplip toolbox and selected new device, parallel port, and
got "No Devices Found".
What else can I try?

---

### Post by Shobuz99 on 2008-07-01
ok.. remember..beginner here.. how do I run debian?

---

### Post by alienexplorers on 2008-07-01
According to SANE you need:
> Requires ppscsi driver and epst module
No idea where you get them!

---

### Post by Xerp on 2008-07-01
Take a look over here:

[http://ubuntuforums.org/showthread.php?t=782242](http://ubuntuforums.org/showthread.php?t=782242)

---

### Post by kansasnoob on 2008-07-01
I found this thread and it appears they did get it worked out ........... after quite a while.

[http://ubuntuforums.org/showthread.php?t=782242&highlight=HP+Scanjet+5100C](http://ubuntuforums.org/showthread.php?t=782242&highlight=HP+Scanjet+5100C)

---

### Post by khelben1979 on 2008-07-01
> **Shobuz99 said:**
> ok.. remember..beginner here.. how do I run debian?

Fetch a Debian image and burn it to a cd-rom. You can get it from [here]("http://www.debian.org/CD/netinst/").

Since you're a beginner Ubuntu may be a better choice for you since Debian is a bit harder to install but the great thing about Debian is when it's finally installed you can easily upgrade the whole system by a small command: apt-get dist-upgrade and all other upgrades goes really fast with the apt tool.

I don't know exactly what scanner hardware is included in Debian Etch at the moment but you might find what you are looking for in [the Debian Wiki pages]("http://wiki.debian.org/").

---

### Post by Shobuz99 on 2008-07-01
> **kansasnoob said:**
> I found this thread and it appears they did get it worked out ........... after quite a while.

[http://ubuntuforums.org/showthread.php?t=782242&highlight=HP+Scanjet+5100C](http://ubuntuforums.org/showthread.php?t=782242&highlight=HP+Scanjet+5100C)

thanks kansasnoob.. it appears that your link and Xerp's link ends up at the same place: [all variants] HP Scanjet 5100C / ppscsi in Hardy

Anyway, I read through the post. Yeow! Some serious editing going on there..:shock:

I'm not new to computers or Unix/Aix/Linux;** however**, THAT amount of tinkering seems a bit scary. I suppose I could try it...But; I'm a beginner with Ubuntu and have been a MS addicted slave for many years; so I don't know what to expect if I get any errors or what I do to recover.. 
First: remove MS hypo from arm.. pause.. This requires some mulling..:)8-[

The debian option sounds intriguing, but also scary...hmmm
Rick (shobuz99)

---


---
title: "how to completely wipe a hard drive?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2008-04-26
Someone told me that there is a command to completely wipe a hard drive? Something like cat dev 0 >/dev/sdb?? but that obviously doesn't work. Can anyone tell me the correct command to send 0's to a hard drive? Thanks...

---

### Post by Saturn357 on 2008-04-26
I know that rm -rf completely removes everything from your hard drive.
Go to terminal and enter that code in. Don't forget to type "sudo" first.

If I'm wrong, I'm a beginner so I apologize.

---

### Post by sandysandy on 2008-04-26
for secure wipe of hdd see this link

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

regards

---

### Post by e1ektrob0y on 2008-04-26
does anyone know the cat dev 0 thing though??

---

### Post by tamoneya on 2008-04-26
dban is definately the way to go.  I typically use the Ultimate Boot CD when I run dban.  It is one of the many useful utilities that is included.

---

### Post by Monicker on 2008-04-26
You mean something like this?


```
dd if=/dev/zero of=/dev/hda
```


If you want a really rhorough wipe, use dban.

[http://dban.sourceforge.net/]("http://dban.sourceforge.net/")

---

### Post by e1ektrob0y on 2008-04-26
Its a long story really. The problem is its a 500GB drive that has become 136GB because of a bios issue moving the drive between computers with older bios. So, apparently the only way to get the drive to detect as being 500GB again is to totally zero byte it...formatting and partitioning don't work. It is always detecting as 136GB when it is actually 500GB...

---

### Post by ugm6hr on 2008-04-26
Ultimate Boot CD has a variety of disk wiping tools.

I know Active Kill Disk has the option to 0 the drive completely (in fact, is default for the "trial" version).

---

### Post by peterkeyani on 2008-04-26
> **sandysandy said:**
> for secure wipe of hdd see this link

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

regards

I use Dariks Boot n' Nuke !

---

### Post by e1ektrob0y on 2008-04-26
aha! found it...```
cat /dev/zero > /dev/sdb
```

---

### Post by nicedude on 2008-04-26
DBAN is the only wiper ever needed

---


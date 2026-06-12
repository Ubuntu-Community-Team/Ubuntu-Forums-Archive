---
title: "[SOLVED] atheros ar242x in hardy with no net access on that comp..."
date: 2008-05-22
forum: New to Ubuntu
---

### Post by bm13084 on 2008-05-22
any clue how to get it going? am i stuck with ndiswrapper? it's odd that the restricted drivers show up then dont work...

---

### Post by bm13084 on 2008-05-23
luckily, the acer 5520 uses the same card and came with xp... so the drivers were there.  Just disable the restricted drivers and do a regular ndiswrapper install with those drivers... you can find the kit with the drivers on acer's site.  works like a charm.

---

### Post by balagosa on 2008-05-23
just in case can you do a 
```
sudo uname -m
``` and post it here.

---

### Post by Monicker on 2008-05-23
I just recently bought a new laptop which uses an AR242x chipset.  I was able to get it to work by following the instructions is this thread:  [http://ubuntuforums.org/showthread.php?t=789824]("http://ubuntuforums.org/showthread.php?t=789824")

Works great. I don't need ndiswrapper, and I have no problems connecting to my WPA network at home.

---

### Post by bm13084 on 2008-05-23
```
ubuntu@ubuntu-laptop:~$ sudo uname -m
[sudo] password for ubuntu: 
i686
ubuntu@ubuntu-laptop:~$ 

```


edited to add that the way with the patched driver still required net access on that comp.  my way didnt.  as long as you had internet access somehow...

---

### Post by balagosa on 2008-05-24
> **bm13084 said:**
> ```
ubuntu@ubuntu-laptop:~$ sudo uname -m
[sudo] password for ubuntu: 
i686
ubuntu@ubuntu-laptop:~$ 

```


edited to add that the way with the patched driver still required net access on that comp.  my way didnt.  as long as you had internet access somehow...

you got an i686 from "uname -m". is there by any chance you got and AMD64 processor. the above post only works for i386 configuration.

the only way for WiFi to work on i686 is Ndiswrapper: will be posting the x86 guide later.

---


---
title: "Issue With Getting Lubuntu To Reboot"
date: 2020-11-24
forum: New to Ubuntu
---

### Post by haydnliehs on 2020-11-24
In a (successful) attempt to increase the performance of an old laptop by changing the operating system, I downloaded Lubuntu, installed it and deleted Windows.

The Lubuntu version I downloaded is 20.04

When attempting to reboot it or shut it down to later turn it on, rather than taking me to the login screen, it takes me to, for lack of a better description, the basic GNU GRUB command screen.

Through some research I discovered when entering a certain sequence of lines I can then reboot. These can be seen in the attached image below.

How do I void having to type these in every time I reboot or start up the laptop so that it just takes me to the login screen?

Thanks

P.S. If the image is too small I can post a link that can redirect to the image in higher quality

[ATTACH=CONFIG]287454[/ATTACH]

---

### Post by Bashing-om on 2020-11-24
haydnliehs; Welcome to the forum 

Hummm ..

Appears the kernel can not find the boot config file on it's own.
As you can boot with grub speak "(hd0,2)", then we know where that config should be,
We can beat on this manually and attempt to fix
OR
see if the package manager will fix.
Might try re-installing grub from the booted system:
```

sudo grub-install /dev/sda

```
If errors we need to see all in context. Post them back - between code tags-
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

else:
Want to take the learning adventure then we need to see what grub has for it's current config.
post back then:
```

sudo fdisk -lu
sudo blkid
cat /boot/grub/grub.cfg

```

[INDENT]ubuntu
[INDENT][INDENT]fixable
[/INDENT][/INDENT][/INDENT]

---

### Post by ActionParsnip on 2020-11-25
What is the output of:
```

sudo update-grub

```

---

### Post by haydnliehs on 2020-11-27
Thanks guys, it works now.

I used the sudo update-grub command

---

### Post by haydnliehs on 2020-11-27
I used it in the qterminal

---

### Post by Bashing-om on 2020-11-27
haydnliehs; Outstanding :D

Pleased you gave the resolution.
As such ->
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---


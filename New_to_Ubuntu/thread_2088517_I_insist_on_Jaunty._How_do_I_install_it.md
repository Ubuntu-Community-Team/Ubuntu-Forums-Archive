---
title: "I insist on Jaunty. How do I install it?"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by AlaskanPotHead on 2012-11-26
I want to install Jaunty (already have, actually). It was the best for my needs. I've heard all the reasons for upgrading, but the upgrades suck. What I want is to try to install the old packages for it. I have a bunch downloaded, but Synaptic doesn't open them. (tar files) Which means that I have to use the archive manager, and that only seems to want to put all those extracted files on my desktop. I've searched here, Google- everywhere. But nothing tells me how to do this, just to upgrade. Please help.

---

### Post by Frogs Hair on 2012-11-26
I have not worked with unsupported releasese ,so I don't about getting dependencies for installing additional programs. [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by AlaskanPotHead on 2012-11-26
I saw that thread. That's where I found the packages. It just isn't too clear on installing them. Thanks, though.

---

### Post by Frogs Hair on 2012-11-26
Try This .[http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty](http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty)

---

### Post by newb85 on 2012-11-26
> **AlaskanPotHead said:**
> What I want is to try to install the old packages for it.

Do you mean the packages that could be installed on it back when it was still supported?  The easiest way to do that is the same way you would have done it back then--through Synaptic, using the repositories.  The repos still exist, but they've been moved.  Once you change your sources in /etc/apt/sources.list to [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)..., everything should work.

---

### Post by AlaskanPotHead on 2012-11-26
Yes! That's exactly what I want to do. I'll give that a try.

---

### Post by CharlesA on 2012-11-26
Do you have a specific reason for wanting to run Jaunty?

Keep in mind that it is unsupported and is no longer getting any updates - regular and security updates alike.

---

### Post by whatthefunk on 2012-11-26
> **AlaskanPotHead said:**
> I want to install Jaunty (already have, actually). It was the best for my needs. I've heard all the reasons for upgrading, but the upgrades suck. What I want is to try to install the old packages for it. I have a bunch downloaded, but Synaptic doesn't open them. (tar files) Which means that I have to use the archive manager, and that only seems to want to put all those extracted files on my desktop. I've searched here, Google- everywhere. But nothing tells me how to do this, just to upgrade. Please help.

If they are tar files, you probably have to uncompress it and 
```
./configure
make
make install
```

Is there a read me file in the download anywhere?  What are the contents of the file you downoladed?

What reasons do you have for insisting on Jaunty?  It really sint wise to use outdated software.  If its because you dont like Unity, you might want to try a Ubuntu spinoff like Xubuntu or Lubuntu.

---

### Post by CharlesA on 2012-11-26
> **whatthefunk said:**
> 
What reasons do you have for insisting on Jaunty?  It really sint wise to use outdated software.  If its because you dont like Unity, you might want to try a Ubuntu spinoff like Xubuntu or Lubuntu.

Could always stick with 10.04 for a little bit more. Gnome fallback is still on 12.04 as far as I know.

---

### Post by AlaskanPotHead on 2012-11-26
Frogs Hair and newb85- You rock!!! Thank you so much! I once again have the version of Ubuntu that made me fall in love with Linux. Awesome! Now, if I can just remember how to mark this as 'SOLVED'...

---

### Post by DuckHook on 2012-11-26
> **AlaskanPotHead said:**
> Frogs Hair and newb85- You rock!!! Thank you so much! I once again have the version of Ubuntu that made me fall in love with Linux. Awesome!

@CharlesA raises a valid point and you are open to malicious exploits using an unsupported version. But it's hard to counsel caution in the face of such enthusiasm and happiness. May the Linux be with you! :)

---

### Post by AlaskanPotHead on 2012-11-26
CharlesA, I just like everything about it. With each new release the options I like (such as hiding password feedback) are being removed. With 12.10 I don't even get a screensaver anymore. I could try workarounds, but this just gives me what I want. Not getting security updates could be problematic, but I'll take the risk. Thank you, though.

---

### Post by AlaskanPotHead on 2012-11-26
DuckHook, I know. I will have to be very careful. But I love my computer again... :D

---

### Post by CharlesA on 2012-11-26
> **AlaskanPotHead said:**
> CharlesA, I just like everything about it. With each new release the options I like (such as hiding password feedback) are being removed. With 12.10 I don't even get a screensaver anymore. I could try workarounds, but this just gives me what I want. Not getting security updates could be problematic, but I'll take the risk. Thank you, though.
Be careful and make regular backups in case you get owned.

---

### Post by AlaskanPotHead on 2012-11-26
whatthefunk, I do have an outdated PC. I was considering Lubuntu with the LXDE shell. I wish Jaunty had been a LTR...

---

### Post by CharlesA on 2012-11-26
> **AlaskanPotHead said:**
> whatthefunk, I do have an outdated PC. I was considering Lubuntu with the LXDE shell. I wish Jaunty had been a LTR...
LXDE and XFCE are both good for older machines.

Are you dead set on using Ubuntu? You could also check out Debian and Fedora as both have LXDE and XFCE spins.

---


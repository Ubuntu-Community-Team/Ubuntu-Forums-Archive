---
title: "[SOLVED] Incorrectly showing updates"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by adobrakic on 2008-09-07
I'm on LinuxMint, and the little lock icon on the bottom right keeps showing me that I have updates, but when I open it.. there's no updates there.

Also, there haven't been updates for over a month now, which is weird for Linux.

---

### Post by Xiong Chiamiov on 2008-09-07
What about if you update through the terminal?
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by iaculallad on 2008-09-07
> **adobrakic said:**
> I'm on LinuxMint, and the little lock icon on the bottom right keeps showing me that I have updates, but when I open it.. there's no updates there.

Also, there haven't been updates for over a month now, which is weird for Linux.

Try updating on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by adobrakic on 2008-09-07
Now that I think about it, I do this regularly, heh. Most likely why there aren't ever any updates. I was about to start a new thread on my following question, but after reading your guy's posts, I'll post it here. 

When I do upgrade, I recieve the following output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils language-support-writing-en libbind9-30 libisccfg30
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
ado@ado-desktop ~ $ 

```

Why is it "keeping" these files back?

---

### Post by IusedTObeSOMEONEelse on 2008-09-07
Some times I do:
```
sudo apt-get dist-upgrade
```
after I do update

---

### Post by iaculallad on 2008-09-07
Installation package are kept-back because it involves system/configuration changing results. This action will modify other parts of the system. Try using the command below to do a "full-update" if you want to:

```
sudo aptitude dist-upgrade
```

---

### Post by adobrakic on 2008-09-07
thanks! :)

---


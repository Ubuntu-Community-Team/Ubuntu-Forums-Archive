---
title: "ncurses and config"
date: 2008-11-16
forum: Programming Talk
---

### Post by swappo1 on 2008-11-16
Hello,

I am trying to configure the linux kernel on an old computer that doesn't have intenet or network acces.  In order to #make menuconfig, I need to download ncurses-dev to a USB drive.  Is there a command to do this from the package manager?  Example apt-get <something> ncurses-dev.  Thanks

---

### Post by pdwerryhouse on 2008-11-18
You could try this:

```
apt-get --reinstall -d install libncurses5-dev
```

...and then you'll have to go fish it out of /var/cache/apt/archives/

-d makes it download only, and not install it
--reinstall forces it to download it if the computer you're on already has it installed.

---


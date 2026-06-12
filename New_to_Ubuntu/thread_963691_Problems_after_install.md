---
title: "Problems after install"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by bigbaws on 2008-10-30
Hi Guys, i am completely new to this forum and looking for some help.

I have just installed Ubuntu 8.04 and am having issues. It seems to have installed fine but when i choose Ubuntu from the boot manager all goes well until i am presented with the lof on screen.

I am presented with loads of white lines accross the screen and two mouse pointers.

Any ideas?

Thanks in advance

---

### Post by rockerphil on 2008-10-30
hm, that's an odd one. my advice would be to choose the recovery mode from the boot loader and let it do it's thing. also i'd let it attempt to fix the X server which is where i'm guessing the problem lies. if that doesn't work and if you know your system hardware pretty well i'd also run this command from the command line:

```
sudo dpkg-reconfigure xserver-xorg
```

hope this helps,

Phil

---


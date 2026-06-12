---
title: "Video card causing white out ?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by bikinguy77388 on 2008-07-10
Hi All,

I have just downloaded ubuntu and all went well until as the os suggested I enabled my video for 3d . I have a 256meg Radeon 9800pro. When I do this the screen turns white with just the mouse pointer showing. Earlier the same happened with kbuntu and I thought it was caused by the compiz package.

Any thoughts on this ?

---

### Post by LowSky on 2008-07-10
your Xorg.conf is messed up
restart in safe mode log in then type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---


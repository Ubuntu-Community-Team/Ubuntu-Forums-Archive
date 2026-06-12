---
title: "Dual Boot Screen"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by kc9fsh on 2013-03-17
I just installed Ubuntu, on my spare computer, it is installed my second hard drive and have it set-up as a dual boot system alongside Windows XP. Ran into a few issues but was able to resolve them by searching around online but the one issue I can't find a solution for is during the screen that would allow me to select Ubuntu or Windows XP my monitor comes up saying that it is a unsupported mode and won't show me anything for about 30 seconds until it boots to Ubuntu (by default I assume.) Is there a way to change some of the display settings at the dual boot screen?

---

### Post by DuckHook on 2013-03-17
Please post the output of:```
cat /etc/default/grub
```by enclosing in CODE tags (as I have) which can be used by highlighting all text and clicking hash (#) button at top of posting box.

---

### Post by fantab on 2013-03-18
What graphics do you have on your "spare computer"?
What is the 'Native Resolution' of your monitor?

Meanwhile you can:

```
$ gksu gedit /etc/default/grub
```

and EDIT the line which says *#GRUB_GFXMODE=640x480* to **GRUB_GFXMODE=1920x1080** ie, remove "#" in front of the line, if there is any, and change 640x480 to the native resolution of your monitor. Then,

```
$ sudo update-grub
```

See if it solves the issue. If not post the output of "cat /etc/default/grub".

---

### Post by kc9fsh on 2013-03-18
> **fantab said:**
> What graphics do you have on your "spare computer"?
What is the 'Native Resolution' of your monitor?

Meanwhile you can:

```
$ gksu gedit /etc/default/grub
```

and EDIT the line which says *#GRUB_GFXMODE=640x480* to **GRUB_GFXMODE=1920x1080** ie, remove "#" in front of the line, if there is any, and change 640x480 to the native resolution of your monitor. Then,

```
$ sudo update-grub
```

See if it solves the issue. If not post the output of "cat /etc/default/grub".

Thank you fantab! Setting that to my monitors native resoultion has fixed the issue.

---


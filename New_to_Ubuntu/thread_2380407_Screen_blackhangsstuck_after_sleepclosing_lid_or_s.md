---
title: "Screen black/hangs/stuck after sleep/closing lid or shutdown command via terminal"
date: 2017-12-17
forum: New to Ubuntu
---

### Post by senneverhaegen on 2017-12-17
**The problem:**
When I type shutdown in the terminal, the computer just freezes.
When i close the lid for a long time, the my laptop turns on but I only get a black screen. When i close the lid and reopen it immediatly it's not a black screen but everything is still stuck. (Can't move the mouse, can't execute commands with keyboard)


**About my laptop:**
32GB ram
Intel core i7-7700HQ CPU 2.8GHz x8
Intel HD Graphics 630 (Kaby Lake GT2) (says ubuntu but i have nvidia GTX 1050 TI)
I have installed ubuntu budgie. (Settings --> details --> overview say GNOME 3.26.2)


**What i have tried:**

There are a lot of posts about this problem and most of them are solved because they are old threads in older kernel versions. However i've still tried the methods described in those threads.


```
uname -r 
 "4.13.0-19-generic"

```

In /etc/default/grub I added "acpi=force" on the line with GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Setting --> privacy --> screen lock off






I also cannot get into a (text?) terminal by pressing ctrl+alt+f1,f2...


I think it has maybe something to do with lightdm or with graphics drivers, but i don't know where to go from here.

---


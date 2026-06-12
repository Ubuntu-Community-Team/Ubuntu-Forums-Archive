---
title: "new pc with ubuntu. display is playing up."
date: 2013-04-03
forum: New to Ubuntu
---

### Post by meeky1nz on 2013-04-03
i have just built a new pc and installed ubuntu(first time user) on it. The screen keeps going pixelated and now its showing up wrong. I have tried downloading the latest amd graphics drivers for linux but it hasnt done anything. 
I changed the driver in software sources/additional drivers/ from the open source, tested X.Org X server to the fglrx proprietary driver and it got rid of the pixelation but nothing would show up on my desktop.

I have a gigabyte 780t-usb3 mobo
radeon HD 6670 2gb gpu

im hanging out to be able to play with this thing but so far cant get it to work properly = frustrating.

any help would be awesome.

Chris

---

### Post by DuckHook on 2013-04-04
Hi and welcome to Ubuntu and the forums.

Just need some more info:

1. By "pixelation", are you referring to your 2nd attached image?

2. By "...nothing would show up on my desktop", are you saying that icons/dash/system panel are missing, or that application windows won't launch?

3. What driver and settings were you using when you produced the 1st attached image?

4. Did you try nomodeset on boot at any time using either the open-source radeon or proprietary fglrx?

5. You mentioned that you "tested X.Org X server to the fglrx proprietary driver" but I don't understand what this means. Did you change any settings in catalyst? If so, what did you change?

6. Assuming nomodeset gets you to even a simple working system, can you bring up a terminal using <Ctrl>+<Alt>+<t>? If you can, please post output of```
lspci -vk | grep -iA13 vga
``````
cat /etc/X11/xorg.conf
```

7. You have posted under "Ubuntu" but what Ubuntu version are you using? If you are actually using a different Ubuntu flavour, please tell us what it is?

8. Do:```
dmesg
``` to see if there is anything unusual. If you can't bring up a terminal within the GUI, then try <Ctrl>+<Alt>+<F1> instead. This will bring you to an command line shell with no GUI where you can also review dmesg. This log is long, so no need to post it all here. Just look through it to see if anything unusual pops out at you. If you do wish to post the output, remember to enclose it in "CODE" tags (hash marks at top of response box).

---


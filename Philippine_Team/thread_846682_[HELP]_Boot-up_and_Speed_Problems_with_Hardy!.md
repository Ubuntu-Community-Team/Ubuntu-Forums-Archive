---
title: "[HELP] Boot-up and Speed Problems with Hardy!"
date: 2008-07-01
forum: Philippine Team
---

### Post by echo2knight on 2008-07-01
Hi guys, could you please help me out with the following problems, to wit:

1. My Linux box ran at top speed when connected to the net, however, if the lan cable is not attached, it took forever for the machine to boot up. Plus the facts that each app that I ran, is crawling just to start up. (I did some tweaks, like prefetch, prelink and the likes just to make it start faster.)

2. Whenever I restart my l-box, the keyboard kept changing layouts, making the key assignments into SW, however, what makes it confusing is that I only installed USA-Default 105 keys in the keyboard settings.

3. I have an Intel GMA965 as my video and Intel HDA Sigmatel as sound. The driver seems to be installed properly, however, Im having video issues when running apps specially the ones using GL extensions and videos; the multimedia keys seems to be functioning, the volume adjusts as i use the Vol +,- yet there is no sound, even in the headphone jacks. Been searching different threads re this problem, to no avail. I hope someone here can help me.

Here's my Ubuntu Box Specs: Blue Stannum-EX, Intel Core2 Duo 1.6GHz, 14.1 WXGA, Intel GMA965 Chipset, 160G SATAHD, 4G RAM.

Many thanks!!!

---

### Post by saDDam kill me on 2008-07-01
> **echo2knight said:**
> Hi guys, could you please help me out with the following problems, to wit:

1. My Linux box ran at top speed when connected to the net, however, if the lan cable is not attached, it took forever for the machine to boot up. Plus the facts that each app that I ran, is crawling just to start up. (I did some tweaks, like prefetch, prelink and the likes just to make it start faster.)

2. Whenever I restart my l-box, the keyboard kept changing layouts, making the key assignments into SW, however, what makes it confusing is that I only installed USA-Default 105 keys in the keyboard settings.

3. I have an Intel GMA965 as my video and Intel HDA Sigmatel as sound. The driver seems to be installed properly, however, Im having video issues when running apps specially the ones using GL extensions and videos; the multimedia keys seems to be functioning, the volume adjusts as i use the Vol +,- yet there is no sound, even in the headphone jacks. Been searching different threads re this problem, to no avail. I hope someone here can help me.

Here's my Ubuntu Box Specs: Blue Stannum-EX, Intel Core2 Duo 1.6GHz, 14.1 WXGA, Intel GMA965 Chipset, 160G SATAHD, 4G RAM.

Many thanks!!!
try to reinstall your ubuntu.. if you install it correctly, there should be no problem. try to reinstall it first and see if you still encounter the same problem.

---

### Post by jeffimperial on 2008-07-02
> **saDDam kill me said:**
> try to reinstall your ubuntu.. if you install it correctly, there should be no problem. try to reinstall it first and see if you still encounter the same problem.
I too cannot provide anything as to the original poster's problems, but ^that^ sounds like a last resort.

---

### Post by echo2knight on 2008-07-02
> **saDDam kill me said:**
> try to reinstall your ubuntu.. if you install it correctly, there should be no problem. try to reinstall it first and see if you still encounter the same problem.

Reinstallation of Hardy is not in my options as of the moment. Anyway, with respect to my #1 concern...

I was able to find a solution to such. Since Linux is supposed to be networked, the system kept inquiring the NIC for a probable host address, which took some time to answer. The "loopback" is the culprit. I recalled renaming my host system. Hardy somehow failed to rename the loopback to its proper alias which is my host name. That is why my box was very sluggish because of the constant inquiry to the NIC without supplying the proper answer.

Well, I hope my other concerns can be resolved as fast as this one.

I really appreciate all you guys for the help!!!

---

### Post by echo2knight on 2008-07-02
Another thing guys, can someone instruct me how to disable the touchpad when you insert an usb mouse?

I know most of you experience this at one point in time when typing in a word processor, accidental touching of the touchpad moved the curser to a different position thus typing at a wrong part, producing errors, making you to retype it again.

So guys, kindly help me out. All infos will be very much appreciated! Thanks!

---

### Post by loell on 2008-07-02
#2

most probably a bug in xorg

[https://bugs.launchpad.net/ubuntu/+bug/225055]("https://bugs.launchpad.net/ubuntu/+bug/225055")

---


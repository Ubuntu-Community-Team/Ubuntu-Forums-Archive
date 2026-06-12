---
title: "(sigh) Newbie, wmp54gs, can't connect"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by Aqua009 on 2012-05-22
I'm fresh out of the box and used to OS's doing all my work for me.  But I have some knowledge of computers.

I have a Dell XP 32 bit.  I used Wubi to install Ubuntu.  When I restarted it, it just locked up in the first time run phase and never moved on.

I did a restart in ubuntu recovery mode and it looks like I needed a driver for my Linksys wmp54gs v1.4 card.

After searching around (for many hours), the best I could come up with was the need to install a ndiswrapper.  But I couldn't find a free program to install the .tar extension of this file.

Also on many help posts, I see the advise to enter commands in a "terminal".  How do you do that? Is that like opening a DOS window?

I am not lazy and have done numerous searches on trying to figure this stuff out.  I think I just need some guidance to get me on the track and I will be able to work out the rest of it.

Please... help me see the light!

---

### Post by wildmanne39 on 2012-05-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---


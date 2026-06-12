---
title: "Kernel panic after messing with Wifi card"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by jonasb2 on 2014-07-29
[SIZE=2][FONT=arial]So I have a [COLOR=#333333]rtl8723be wifi card which did work after updating to 3.13.0_32. But the connection drops now and then as also explained in this bug report:[/COLOR]

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070)

From there I tried the solution in #29
> [COLOR=#333333]I have tried the following on several kernels (under 12.04 and 14.04) and so far it has worked well :[/COLOR][COLOR=#333333]sudo apt-get install linux-headers-generic build-essential git
    # needed only if you don't have yet that package
git clone [http://github.com/lwfinger/rtl8723be](http://github.com/lwfinger/rtl8723be)
                           # needed only if you don't have yet downloaded rtl8723be[/COLOR]
[COLOR=#333333]cd rtl8723be
git checkout 604aa9058fb9e5bb1cf571c99989d081f8fc8b9
make clean
make[/COLOR]
[COLOR=#333333]sudo make install[/COLOR]
[COLOR=#333333]sudo modprobe rtl8723be[/COLOR]
[COLOR=#333333]echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf[/COLOR][COLOR=#333333][COLOR=#222222]

And after rebooting I ran into the Kernel panic #30 warned me for... so I can't boot normally now...

I did find out I had the option to boot in 3.13.0_24 so I tried that and it works. Doesn't even seem to detect a wireless card.

My question is:how do I fix my system? Can I somehow repair the damage I did? Or can I update this 3.13.0_24 somehow and pretend nothing happened? Or should I just reïnstall the whole OS and everything (it's not much yet)?

Edit: Here is some more info. I'm very new to Ubuntu/Linux. I'm using Ubuntu 14.04. And in the picures below you can see the messages I get when booting normally now:

[ATTACH=CONFIG]255158[/ATTACH][ATTACH=CONFIG]255157[/ATTACH]

Just in case the one line between the 2 pictures is important: it says "handle_irq_event +0x3d/0x60" :p.
[/COLOR][/COLOR][/FONT][/SIZE]

---

### Post by jonasb2 on 2014-07-31
Is nobody able to help me? Anythin more you need to know, or is my explanation confusing maybe?

---

### Post by MrSteve on 2014-07-31
please try removing the wifi card from the system 
then boot the system with the wifi card removed

this should clear the system

close the system down again then install the wifi card 
the system 'should' pick the card up and re-install as a new card ...

it worked on my system when i had wifi problems ...

---

### Post by jonasb2 on 2014-07-31
It's a laptop, I can't exactly remove the wifi card I'm afraid...

---

### Post by claracc on 2014-08-01
Perhaps your question would get a quicker answer if posted in the networking & wireless support subforum.

You can ask a moderator to move the post to the forementioned subforum.

---


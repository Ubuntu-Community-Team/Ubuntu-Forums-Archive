---
title: "Ubuntu slowed down my boot sequence"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2011-09-16
I haven't used Ubuntu in a while, as I removed my Ubuntu partition to make space for Windows to run. I'll definitely use Ubuntu in the future sometime, but right now I want to figure this out.

Before I had installed ubuntu, the white text that runs along the left of the screen would display for maybe a second or two, and then Windows would start to load. Now, it sits at that text for maybe 25 seconds or so, rather annoying. I'm thinking that ubuntu changed some setting for it to wait before booting? Is there a way for me to change the default time back to nothing? I have the program EasyBCD...could I use that to fix it?

I'm sorry for my vague description of what the text says, but I figure most of you know what I mean. If you need me to though, I could restart my pc and write down exactly what that jibberish says.

---

### Post by ajgreeny on 2011-09-16
Some of that time may be the default 10 seconds that the grub menu sits and waits before it boots, just in case you want to choose another OS.  That time can be easily reduced by editing a text file /etc/default/grub, where you need to change the line ```
GRUB_TIMEOUT=10
``` to a lower figure, eg 2 or 3.  Don't use 0 as that makes it difficult to choose any other OS from grub.

Exactly what the text that you see is will depend on the way your BIOS is set, along with many other factors, so it would be good to know a bit more detail of what you see.

---


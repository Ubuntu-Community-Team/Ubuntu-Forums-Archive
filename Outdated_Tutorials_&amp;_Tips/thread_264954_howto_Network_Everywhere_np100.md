---
title: "howto: Network Everywhere np100"
date: 2006-09-25
forum: Outdated Tutorials &amp; Tips
---

### Post by dmizer on 2006-09-25
to get the linksys/network everywhere fast ethernet 10/100 pcmcia network adapter model np100 working in dapper:

edit /etc/modprobe.d/blacklist:
```
sudo nano /etc/modprobe.d/blacklist
```
and add the following to the end of the file:
```
blacklist pcnet_cs
```
save by hitting ctrl+x, type y to save, and enter.

now restart the pcmcia daemon to implement the change:
```
sudo /etc/init.d/pcmciautils restart
```

reconnect the card, and you should see something like follows:
```
[17184248.780000] pccard: PCMCIA card inserted into slot 0
[17184248.780000] pcmcia: registering new device pcmcia0.0
[17184248.832000] eth0: Asix AX88190: io 0x300, irq 3, hw_addr 00:00:00:00:00:00
```

now use networking (or your preferred client) to configure your card as needed.

note:
i'd like to know if someone has a better way of doing this than blacklisting the pcnet_cs, as i'm sure there are other cards out there that need this module.

in the past (breezy) i had been successful in binding this card to axnet_cs by adding an entry to /etc/pcmcia/config.opts, but this is no longer functioning correctly.

i've also edited /etc/pcmcia/config to make sure that all AX88190 cards are listed as being bound to axnet_cs, also without success.

chime in if you've figured this one out on a deeper level :)

---

### Post by panda84 on 2008-03-22
> **dmizer said:**
> i'd like to know if someone has a better way of doing this than blacklisting the pcnet_cs, as i'm sure there are other cards out there that need this module.

Though the thread is quite old I think that there are still some people out there trying to figure this out. I spent some time to investigate this and, to make a long story short:

1) pcmcia-cs is deprecated since kernel 2.6.13, I think that, as of now, it is totally obsoleted. Its (partial) replacement is called pcmciautils;
2) card bindings are no more included in .config files in /etc/pcmcia as it was some time ago and are no longer managed by pcmciautils. **Card bindings are now included directly in the kernel!**;
3) several bindings are now fixed in the kernel but if you still receive the kernel message "pcnet_cs: use axnet_cs instead" during boot or card insertion then you should report the bug directly to the kernel team or contact pcmciautils developers in their mailing list. I did so and I discovered two interesting things: my card binding has just been fixed in kernel 2.6.24 (so it's never too late to fix a bug!) and that developers are still awaiting users to report wrong bindings!

You can figure out better the situation by reading this thread in pcmciautils mailing list:
[http://lists.infradead.org/pipermail/linux-pcmcia/2008-January/005305.html](http://lists.infradead.org/pipermail/linux-pcmcia/2008-January/005305.html)

If you still miss something don't hesitate to ask here!

Hope it helps,
Diego

---

### Post by swarup on 2008-07-07
Just an update for Hardy:

I have this np 100, and it works out of the box with Hardy. :) No need to do anything. Just works.

The first time I plugged it in, nothing happened. But then once I rebooted and tried it again, it sprang to life. And someone told me that this is often needed, in order for the card to get registered in your computer.

---


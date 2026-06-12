---
title: "Ubuntu 8.04 - NetworkManager issues - loosing settings"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by serid on 2008-05-24
Hi everyone !

I have been using Ubuntu since 6.04. The reason is it's stable and
allows me to use the system without difficult configuration.

I have just installed 8.04 and I have problem with NetworkManager.

1) Roaming mode works fine - ones set, I can reboot and it just works.
2) Manual settings - loosing setting every reboot.

Now as for manual setting - I tried to save my settings giving it
a name. It works partially - after reboot I don't have the network
on as I would expect it, but "at least" I can click on my saved
network setting and the connection comes back.

Is there a way to use manual configuration without a need to 
choose my saved configuration in NetworkManager every time I reboot ?


I searched through the forum, but couldn't find a solution which would
work on my machine:

Laptop VAIO VGN-SZ2XP/C - Intel 945GM chipset using iwl3945


Any help highly appreciated !

Adrian

---

### Post by mbaker824 on 2008-05-24
> **serid said:**
> 
I have just installed 8.04 and I have problem with NetworkManager.

1) Roaming mode works fine - ones set, I can reboot and it just works.
2) Manual settings - loosing setting every reboot.

Now as for manual setting - I tried to save my settings giving it
a name. It works partially - after reboot I don't have the network
on as I would expect it, but "at least" I can click on my saved
network setting and the connection comes back.

Is there a way to use manual configuration without a need to 
choose my saved configuration in NetworkManager every time I reboot ?

Adrian

Check the 8.04 release notes, where you'll find this:

> In Ubuntu 8.04, **network-manager only manages interfaces that are marked for roaming**. Thus, all interfaces that were previously managed by network-manager will be set to roaming mode during upgrade. Technically, this takes any interface stanzas using the dhcp method with no options and that are marked auto, and removes them from /etc/network/interfaces. If you rely on your interfaces being started by ifupdown when the system starts up, you need to re-enable them in /etc/network/interfaces manually, or disable roaming in System -> Administration -> Network

After disabling roaming mode in Network Manager, edit your interfaces file, which by default (in your situation) probably only starts up the loopback adapter.  Here's what mine looks like after modification:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
   address 192.168.1.101
   netmask 255.255.255.0
   broadcast 192.168.1.255
   gateway 192.168.1.1
   dns-search ph.cox.net
   dns-nameservers 68.105.28.11 68.105.29.11 68.105.28.12
```

After doing this the interface will be down.  You can either reboot or simply execute 'ifup eth0'. Run 'ifconfig -a' to make sure your settings are there.

Good Luck,
Mark

---

### Post by serid on 2008-05-28
Hi Mark,


Thanks for your reply.

Yes - I read that bit as well, but what I don't understand is why
when I manually edit that file and switch off the roaming mode
the setting still "are not remembered". Yes - they are saved
in the file, but network doesn't start by itself after reboot.

I haven't mentioned that it is wifi card.

Is there anything else I could check ? I mean it's not a big deal - 
it works with roaming, but just for curiosity ...


Cheers,

Adrian

---

### Post by mbaker824 on 2008-06-10
> **serid said:**
> 
I haven't mentioned that it is wifi card.


Ah, that's a horse of a different color.  Network Manager really is useful for wireless adapters, so I'd recommend keeping it.  I haven't tried to run a wireless adapter in Ubuntu without it, although it's no doubt possible.

Mark

---


---
title: "strange network DHCP client kicks in before static configuration is applied"
date: 2017-12-27
forum: New to Ubuntu
---

### Post by mam59 on 2017-12-27
Hi,
I'm rather new to Ubuntu/Linux, I'm more the BSD type...
Anyway I need to run some Ubuntu boxes/VMs to have some appliences running, that are only available for linux.

All works fine so far, but there is a nasty glitch I notice and that kept me searching for some days now (of course searching the web too, but I cant find anything close).

Maybe there is some kind of easys misconfiguration that I simply overlook?

Let me describe the symptoms:

* these boxes have more than one network card, eth0 is only used for management, eth1 should be used by the installed services (in this case: PiHole)
* eth0 should be IPV6 only!
* eth1 should handle V4 and V6
* both use static addresses

I configured /etc/network/interfaces accordingly and after a reboot, I was scratching my head.

Although NO config for V4 on eth0 was there, it automatically loaded one from the DHCP server of that segment!
Eth1 first looked fine (all static addresses applied) but a deeper look showed that it got a different gateway added, this also was read from a DHCP server!

So, obviously, although there is a static config only, it seems that on reboot it first asks for DHCP data, and afterwards it overwrites those values with the static ones configured in the interfaces file!

Thats no good!

I currently "resolved" the problem by adding a static v4 to eth0 too (one from a nonexisting net to send the packets to never-neverland), but then I noticed that I still am in deep trouble, because that unwanted DHCP requests trigger a dynamic DNS registration in the DHCP server. So the DNS Entries for the ubuntu machines are killed every reboot and get replaced by the address, it gets from the DHCP server (which is later on overwritten by the static config, but that one does not get updated into the DNS of course).

There is another nasty side effect from this "feature": it seems that any value that is present on the DHCP Server, but not in the static config, is not delete, but kept.

Currently I had to deny the Mac Addresses of the Ubuntu boxes in the DHCP Server to avoid this havoc! But I would not call this a "good solution"... (the "boxes" are VMs, their MAC may move if they are transfered or something)

So the urgent question is: "[B]how can I disable the DHCP client requests of the Ubuntu Boxes ???"
[/B]

---


---
title: "Manually IP Configuration on Virtualbox Server"
date: 2015-10-09
forum: New to Ubuntu
---

### Post by childerschase on 2015-10-09
Hello everyone,

For some reason this is really stumping me today. I've edited my /etc/network/interfaces file to match as below:

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 8.8.8.8

All requests both internally and externally return 'Destination Host Unreachable'

Obviously this is something simple I've messed up in my settings but I can't quite put my finger on it. Anyone have any suggestions to offer?
Thanks in advance.

[IMG]http://i.imgur.com/WOm5oU4.png[/IMG]

---

### Post by SeijiSensei on 2015-10-09
You probably need to use "bridged mode" for the virtual network adapter rather than the default "NAT mode." Look in Settings > Network for the VM.

---


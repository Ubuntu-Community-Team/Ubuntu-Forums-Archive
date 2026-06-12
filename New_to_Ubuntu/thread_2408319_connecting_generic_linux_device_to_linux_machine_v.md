---
title: "connecting generic linux device to linux machine via ethernet cable"
date: 2018-12-17
forum: New to Ubuntu
---

### Post by benjaminjcates on 2018-12-17
Greetings - Linux beginner here, and I would surely appreciate a nudge in the right direction.

I have connected a linux device to to my computer, and on the device i have:

 activated ethernet~  ifconfig eth0 192.168.135.2 netmask 255.255.255.0
started dropbear server ~ /etc/init.d/dropbear start

on my host linux machine i cannot successfully ping the device using the associated address. i can ping my own address, i can ping google. But when pinging the device It says "Network unreachable".

The ifconfig command on the device shows a small amount of Rx data, non-zero at least.

It just so happens that the device uses eth0, and my virtual machine running ubunto uses ens33. i've seen some methods for converting ens33 to eth0 (even did that at one point) but didn't solve the problem. Does this create any communication issue between the two?

Thank you very much in advance for your time and thoughtful wisdom,
Ben

---

### Post by jdeca57 on 2018-12-17
There are two possible issues:
your network is on a different subnet, say 192.168.1.2 and you won't reach 192.168.135.2, or
You mention VM. Virtualbox uses standard NAT, and that won't let you reach the 192.168.135.x. Use bridged adapter to do that.

---

### Post by benjaminjcates on 2018-12-17
Thanks very much for your two suggestions. With respect to #1 the VM is on 192.168.135.50 and the device eth0 was setup to be 192.168.135.2 .  I am using VMware. Do i need to investigate a bridged adapter for that case as well?

Ben

---

### Post by ubname on 2018-12-17
Yes, you'll ned a bridged adapter with vmware as well.
Just select bridge instead of NAT for your Virtual Machine network card configuration in vmware.

---


---
title: "If I change the name of the network card, the computer will not be able to access the"
date: 2020-07-12
forum: New to Ubuntu
---

### Post by rostds on 2020-07-12
ubuntu 18.04 lts


Network card name: xw001, changed to eth3.

[COLOR=#222222][FONT=Verdana]sudo ip link set  xw001  down                   [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]sudo ip link set  xw001   name  eth3             [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]sudo ip link set  eth3  up   
[/FONT][/COLOR]

Can't the computer connect to the Internet?

[ATTACH=CONFIG]286459[/ATTACH]

---

### Post by ActionParsnip on 2020-07-13
did you change any netplan rules to affect the NIC on its new name?
Did you get the NIC to re-request DHCP?
Can you ping the default gateway?
Can you ping your DNS servers?
Can you ping 8.8.8.8?
Can you ping bbc.co.uk?

Also, why change the name? It doesn't affect anything........

---


---
title: "Can Internet but not local net"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by n.brenner on 2011-10-21
After much hand wringing and rebooting, several new installs,
I TRACKED IT DOWN......It seems, after the first update, something
came across the update that shut my 10 Machine network and servers 
down from LOCAL NETWORKING......AARRGH

Found the CULPRIT.....

open /etc/hosts and comment out 2 of the IPV6 lines.

/etc/hosts
]
]
#The following lines are desirable for Ipv6 capable hosts
;;1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
fe00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts          #this one may not be there, add it if it isn't

comment out these lines

]
]
#ff02::1 ip6-allnodes
#ff02::2 ip6 -allrouters

It was amazing behind the router....everything worked..YEA

My router uses MAC address for local ip designation ie:  MAC address 00:00:00:00:00 = 192.168.1.1xx

---


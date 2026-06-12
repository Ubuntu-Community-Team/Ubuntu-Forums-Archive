---
title: "VPN status in conky"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by MikeJParry on 2011-12-07
hello, I'm new with Ubuntu and google has not helped me much with this issue.
I would like to have in this conky the VPN status so I would know if is down or up at a glance.
any suggestions would be welcomed :popcorn:

---

### Post by editheraven on 2011-12-07
Try this.

```
if_up     (interface)     
if INTERFACE exists and is up, display everything between $if_up and the matching $endif
```

Example

```
${if_up ppp0}Up${else}Down$endif
```

---

### Post by MikeJParry on 2011-12-07
Thanks for the quick answer but now I'm stuck again.
The ppp0 dose not work for me, I tryed with 1,2,3 but still it reports as down.
In the network manager it says I'm connected but I can't figure what the network should be, for eth0 works fine ?
Any way I can check witch interface I use ?

---

### Post by MikeJParry on 2011-12-07
Solved and thanks again,
I found the interface with **ifconfig** and the code for OpenVPN should be :
```
${if_up tun0}Up${else}Down$endif
```

---


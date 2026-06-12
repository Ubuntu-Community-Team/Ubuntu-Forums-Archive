---
title: "Error when remove the older version of a single kernel module"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by ymsaputra on 2013-02-18
Dear All,

I have a problem to activate new module. So I try to modify one file in mac80211 module and it will successfully be compiled until copy the new .ko file to my running kernel module /lib/modules/3.5.0/kernel/net/mac80211.

But when I try to remove the older module, it is said

> 
% rmmod mac80211

ERROR : Module mac80211 is in use by carl9170, iwlwifi


Do you know how to fix this error? so I can remove the older module and change with new module?

If the new module is successfully installed -> modprobe -v mac80211, it will display
> 

insmod /lib/modules/.../mac80211.ko



but i don't see this message because there is error in removing older module.

Thank you for the answers

---

### Post by tgalati4 on 2013-02-18
Try removing carl9170 and iwlwifi first, then remove mac80211.

---


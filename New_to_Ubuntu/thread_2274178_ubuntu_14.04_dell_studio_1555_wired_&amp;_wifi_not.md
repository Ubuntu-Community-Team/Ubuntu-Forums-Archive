---
title: "ubuntu 14.04 dell studio 1555 wired &amp; wifi not working"
date: 2015-04-18
forum: New to Ubuntu
---

### Post by deepak26 on 2015-04-18
just changed to ubuntu 14.04 from windows. in my previous experience with ubuntu (some earlier version) it would automatically detect the internet. I tried through ethernet port but even that is not detecting the internet for me to update drivers for wifi. while I was on windows both wired and wireless were working perfectly fine.
please help 

deepak

---

### Post by uxbal on 2015-04-18
Hi!

Could you please provide some more information, f.ex. have you tried the following:
- using hotkeys on your keyboard to turn on / off wifi card
- scanning for additional drivers in ubuntu itself
- what model is your wifi card?

Kind regards,

---

### Post by deepak26 on 2015-04-18
[QUOTE=uxbal;13267372]Hi!

thanks uxbal for the reply.
I don't seem to have turned the keys off. I checked it by pressing it several times after seeing your reply. it does not seem to be working.
please tell me how to search for drivers within ubuntu as i can not update anything for my Internet connection is not working with wire or wifi. when I attache the ethernet cable I see some activity on the internet symbol at the write top - then I get the message you connection is turned off. ..
the wifi card is Dell 1397 802.11 B/G wireless mini card

deepak

---

### Post by wildmanne39 on 2015-04-18
Please post the output of:
```
lspci -nnk | grep -iA2 net
```
and use code tags, directions for using code tags is in my signature.
Thanks

---


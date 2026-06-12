---
title: "Slow Ubuntu 12.04.4 boot on ASUS X53E / fresh install"
date: 2014-04-12
forum: New to Ubuntu
---

### Post by jesipr on 2014-04-12
I have two computers my Acer Aspire 5734Z running Ubuntu 13.10 without any problems and my ASUS X53E with a fresh install of Ubunutu 12.04.4 LTS (After trying to install Ubuntu 13.10 with no luck) that is giving me boot problems.The problem is that the computer is taking like two minutes to boot and sometimes it doesn't even boot. I did a search and did a dmesg which returned this [http://pastebin.com/pxKAFKZF](http://pastebin.com/pxKAFKZF). I can see that the problem is in one of this lines:


[LIST=1]
[*][COLOR=#000000][   14.074387] Bluetooth: RFCOMM ver 1.11[/COLOR]
[*][COLOR=#000000][   90.168188] audit_printk_skb: 3 callbacks suppressed
[/COLOR]
[/LIST]

I have looked for "audit_printk_skb" in Google and in this forum with no luck.
My question is, what can I do? Right now the computer won't boot but I could try re-installing Ubuntu 12.04 but I'm pretty sure it will remain the same. The computer has intel Core i5. It has a USB 3.0 port. It came with Windows 7.

---


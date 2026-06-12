---
title: "about security"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by yoyohoney720 on 2013-06-04
Hiii.
please someone tell me is there a inbuilt Firewall option for Ubuntu 12.04 lts , like in Windows.
please reply.:confused:

---

### Post by slickymaster on 2013-06-04
Yes there is. Check it [here]("https://help.ubuntu.com/community/UFW").

Edit: Be welcome to the forums.

---

### Post by matt_symes on 2013-06-04
Hi

There's an inbuilt firewall in the kernel called netfilter.

Netfilter is configured by a series of rules using IPtables.

There is a graphical front end called gufw. You can install this and configure the firewall.

There is another graphical front end called firestarter that can be used to configure the firewall, however i keep reading that this is not much maintained anymore. I can offer no information about that though as i don't use firestarter.

Ubuntu does not come with many open ports though, so you may not need a firewall - depedning on how you use your system

Do you want to configure the firewall on a server or a desktop/laptop machine ?

Kind regards

---

### Post by 3rdalbum on 2013-06-04
> **yoyohoney720 said:**
> Hiii.
please someone tell me is there a inbuilt Firewall option for Ubuntu 12.04 lts , like in Windows.
please reply.:confused:

Yes, there is, but most people these days are firewalled anyway by their modem.

Ubuntu comes with no services that listen to incoming ports from the internet (only to internal network connections) so all in all, the vast majority of people find it completely unnecessary to set up Ubuntu's firewall.

I don't use Ubuntu's firewall and I connect to the internet via 3G - and no problems yet. (I've been doing this for nearly a year).

---


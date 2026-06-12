---
title: "Uninstalling Guarddog Firewall"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Sarah L on 2008-09-16
Hi,
I've used [Guarddog]("http://www.simonzone.com/software/guarddog/") for quite some time now and I've found it to be too inconvenient for my purposes. I'd like to be able to uninstall Guarddog and restore my network settings to Kubuntu defaults. I'm not sure if sudo apt-get purge guarddog will be able to do this as Guarddog has modified some rules in iptables.

Does anyone have suggestions?

Thanks,
Sarah

---

### Post by nowshining on 2008-09-16
just an uninstall should work fine and remove any iptables rules, if not then u'll need to manually flush them..

---

### Post by Sarah L on 2008-09-18
Sorry, but this doesn't answer my question......

---

### Post by bodhi.zazen on 2008-09-18
apt-get purge is the key.

Then either re-start iptables or reboot.

---


---
title: "&quot;Stopping the firestarter firewall...done"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Andavane on 2008-06-09
Starting the firestarter firewall...fail!"

This is the dialogue I get in the booting sequence.
have often wondered about it.

What does it actually mean?
Does it mean I have a problem?

Regards

John

---

### Post by jbrown96 on 2008-06-09
I believe that it fails because there is no active network connection at the time. Firestarter will only work if it has a connection; and not just any connection but the one you specified in its configuration.
I used to use firestarter but it always displayed that message and never seemed to start once networking came up. I now use UFW, which doesn't have the nice logging features (afaik) and can't do internet forwarding but it's much easier to use

---

### Post by hyper_ch on 2008-06-09
FIRESTARTER IS NOT A FIREWALL!

It's just a configuration tool for iptables and iptables is built into the kernel. I think for some reason you have firestarter on autostart during bootup before xserver runs.

---


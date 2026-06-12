---
title: "[SOLVED] Cupsd Warning..."
date: 2008-07-12
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-07-12
Jul 13 10:32:29 PJ cupsd[5083]: *** WARNING *** The program 'cupsd' uses the Apple Bonjour compatibility layer of Avahi.
Jul 13 10:32:29 PJ cupsd[5083]: *** WARNING *** Please fix your application to use the native API of Avahi!
Jul 13 10:32:29 PJ cupsd[5083]: *** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd>
Jul 13 10:32:30 PJ kernel: [   55.200305] audit(1215901950.037:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5083 profile="/usr/sbin/cupsd" namespace="default"
Jul 13 10:32:30 PJ kernel: [  111.137798] Marking TSC unstable due to: cpufreq changes.

Even after going to the suggested website, I am not wiser on what I should be doing if anything...

---

### Post by alienexplorers on 2008-07-12
I was getting the same error when I set up my printer.  I found that it was a bad USB port.  I got a new 2,0 card and the problem corrected itself.

---

### Post by brian_p on 2008-07-13
> **dunbrokin said:**
> 
Even after going to the suggested website, I am not wiser on what I should be doing if anything...

Basically, cupdsd uses avahi in a way the cups developers would prefer it not to. They will not fix this. The warning is harmless.

[https://answers.launchpad.net/ubuntu/+question/27131](https://answers.launchpad.net/ubuntu/+question/27131)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=451562](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=451562)

---


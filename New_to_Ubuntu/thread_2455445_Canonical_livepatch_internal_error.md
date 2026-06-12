---
title: "Canonical livepatch internal error"
date: 2020-12-19
forum: New to Ubuntu
---

### Post by kaamilmirza on 2020-12-19
When the live patch is on its showing and error
"Canonical Livepatch has experienced an internal error. Please refer to [https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues](https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues) for further information."
I tried disabling and re-enabling it, I tried reboot, I tried getting a new token and rebooting, buts its not working.

Here are the logs

ec 19 23:42:55 kaamil-HP-Laptop-14s-fr0xxx systemd[1]: Mounting Mount unit for canonical-livepatch, revision 95...
Dec 19 23:42:55 kaamil-HP-Laptop-14s-fr0xxx systemd[1]: Mounted Mount unit for canonical-livepatch, revision 95.
Dec 19 23:42:56 kaamil-HP-Laptop-14s-fr0xxx kernel: [  849.874333] audit: type=1400 audit(1608401576.219:1719): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.canonical-livepatch" pid=5903 comm="apparmor_parser"
Dec 19 23:42:56 kaamil-HP-Laptop-14s-fr0xxx kernel: [  849.959341] audit: type=1400 audit(1608401576.307:1720): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatchd" pid=5905 comm="apparmor_parser"
Dec 19 23:42:56 kaamil-HP-Laptop-14s-fr0xxx kernel: [  850.006717] audit: type=1400 audit(1608401576.351:1721): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatch" pid=5904 comm="apparmor_parser"
Dec 19 23:42:56 kaamil-HP-Laptop-14s-fr0xxx kernel: [  850.011483] audit: type=1400 audit(1608401576.359:1722): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.canonical-livepatch.hook.configure" pid=5906 comm="apparmor_parser"
Dec 19 23:42:58 kaamil-HP-Laptop-14s-fr0xxx kernel: [  852.258639] audit: type=1400 audit(1608401578.603:1726): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.canonical-livepatch.hook.configure" pid=5996 comm="apparmor_parser"
Dec 19 23:42:58 kaamil-HP-Laptop-14s-fr0xxx kernel: [  852.403899] audit: type=1400 audit(1608401578.751:1727): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatch" pid=5994 comm="apparmor_parser"
Dec 19 23:42:58 kaamil-HP-Laptop-14s-fr0xxx kernel: [  852.408113] audit: type=1400 audit(1608401578.755:1728): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatchd" pid=5995 comm="apparmor_parser"
Dec 19 23:42:58 kaamil-HP-Laptop-14s-fr0xxx systemd[1]: Started Service for snap

---

### Post by CelticWarrior on 2020-12-19
Welcome.

Wait a day or two.
If you're installing updates regularly you don't really need Livepatch.

---


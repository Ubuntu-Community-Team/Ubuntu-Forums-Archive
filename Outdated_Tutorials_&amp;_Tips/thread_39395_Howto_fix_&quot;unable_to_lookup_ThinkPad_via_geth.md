---
title: "Howto fix &quot;unable to lookup ThinkPad via gethostbyname()&quot; error"
date: 2005-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by jcs296 on 2005-06-04
Okay, I found the solution.  That post you referenced has the right idea (edit /etc/hosts) but doesn't say what to do:

1) reboot into rescue mode (at the grub boot menu hit Escape, select the rescue/recovery mode). This gives you a root shell without requiring a password.

2) cp /etc/hosts /etc/hosts.backup

3) enter 'vim /etc/hosts' (or nano/pico, whatever console editor you like), and edit the line:
127.0.0.1 localhost 
to be:
127.0.0.1 localhost yourhostname

where 'yourhostname' is the hostname you entered during install.

Alternatively, you can make these separate lines:
127.0.0.1 localhost
127.0.0.1 yourhostname

4) save the file, and reboot. problem should now be fixed.  If you have problems with postfix (you may notice at shutdown that it gives an error as the text scrolls by), it is related to this but I don't know how to fix it.  

Hope this helps,
Joe

---


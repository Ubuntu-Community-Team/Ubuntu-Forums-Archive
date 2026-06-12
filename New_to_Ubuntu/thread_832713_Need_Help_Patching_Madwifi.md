---
title: "Need Help Patching Madwifi"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by shaggy1054 on 2008-06-18
Hey all, 

I've been having trouble with madwifi and wireless connectivity ever since the -16 to -17 kernel update. It's taken a while for me to figure things out, but I think I've found somewhat of a solution here: 

[http://madwifi.org/ticket/705](http://madwifi.org/ticket/705)

Accordingly, I downloaded the ani_sensitivity_fix_v2.diff patch. However, I have no idea of how to actually apply this patch. Could someone maybe help me out here? Much thanks in advance.

---

### Post by shaggy1054 on 2008-06-18
*bump* for help please

---

### Post by shaggy1054 on 2008-06-18
Alright, one last bump. Please guys, I just need to know what directory to put this in, or what script to run, or what to type into the terminal.

---

### Post by mond0 on 2008-06-26
I have the same problem.  Don't know how to use a simple .patch file.  I tried looking around online learning about them, but I still dont know exactly how they work.  I got one to patch my mac80211 stack, but.. i look for the target file "tx.c" on my computer and cant find it, and don't know how to use the patch :(

---

### Post by doddi on 2008-06-26
never done patches either but simple google returned this [http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

use the patch coammnd should do the trick

---

### Post by shae on 2008-06-27
That patch is either in the kernel or in the madwifi driver.  Check the respective sources for that file.  Let me know which it is in.

---


---
title: "VMWARE Problem when /tmp is ram"
date: 2008-08-24
forum: Philippine Team
---

### Post by Recursion_1209 on 2008-08-24
I was trying to add the below lines to /etc/fstab:

tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
tmpfs /var/log/apt tmpfs defaults,noatime 0 0

I have 2GB of ram so I would to use some of it to speed up some applications using this directories. But, when I tried running VMWARE it won't start. It just hangs and nothing happens.

Anyone have any suggestion?

---

### Post by insane_alien on 2008-08-24
first off, /tmp in a ram disk will likely slow down your system more than any speed up. if the files in /tmp are use alot then they will be cached in ram anyway so you would be using twice the ram for the same stuff with no speed up.

solution is to take /tmp out of ram.

---

### Post by Recursion_1209 on 2008-08-27
I didn't know that. I thought it will speed it up. Thanks for the tip.

---

### Post by insane_alien on 2008-08-27
yeah, just remember, the kernel is better at managing RAM than you are, overriding the kernel tends to result in more swapping and system slowdowns under heavy load.

---


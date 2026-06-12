---
title: "[SOLVED] A grep question"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by unutbu on 2008-07-03
/etc/event.d/rc-default has a very interesting line:
```

	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
```
This tells the machine what to do if the word "single" is placed in the GRUB boot command.
But what does "-s\|" and "\|S" mean?

---

### Post by sisco311 on 2008-07-03
\| = or
The command tells what to do if "-s" or "single" or "S" is placed in the GRUB boot command.

---

### Post by unutbu on 2008-07-03
Thank you so much, sisco311. Would you happen to also know the answer to this question:

[http://ubuntuforums.org/showthread.php?t=846380](http://ubuntuforums.org/showthread.php?t=846380)

---


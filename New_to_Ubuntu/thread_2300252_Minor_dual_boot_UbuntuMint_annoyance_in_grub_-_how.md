---
title: "Minor dual boot Ubuntu/Mint annoyance in grub - how do I fix this?"
date: 2015-10-24
forum: New to Ubuntu
---

### Post by Ian_Scott on 2015-10-24
I have a HP Pavilion dv6 notebook that now dual boots Ubuntu 15.10 and Mint Cinnamon. However on boot, it defaults to "advanced options..." when I had hoped to boot at Ubuntu. How do I fix this - I am sure the solution is simple. I looked at /etc/default and sudo su then gedit grub from a terminal. The code was

GRUB_DEFAULT=1
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

I had the first line as 0 and changed it to 1 as shown, rebooted, used the default advanced options and rebooted - no change. Any suggests welcome:p

---

### Post by yancek on 2015-10-24
The line you need to change is the one below which is set to boot the second entry in the grub.cfg menu file.

> 
GRUB_DEFAULT=1

In this instance, Grub counts from zero so if you want the first menuentry to boot by default, change the 1 to a 0.  If you want something else you will just need to count down the menuentries to the one you want and enter that number.  When you have done that, run sudo update-grub.

---

### Post by Ian_Scott on 2015-10-24
Hi jancek

Thanks for the explanation. I changed the 1 back to 0 now and all is now hunk-dory - although I'm not sure why it played up the first time. Perhaps a notebook glitch?

---


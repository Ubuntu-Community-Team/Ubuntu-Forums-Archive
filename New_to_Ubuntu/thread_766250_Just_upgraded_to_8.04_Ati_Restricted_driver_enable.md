---
title: "Just upgraded to 8.04 Ati Restricted driver enabled but not in use?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Eastisle on 2008-04-25
I just finished the upgrade from Gutsy to Hardy. When going to Hardware Drivers window, my ATI driver shows up as enabled but status is displayed as "not in use". It used to work fine in Gutsy, anyone else having the same problem? 

How can I fix it? The slow choppy display is unbearable, help please.

---

### Post by sloggerkhan on 2008-04-25
did you reboot after re-enabling the driver?

It might be that you should have disabled the proprietary driver before upgrading or something.

---

### Post by Eastisle on 2008-04-25
Yes, I did reboot.

In fact, I had the driver disabled when I did the upgrade.

Thanks for the help, any other ideas?

---

### Post by mister_pink on 2008-04-25
This happened to me at some point, I thought it was a bit odd. Can't really remember how I fixed it, but I think it involved turning it off, rebooting, turn it on, reboot again. I might have actually manually uninstalled the packages rather than turning it off though.

---

### Post by Eastisle on 2008-04-25
Good to know you fixed it. I've rebooted more than a couple of times and just disabled and re-enabled the driver, but no effect.

---

### Post by mister_pink on 2008-04-25
Not really sure what to suggest I'm afraid. It's quite easy to make these things far worse if you're not careful/lucky. I'll tentitively suggest removing it manually, rebooting and enabling it.
sudo apt-get remove xorg-driver-fglrx

---

### Post by Ub1476 on 2008-04-25
Make sure the repos are checked in Software Sources, then check the driver and restart X: Control+alt+backspace.

---

### Post by Eastisle on 2008-04-25
Thanks for the responses. I have everything working now. I manually installed the driver and some other things I didn't keep track of, and then it just worked after a couple of tries. :)

---

### Post by autocrosser on 2008-04-25
Take a look in the closed Hardy testing forum--there is a bug report you need to send info to---several of us had this problem-within the last couple of weeks............Thanks!!

---


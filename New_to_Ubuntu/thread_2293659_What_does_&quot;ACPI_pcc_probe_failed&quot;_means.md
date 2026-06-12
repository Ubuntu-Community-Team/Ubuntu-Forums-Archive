---
title: "What does &quot;ACPI pcc probe failed&quot; means?"
date: 2015-09-06
forum: New to Ubuntu
---

### Post by Austin_Muckelrath on 2015-09-06
Whenever I boot up Ubuntu, it keeps on popping up with a black screen stating "ACPI pcc probe failed" for, like, 5 seconds, then it loads up Ubuntu afterwards. It only takes 15-20 seconds to boot up, even with that pop up. I never had any issues with Ubuntu, everything about it just works right out of the box. But I never understood what "ACPI Pcc probe failed" means. I'm pretty sure it's just a glitch to the OS, right?

---

### Post by tristan16 on 2015-09-06
From what I've found, it's more of an info message than an error. Basically, if the PCC driver can't find any PCC hardware, the probe fails (because there's nothing to probe). I don't see it on every boot, and it doesn't seem to have any effect.

You can find more from a Google search, or just from this thread I found: [https://askubuntu.com/questions/584248/boot-error-acpi-pcc-probe-failed](https://askubuntu.com/questions/584248/boot-error-acpi-pcc-probe-failed)

---

### Post by grahammechanical on 2015-09-06
There is a bug report for it. Look for comment #15 which explains what is causing this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1430625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1430625)

When you upgrade to 15.10 you will not see that message.

Regards.

---

### Post by Austin_Muckelrath on 2015-09-06
> **grahammechanical said:**
> There is a bug report for it. Look for comment #15 which explains what is causing this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1430625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1430625)

When you upgrade to 15.10 you will not see that message.

Regards.

"PCC (Platform  Communication Channel)  is a recent ACPI 5.0 addition. The driver does  not find a PCC communications mailbox and just exits with that error  message.  It is not something to worry about, most machines don't have  an ACPI PCCT table and they don't use this mechanism.
 References: ACPI specification Chapter 14.0 "Platform Communications Channel"

 Linux source: drivers/mailbox/pcc.c


              
 


In other words, I have nothing to worry about?

---

### Post by brian-mccumber on 2015-09-06
Yes nothing to worry about. This error kept popping up on my desktop, I just edited the grub to turn off the splash screen and now it goes by so fast I don't even notice it anymore, hehe. I only did this after an extensive search on the error and I found out it's just for hardware my desktop doesn't have it was added to the distro because Ubuntu is going mobile. When I edited grub to not use the splash I get to see the terminal output while Ubuntu is booting which is fine because purple is not one of my favourite colors anyway.

---

### Post by Austin_Muckelrath on 2015-09-07
Aw, now I get it. Thank god it's nothing serious! I've been using Ubuntu for the past month, on my custom-rig desktop, and it's been a great secondary operating system. I had Windows 10 installed (mainly for gaming and Adobe suites) and I'm not happy with the direction Microsoft is heading with it. So instead, I dual-booted Ubuntu (32GB partition out of 1TB) and I love it so much. I'm still new to Linux/Ubuntu, but I'm still trying to learn it and - oh, you know - understand the terminal a little bit. :P

Thanks for the help, guys!

---


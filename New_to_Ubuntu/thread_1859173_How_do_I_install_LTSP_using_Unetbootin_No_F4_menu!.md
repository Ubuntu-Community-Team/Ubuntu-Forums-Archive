---
title: "How do I install LTSP using Unetbootin? No F4 menu!"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by doctorbighands on 2011-10-13
I couldn't get Startup Disk Creator to work properly, so I had to use Unetbootin to make a bootable USB stick.

The goal with this USB stick is to build an LTSP server on a 1U machine I have. The problem is that the F4 option you normally get at boot time doesn't exist! I can modify the boot string with Unetbootin, but I have no idea what I'd put in there to run the usual automatic LTSP install.

Help!

---

### Post by doctorbighands on 2011-10-13
Okay, so I dodged the original problem by using a third computer. On that machine, Startup Disk Creator worked fine. Go figure.

Now, I have a new problem!

I'm in the process of installing the LTSP server on the target machine, and it's halted with a message that reads something like, "Please insert the disk labeled Ubuntu 11.04 - media change". This doesn't make sense, because I'm not using CD media for the installation. If this were happening after the install was done, I know I'd simply comment out the appropriate line in my sources.list file, but what do I do now that it's happened DURING the installation? Clicking "Continue" just puts the alert window right back up, and I don't see a way around it - it's like it's stuck in an infinite loop.

Help!!

---


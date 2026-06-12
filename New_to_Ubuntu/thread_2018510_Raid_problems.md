---
title: "Raid problems"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by Slimmons on 2012-07-06
I've been looking for a while into some errors I've had with Ubuntu and setting up a Raid 0 on two 1tb WD caviar blacks.  Most of what I've found says to just do a software raid, but I'd really rather not do that.  The issue I'm having is that I set up the hardware raid, install Ubuntu as raid0, and it completes successfully, then when it restarts, it always says, grub not loaded, and won't recognize any commands I do.  I've been told to use the alternate download, and do software raid......any other options?

---

### Post by Gone fishing on 2012-07-06
There are hardware raids and hardware raids a proper hardware raid I would have thought should be no problem the OS will just see it as a disk. However, the hardware raids that come with mother boards are not usually true hardware raids and can be a problem.

However, I used raid1 with mdadm and it was good.

---

### Post by |{urse on 2012-07-06
Are these gpt?

[http://www.shuvoovuhs.com/linux/grub-installation-issue-with-2-tb-hdd-gpt-requires-bios-boot-partition/](http://www.shuvoovuhs.com/linux/grub-installation-issue-with-2-tb-hdd-gpt-requires-bios-boot-partition/)

---

### Post by Slimmons on 2012-07-06
Hey, and thanks for responding so quickly, the advice about hardware raid, and true hardware/fake hardware raid made me go look at the difference more closely, and the link to the large HDD raid grub installer failure helped a lot.  I'm sure that's the key to fixing this is the installer partitions.  Thanks for the help, I'll let you know if that didn't fix it, but now that I see it's not an actually problem with software/hardware, and more of a problem with how I was doing it, I should be able to fix., thanks a lot!

---


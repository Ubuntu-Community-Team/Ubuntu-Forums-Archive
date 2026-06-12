---
title: "Upgrading to 2.6.24-22 Breaks my System"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by jeff_clough on 2008-12-01
I'm was running 2.6.24-21 generic this morning and noticed a lot of updates when I signed on. So I took the updates recommended by the update manager, as usual, which included a kernel upgrade to 2.6.24-22. (I *think* I'm getting those numbers right. That computer won't talk to me at the moment.) Upon restart, my computer wouldn't boot. I don't even see a grub message. The BIOS screen goes away, and I'm looking at a blinking cursor. Pressing keys does nothing.

Having no other ideas, and with my home directory safely on a separate drive, I reinstalled 8.04 from CD and again took the updates. Same result.

So have the standard repositories failed me? Is there a solution that doesn't involve reinstalling everything from scratch and never taking another update?

Thanks for any advise.

--Jeff

---

### Post by jeff_clough on 2008-12-01
:oops:Well crap! Sometimes I'm just a complete noob.

30 seconds after posting my question, and after trashing practically the whole day on this problem, it occurred to me that I'd been playing with booting from USB devices (which I never got to work) last week, and today is the first time I've had to reboot after that. My BIOS was trying to boot from a USB attached drive, which is in now way bootable! Yes! I'm an utter moron. Now that I've reconfigured by BIOS to boot from the hard drive, everything's fine.

For the record, I do hereby apologize to the package managers for implying that installing the new kernel broke my system. This was completely untrue, and further, I broke my *own* system without any help from Ubuntu or the Ubuntu community.

Thank you for your time, and I will endeavor henceforth never to waste it again.

--Jeff

---


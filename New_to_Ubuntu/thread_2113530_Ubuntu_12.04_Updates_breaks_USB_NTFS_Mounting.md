---
title: "Ubuntu 12.04 Updates breaks USB NTFS Mounting?"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by pablolie on 2013-02-07
I have 12.04 on a standard Intel cpu-mobo. It isnalled easily and runs well.

But with 12.04, I have now *twice* seen that a regular software update "unmounts" the external USB NTFS drive. It is a WD "MyPassport 0730".

The odd thing is that the fstab is untouched. The drive just doiesn't mount after the update. It seems to happen when the update includes a new Linux kernel. My suspicion is that the resulting restart hasn't properly shut down the external drive, and hence the issue until it is mounted again.

Not sure if anyone else has observed this in 12.04 - I can't recall it happening in 8.0x or 10.0x (I mostly do LTS).

This is meant as feedback to the developer community, in case other users have noticed this phenomenon in 12.04.

And thanks to the developers for a wonderful OS I benefit from. :)

---

### Post by Cheesemill on 2013-02-07
> **pablolie said:**
> This is meant as feedback to the developer community, in case other users have noticed this phenomenon in 12.04.
The developers don't usually visit this site.

You should post a bug on Launchpad if you want to get this issue looked at.

[https://launchpad.net/](https://launchpad.net/)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by -kg- on 2013-02-07
One thing I can say is that I have 12.04 installed on my desktop, and I've never experienced the problem.

Another thing I can say is that it isn't a kernel update that's at fault.  When you update the Linux kernel, it won't unmount anything.  In fact, the new kernel won't be running; your system will still be using the old kernel until you reboot, at which point the default entry in the GRUB menu will launch the new kernel.

I can't imagine what's causing the problem, but thought I'd tell you that it isn't a kernel update, but something else.

---


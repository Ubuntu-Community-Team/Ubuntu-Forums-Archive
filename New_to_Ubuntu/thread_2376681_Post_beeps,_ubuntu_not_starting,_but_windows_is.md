---
title: "Post beeps, ubuntu not starting, but windows is"
date: 2017-11-04
forum: New to Ubuntu
---

### Post by crip720 on 2017-11-04
Have an Acer aspire 5536 that is giving post beeps. I think they are 1-3-2-2/or 1-3-4.  Ubuntu 14.04 will give a page or two of ^[[3 with libcypt about half page down on page one, then seems to give pages of starting/stopping processes with 'ok'. Might be looping. Ubuntu does not boot to desk top. Windows 7 and Windows 10 will boot up well.  All OSs are needing updates for last three or four months,from when Win 7 and ubuntu were updated last, Win10 was not updated.  Just play with Windows, but use Ubuntu.  Any ideas on what I can do, it is a secondary laptop not been booted up for three months.  Any infomation you need will have to come from Windows OS

---

### Post by william.hua on 2017-11-05
Look for a "Secure Boot" option in your BIOS, disable it, and use the "Legacy Boot" option or something similar. See if that works.

---

### Post by crip720 on 2017-11-05
It is a legacy bios computer, does not have secure boot.  Some posts that I have looked at that explains post beeps simply, recommend replacing motherboard, not a good idea for a laptop.

---

### Post by william.hua on 2017-11-05
Is the BIOS running the latest firmware provided by the manufacturer? Usually manufacturers suggest you flash the BIOS with the latest revision only if you are having issues with the current one, which you seem to be in this case. I would go ahead do it in this case and see if it helps.

---

### Post by crip720 on 2017-11-05
BIOS problem should affect Windows and Ubuntu, but Win 7 and 10 are loading okay with no problem.  Win7 and Ubuntu have been working well with this laptop since Win 7/Ubuntu 10.04 came out.  Grub is okay.

---

### Post by crip720 on 2017-11-05
Have been able to load Ubuntu 14.04 by recovery mode and resuming normal boot.  Tried some earlier kernels and they do the same.  Will try to update.  Have updated and still same with new kernel, seems like I can only boot by going to recovery and resume normal boot.

---


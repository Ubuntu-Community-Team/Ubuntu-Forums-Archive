---
title: "Why is 32-bit install recommended over 64-bit?"
date: 2011-12-29
forum: Recurring Discussions
---

### Post by PeterTaps on 2011-12-29
Folks,

When you go to download Ubuntu image, it says "Download 32-bit (recommended)." I don't understand why 64-bit is being discouraged? Are there issues with 64-bit image?

I am building an HTPC and will primarily be running VLC. Is there a problem with av codecs on 64-bit?

Thank you in advance for your help.

Regards,
Peter

---

### Post by kalfusisagod on 2011-12-29
I don't think 64 bit is NOT recommended per se, but, 64 bit is slowly becoming the standard. Plus if you do have a 64 bit processor, a 32 bit WILL be able to run on that processor. If you have a 32 bit processor, a 64bit OS will NOT run on that processor. Plus many programs have not been compiled to work with 64 bit, but a 32 bit program should still work on a 64bit OS and processor.

---

### Post by JRV on 2011-12-29
> **kalfusisagod said:**
> Plus many programs have not been compiled to work with 64 bit, but a 32 bit program should still work on a 64bit OS and processor.

There are still a few programs that are not 64 bit, but not many.  Lightscribe printing is the only one that I use.  I have heard that there is an improvement in the way 64 bit handles 32 bit code in the latest Ubuntu (Oneiric 11.10).  But I have not tried it.

Starting with Ubuntu 12.04 64 bit will be the recommended install.

---

### Post by oldos2er on 2011-12-29
Moved to Recurring.

---

### Post by mamamia88 on 2011-12-29
Because 32 will work on 64 machines but not vice versa.

---

### Post by 3Miro on 2011-12-29
64-bit used to have issues with flash and some drivers, right now, the only issue may be with some very old 32-bit proprietary printer drivers. Starting with the next version, 64-bit would be the recommended one, although you can install 64-bit now. I have been using 64-bit exclusively since 8.10 (i.e. three years ago).

---

### Post by aysiu on 2011-12-29
I think it would make sense that the Ubuntu website detect whether you're using a 32-bit or 64-bit OS and then recommend the appropriate version. Does that show up in the user agent string?

(Yes, of course, some people change their user agent strings, but it's usually the browser version and not the OS... and anyone power user enough to do that can override the recommendation and download whichever version of Ubuntu shes wishes).

---

### Post by 3rdalbum on 2011-12-29
The 32-bit edition was "recommended" previously because some 32-bit-only proprietary software took a few extra steps to work on 64-bit Linux. 99.99% of open-source Linux software was already available for 64-bit Linux as it was only a recompile away.

On Ubuntu 11.10, even the 32-bit-only, proprietary software works without issue on 64-bit.

Starting from Ubuntu 12.04, the 64-bit edition will be "recommended" and the 32-bit edition will only be advised to people without 64-bit-capable CPUs.

---

### Post by Merk42 on 2011-12-30
> **aysiu said:**
> I think it would make sense that the Ubuntu website detect whether you're using a 32-bit or 64-bit OS and then recommend the appropriate version. Does that show up in the user agent string?
It can, but there are the cases where someone would have a 32bit OS (and thus User Agent) on a machine with 64-bit capable hardware. There is also the case where they would download on computer A to install on computer B

---

### Post by aysiu on 2011-12-30
> **Merk42 said:**
> It can, but there are the cases where someone would have a 32bit OS (and thus User Agent) on a machine with 64-bit capable hardware. There is also the case where they would download on computer A to install on computer B
The autodetection would be only for a default recommendation. It would **not prevent** someone from downloading another version.

Someone who *knows* she's on a 64-bit processor with a 32-bit OS could still download the 64-bit version. But if she's already using a 32-bit OS on her current computer, maybe 32-bit Ubuntu might be a good idea for her to start with as a download anyway.

---


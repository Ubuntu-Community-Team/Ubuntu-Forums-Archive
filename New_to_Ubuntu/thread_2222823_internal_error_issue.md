---
title: "internal error issue"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by windowsfree on 2014-05-08
Hello all,

I recently installed Ubuntu 14.04 on my Lenovo s10-2 netbook.  Seems like all went well for about 4 days and now i am getting an "internal error" message after logging in.  I have the option to cancel or send report.  i have been sending report.  it doesn't seem to affect operation, but i get the popup about 3 times before i can continue with being stopped by it.
  
I don't have a screenshot of it, but how can i tell what is causing it.  I just received a pop-up to update the kernel and have done that.  The issue continues after doing the update and rebooting. 

Any suggestions?

---

### Post by tgalati4 on 2014-05-08
Use your smartphone to take a picture of the screen and post a picture.  It could be a module (hardware driver) issue or an ACPI issue, or a kernel issue, but it's hard to guess.  New kernels on older hardware will tend to generate errors until they are patched.

---

### Post by Danger_Monkey on 2014-05-08
You might also look at the system logs in /var/log and see if there is a clue there as to what is happening.  specifically, check these files:

```

/var/log/kern.log
/var/log/syslor
/var/log/boot

```

Hopefully, they can shed some light on the issue.

---

### Post by windowsfree on 2014-05-08
> **tgalati4 said:**
> Use your smartphone to take a picture of the screen and post a picture.  It could be a module (hardware driver) issue or an ACPI issue, or a kernel issue, but it's hard to guess.  New kernels on older hardware will tend to generate errors until they are patched.

Thank you for the reply,  I will do that and post it as soon as i can.

(I am using a Lenovo S10-2 netbook with a 1.6 atom proc and 2 gigs of ram.)

---

### Post by windowsfree on 2014-05-08
thanks DM, i will check

---

### Post by windowsfree on 2014-05-08
kernel log too big to upload.

---

### Post by Danger_Monkey on 2014-05-08
Probably the last 200 lines or so would work

---

### Post by windowsfree on 2014-05-09
added attachment above.  have not been able to reproduce original issue.

---

### Post by Danger_Monkey on 2014-05-09
Interesting.  In the Kernel log, it appears that there is no disk cache, like the drive presents itself as SCSI.  So it has put itself in "write-through" mode.  No big deal, it will still function correctly, just a little slower.  As I recall, this was a bug a couple of years ago, but has been patched.  

Not much to go on for the original issue....

---

### Post by windowsfree on 2014-05-09
thanks for reviewing it, i haven't been able to duplicate the issue now in 2 days.  I just tried again about 30 minutes ago.  I hope to install this on my laptop next.  Thanks again.

---

### Post by windowsfree on 2014-05-12
Can't seem to get it to occur again.  marking issue as Resolved.

---


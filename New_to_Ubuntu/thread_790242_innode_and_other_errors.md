---
title: "innode and other errors"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by carusoswi on 2008-05-11
Running 8.04 since beta first was released.  System updates are current.  Went to check my iwconfig, no terminal would come up.  Rebooted.  Machine went into forced fsck.  Failed.  Ran manual fsck.

Numerous inode file errors (don't know what that means, but answered yes to 50 or more such requests to fix.

Then, another nearly equal number of orphaned files to fix - answered yes.

Finally, machine requested a reboot.  Back to "normal" now.

What is causing this.

Caruso

---

### Post by nowshining on 2008-05-11
could be ur hard drive is about to die out. I suggest Getting a new one soon.

---

### Post by carusoswi on 2008-05-11
> **nowshining said:**
> could be ur hard drive is about to die out. I suggest Getting a new one soon.

I really think this has something to do with 8.04.  Never see the problem on XP side, and never had a problem previous to this particular instance.  Drives aren't spankin' new, but they aren't ancient, either.  My main drive is probably less than 9 months old, 300 GB - forget which make.  I really don't think it's a hard drive problem, though.

Machine doesn't run 24/7 and never has (don't know if that's good or bad).

I suppose I could run some sort of diagnostics on the drive - what do you think?  If it is a drive problem, what would diagnostics show that would give me a clue, and what would you recommend as a diagnostic tool?

Thanks for your reply.

Caruso

---

### Post by carusoswi on 2008-05-17
> **nowshining said:**
> could be ur hard drive is about to die out. I suggest Getting a new one soon.

As a follow-up, I think you were more on track than I, but, fortunately, my HD didn't (and I don't think it will) go.  I do believe that I had a cooling problem.  Today, I had run my machine some five hours with no problem, but decided to copy the contents of an 8gb flash card to my main system HD.  About half way through,  the transfer stopped and my machine was frozen.  The only way out was a reboot, and that returned an OS Error.  No amount or rebooting would help.  

I figured my HD, for whatever reason was corrupted, so I start rooting around to find my 8.04 LiveCD - last I saw it was when I put 8.04 on the Mrs' computer.

Well, I could not locate it, so had to download 8.04 from the net using her machine, my machine being turned off during this time.

Finished the DL, burned a new iso disc, turned on my crippled machine, and it booted right up.

Went back into my bios, set the smart fan to run continuous, been running all day, made that big transfer from the FC, have rebooted several times (downloaded and tried a livecd of SABAYON - yawn), nothing was lost, all working fine now.

I'm guessing that my problem was overheating - not certain what protection, if any, is built into the HD's these days, but am guessing that it reached a critical temp, then, just shut down in an effort to self-protect, then, was good to go when it cooled down a bit.

Someone smarter than me is welcome to comment on whether or not you think this might be a possibility.

The machine is an XPC small form factor, and I do have two large capacity drives in that little box.

Tell me what you think.

Caruso

---

### Post by nowshining on 2008-05-17
install smartmontools from the repos. (it's a cli thing) - i'll take u thru that next after u confirm installing it.

---

### Post by carusoswi on 2008-05-18
> **nowshining said:**
> install smartmontools from the repos. (it's a cli thing) - i'll take u thru that next after u confirm installing it.

Didn't find smartmontools.  What am I doing wrong?

Caruso

---

### Post by nowshining on 2008-05-21
did u enable all the repos? in software-properties?

---

### Post by carusoswi on 2008-05-21
Yup - I think so.  Can't check now until this weekend.  No internet on the linux box during the week.
Caruso

---


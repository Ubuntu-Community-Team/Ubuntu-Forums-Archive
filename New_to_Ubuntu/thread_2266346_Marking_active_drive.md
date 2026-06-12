---
title: "Marking active drive"
date: 2015-02-22
forum: New to Ubuntu
---

### Post by nick171 on 2015-02-22
I was attempting to set up dual boot windows/ubuntu when I accidently marked C drive partition as active partition.

Now windows won't boot and I have no windows repair cd available so I was wondering if I could remedy this by marking the correct active partition through ubuntu.

How can I fix this through ubuntu so windows will boot again?

Any help would be appreciated (also sorry if this is the wrong forum for this type of question)

---

### Post by Mark Phelps on 2015-02-22
The "active" partition in Windows is the one that contains the OS. In the case of preinstalled Windows installs using Win7 or newer, there is a small partition near the beginning of the drive.  That partition requires the boot flag, but the OS partition needs to be marked as Active.

---

### Post by nick171 on 2015-02-22
Ok how can I mark the boot flag through ubuntu

---

### Post by Mark Phelps on 2015-02-22
> **nick171 said:**
> Ok how can I mark the boot flag through ubuntu

You use GParted.

---

### Post by nick171 on 2015-02-22
Thank you I was able to boot windows

---

### Post by sandyd on 2015-02-23
Hi, if you have found a solution, please mark this thread as solved via Thread Tools -> Mark Thread as Solved

Thanks!

---


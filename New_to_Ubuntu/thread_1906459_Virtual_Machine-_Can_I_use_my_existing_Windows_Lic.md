---
title: "Virtual Machine- Can I use my existing Windows License?"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by Wiking on 2012-01-09
When setting up a Virtual Machine, do I need a **new **Windows License? Or can I use the License of my **pre-existing** Windows 7 install currently running on dual boot?

---

### Post by MartijnNL on 2012-01-09
**Edit: my orginal info was incorrect. See Mark's post below.**

---

### Post by Mark Phelps on 2012-01-09
You need to read that linked material again -- the 4 licenses applies to Volume Licenses (Software Assurance), NOT to OEM or Home versions.

Further down in the linked material is the following:

> Instead of using the software directly on the licensed computer, you may install and use the software within only one virtual (or otherwise emulated) hardware system on the licensed computer.

Notice it says "Instead" -- meaning you can only use it once -- either real install or VM, but not both, and certainly, not FOUR times!

---

### Post by MartijnNL on 2012-01-09
You're right. Should have read a bit further.

---

### Post by Wiking on 2012-01-09
So even if I run a virtual machine on a Linux platform I will need a new Windows license?

---

### Post by nothingspecial on 2012-01-09
You can either run it on the hardware **or** in a virtual machine.

---

### Post by Cheesemill on 2012-01-09
If you currently dual-boot you have a couple of options:

If your version of Windows is an OEM version that came preinstalled on your machine, then you will need a new license whether you continue to dual boot or not.

If you have a full retail version of Windows then you could use that license for your VM as long as you uninstall the physical copy first, ie change to single booting Ubuntu + a Windows VM.

---

### Post by anewguy on 2012-01-09
> **Wiking said:**
> So even if I run a virtual machine on a Linux platform I will need a new Windows license?

EDITED OUT ORIGINAL REPLY TO AVOID CONFUSION

OOOPPPSSS - no, not necessarily a NEW license - I didn't catch the "new" part when I first posted.  You can reuse your existing license if you do things the correct way.  I guess the entire point is you need A license.

Dave ;)

---

### Post by Mark Phelps on 2012-01-09
> **Wiking said:**
> So even if I run a virtual machine on a Linux platform I will need a new Windows license?

According to the info provided, technically, yes.

Will that stop it from installing -- no.

Will it prevent it from being activated -- maybe.

Some folks have tried installing VB inside Linux on a PC currently running a copy of Windows -- and then linking VB (somehow) back to the installed version of Windows. When that DID work (which was not often), every time they booted back into the installed Windows copy, it required reactivation (because the VM hardware signature is different from the real hardware signature).

So even that did not work out in the long run.

---

### Post by anewguy on 2012-01-09
Yeah, I was one of those who went against the recommendations of the forum and linked Virtualbox to my existing WIndows installation, and I would never recommend doing it.  As you mentioned about the license, plus it fights because of the virtual hardware versus the true hardware whenever you change how you boot.  Big mistake on my part ;)

Dave ;)l

---


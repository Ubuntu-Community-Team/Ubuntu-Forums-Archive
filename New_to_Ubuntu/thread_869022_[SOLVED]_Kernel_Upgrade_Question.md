---
title: "[SOLVED] Kernel Upgrade Question"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by BGFG on 2008-07-24
Hi
I just upgraded to kernel 2.6.24-20. During the process a dialog came up asking about my debconf menu.lst and if i wanted to keep my existing one or use the new one provided by the package maintainer. 

I chose the package maintainer this time. I've been googling it, but i'd like some of your feedback also.

---

### Post by avtolle on 2008-07-24
Given the number of threads on the Forum today about the problems with the new kernel, which has a known bug, you might have a problem booting it. As to your question, I always select the option for the package maintainer, which hopefully will have at least one instance of a prior kernel listed so you will be able to boot (if you run into the problems being reported on the Forum).

To anyone lurking: when something is coming from the proposed repository, as the kernel upgrade is, think twice about installing it immediately. I'd suggest not having the proposed repository enabled at all on a production machine, as things in the proposed repository are there for testing, and will have bugs, as does the kernel upgrade. While I encourage anyone interested to help test, this should not be done on one's only computer as things may break, and leave a system which cannot be booted, for example.

EDIT: I'd also advise not being in a hurry about installing updates, especially ones that are not labeled security. My normal practice, especially with a kernel update, is to hold off for a period, during which I read the Forum to see whether the update is causing problems and if so, the work arounds or fixes. I've a separate box I use for this, prior to committing to an update on my main production computer.

---

### Post by Hospadar on 2008-07-24
it all depends really, if you've ever changed a config file, obviously you changed it for some reason, and as such may want to keep the version you have since modified.  Oftentimes though, some process made some minor change, or something re-set the modify timestamp on the file and it hasn't actually been changed in any noticeable way.
I usually just use the new file, although if it's a config file I know I modified for a reason, I'll keep my version.

---

### Post by philinux on 2008-07-24
I always choose "Package Maintainers" version.

---

### Post by BGFG on 2008-07-24
Thanks for the info.
I think i'll stick to the package maintainer's from now on then.
As for the new kernel, I guess you guys can consider me a tester. I upgraded this morning and everything works, booted fine. If there's a command i can execute and post the results here so you guys can see my system in detail just let me know.

NB.
Apparently ov511 is not included in -20

---

### Post by philinux on 2008-07-24
If everything is running fine for now then un-check the Proposed repo in software sources. You dont need it unless you really want to risk breaking your install.

---

### Post by BGFG on 2008-07-24
Actually, i don't mind having the proposed turned on, I definitely don't just hit 'install' when i see something new. Usually i'll hit the forums and google, and if i'm not happy i'll just let them sit there.

---

### Post by philinux on 2008-07-24
> **BGFG said:**
> Actually, i don't mind having the proposed turned on, I definitely don't just hit 'install' when i see something new. Usually i'll hit the forums and google, and if i'm not happy i'll just let them sit there.

Good policy. :)

---


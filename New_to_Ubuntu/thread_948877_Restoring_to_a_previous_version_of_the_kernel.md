---
title: "Restoring to a previous version of the kernel?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Lorelei- on 2008-10-15
Hi all,

I'm having major sound issues after doing a kernel update earlier tonight (see the post on this forum for more on that) and as none of the fixes seem to work at the moment, I'm looking to go back to the previous kernel where the sound was working.

How do I do this? (step by step instructions please!)

---

### Post by jerome1232 on 2008-10-15
Well to just boot from it you can select it from the grub entry

(mash esc during the boot up sequence and when you finally pull up the grub menu hit down twice you should now be highlighting your old kernel)

To make booting to it default the easiest way is to install startupmanager and select it as the default kernel.

Once installed it'll be under System->Administration->Statup Manager

```
sudo apt-get install startupmanager
```

---

### Post by Lorelei- on 2008-10-15
Thanks Jerome1232, its sorted now and I've learnt something new too.

---

### Post by Dermot Doyle on 2008-10-18
I've read about half a dozen threads on this problem and tried all manner of solutions to no avail. Finally did what Jerome 1232 suggested and everything works. I am so impressed with this forum and the help available to newcomers like me. I'm now confident I can go back to the new kernel once the bug is sorted. What a great resource.

---


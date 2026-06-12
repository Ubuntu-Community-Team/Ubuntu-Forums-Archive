---
title: "Weird &quot;update-grub&quot; behavior"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Victormd on 2008-08-14
I just update my kernel to 24.21 and my menu.lst wasn't automatically updated. I ran update-grub to no luck. The weird thing is that update-grub recognizes the new kernel, says that it updated /boot/grub/menu.lst but when I open it, it's not updated. I manually added the new kernel and all is fine but I'm just wondering WHY my menu.lst wasn't automatically updated. Any thoughts?

---

### Post by drs305 on 2008-08-14
Even if you update the kernel and update grub, there are settings within menu.lst that may preclude the menu changing. Here are some of the settings that influence what happens to grub when a kernel is added:

```

## should update-grub create alternative automagic boot options
## should update-grub lock alternative automagic boot options
## should update-grub lock old automagic boot options
## controls how many kernels should be put into the menu.lst
## should update-grub adjust the value of the default booted system

```

For instance, if your settings told grub to keep the last booted kernel and also told it to display only one kernel, even though a newer kernel was available on your machine your menu.lst display would not change.

In another example, it may add a new kernel to the display but still boot to an older kernel if that is how the options are set up.

A bit of this is discussed in the menu.lst link in my signature line.

---

### Post by Victormd on 2008-08-14
Yeah, I'm aware of those options. What's bugging me is that on the last kernel update there were no problems and I didn't change anything... at least not that I can remember... :)

---

### Post by bumanie on 2008-08-14
this won't help with an answer, but I had exactly the same issue with 2.6.xx-19, never worked out a solution.

---

### Post by Victormd on 2008-08-14
that's why I didn't understand, because it's not normal... it's not a big deal, just weird...

---

### Post by epitaph123 on 2008-08-26
No one has said how to manually update the kernel in the grub menu.lst?????????????????????????????????????????????????????

---

### Post by drs305 on 2008-08-26
> **epitaph123 said:**
> No one has said how to manually update the kernel in the grub menu.lst?????????????????????????????????????????????????????
epitath123,

Are you trying to 
1. Download and use a new kernel
2. Change the kernel that boots to a newer one
3. Add a new kernel's options in menu.lst but use an older one
4. Something else

If you post the results of the following and tell us what you want to do we can help:
```
cat /boot/grub/menu.lst
```

**Added:** A few posts have been added after this one. Please note the previous post is not from the OP. It is a follow-on question from another user.

---

### Post by falcon61102 on 2008-08-26
I know it's a simple thing but did you run update-grub as sudo?  Not doing that could prevent the grub from overwriting the menu.lst due to permission issues.

---

### Post by Archmage on 2008-08-26
Kindly note that the 24.21 is not a standard kernel. It seems that you are using a unsuported developer kernel.

---


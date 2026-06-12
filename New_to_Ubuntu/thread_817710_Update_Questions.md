---
title: "Update Questions"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by WhyAreWeRunning on 2008-06-03
After I updated Ubuntu, Grub wants to load and shows two versions of the kernel. How do I fix this and prevent this from happening in the future?

Thanks in advance for the help.
 -Running

---

### Post by drs305 on 2008-06-03
Although you might not like looking at it, having the option to easily switch opening kernels is not a bad thing - at least for the first week or two of a new kernel's introduction.

However, if you must reduce the number of kernels viewed, you can do it via StartUp-Manager (System, Administration, StartUp-Manager, Advanced. Number of kernels to keep. You can change it to 1 if you insist. 

Note this only changes the menu, it doesn't physically remove any of the old kernels. And you can come back to this menu and change it back to a different number (as long as those kernels are still physically stored on ubuntu).

If you don't see StartUp-Manager in the menu,
```
sudo aptitude install startupmanager
```

There are essentially 4 ways to change the menu. This is one of them.

---

### Post by Bubba64 on 2008-06-03
> **drs305 said:**
> Although you might not like looking at it, having the option to easily switch opening kernels is not a bad thing - at least for the first week or two of a new kernel's introduction.

However, if you must reduce the number of kernels viewed, you can do it via StartUp-Manager (System, Administration, StartUp-Manager, Advanced. Number of kernels to keep. You can change it to 1 if you insist. 

Note this only changes the menu, it doesn't physically remove any of the old kernels. And you can come back to this menu and change it back to a different number (as long as those kernels are still physically stored on ubuntu).

If you don't see StartUp-Manager in the menu,
```
sudo aptitude install startupmanager
```

There are essentially 4 ways to change the menu. This is one of them.

This is good advice also if you want to change the kernel running right at booting you hit esc when the screen prompt tells you then choose the kernel for that booting.

---


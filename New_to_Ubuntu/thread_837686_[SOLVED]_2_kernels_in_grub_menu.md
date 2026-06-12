---
title: "[SOLVED] 2 kernels in grub menu?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by tropdoug on 2008-06-22
Yesterday I applied the recommended software updates including an upgraded kernel. This morning I see both the old kernel and the new one listed on the grub menu choices. Does this mean that I now have two complete kernels on the machine? 

If this is the case then what is the reason, because as a common sense thought, it would seem that all that would do would be to take up unnecessary disk space with uneeded software. 

If I am right how do I safely remove the old unwanted kernel, and clean up the traces.

Douglas
</div>

---

### Post by angryfirelord on 2008-06-22
Yes, when you update your Ubuntu system, you install the new kernel, but it keeps the old one as well. If you want to remove the others, open up Synaptic, type in the search box *linux-image*, and then remove the old versions. Don't remove any of the metapackages though.

---

### Post by Biggy on 2008-06-22
1- Open System -> Admin -> Synaptic package manager 
2- Search for: linux-image
3- Select the (old) kernels you no longer need and Mark for complete removal. Click Apply.

---

### Post by KenBW2 on 2008-06-22
I had your problem.
Firstly, what release of Ubuntu are you using
What kernels do you have?

EDIT: Looks like I was beaten to it

---

### Post by Oldsoldier2003 on 2008-06-22
> **tropdoug said:**
> Yesterday I applied the recommended software updates including an upgraded kernel. This morning I see both the old kernel and the new one listed on the grub menu choices. Does this mean that I now have two complete kernels on the machine? 

If this is the case then what is the reason, because as a common sense thought, it would seem that all that would do would be to take up unnecessary disk space with uneeded software. 

If I am right how do I safely remove the old unwanted kernel, and clean up the traces.

Douglas
</div>
do a search in synaptic for linux-image, then select your old kernel and mark it for complete removal. Synaptic will remove the kernel and clean up grub for you.

with that said its not a bad idea to keep the version behind your current kernel as a backup.

---

### Post by drs305 on 2008-06-22
Here is some info on the extra kernel display and how you can safely change other aspects of grub's menu.lst:

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Biggy on 2008-06-22
my latest current kernel is : linux-image-2.6.24-19-generic

---

### Post by tropdoug on 2008-06-22
Wow, thanks guys, that was like lightning replies and all spot on. Great stuff. another nugget of Linux knowledge to file away for future use. 

Thank all.

---


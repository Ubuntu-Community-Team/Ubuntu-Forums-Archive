---
title: "I have 2 Ubuntu and 2 recovery options on bootup?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by LeeHamo on 2008-10-16
I have read a bit about this and understand that recent update may of created a new kernel...

So does this mean the old one that I probably will never boot into (whats the point?) is using up drive space for no reason?

And in future updates I will end up with another boot option?

So potentially I could end up with a whopping great list of boot options, then at the very bottom windows XP, lol where it belongs I suppose.

Does most people keep all the old ones? are they all huge files?

Lee.

---

### Post by fooman on 2008-10-16
i keep the latest and the one previous to it.  the rest have been removed using synaptic.

---

### Post by LeeHamo on 2008-10-16
How do I do that?

I know there is a way to just hide them as such by putting a # before the one you want to hide am i right?

is it # the a space or just # straight before the writing?

How is it done in synaptic?

---

### Post by Keen101 on 2008-10-16
when you put the # symbol in the /boot/grub/menu.lst file it comments out anything after it. It does not matter if there is a space or not as afar i know.

New kernals can sometimes contain bad drivers and may even fail to boot, so it is recommended to keep at least one backup. I comment out all the ones i don't need.

I suppose synaptic would work to remove the rest, but i've never done it.

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by fooman on 2008-10-16
in synaptic,  searching for *linux-image* will show you all the installed kernels.  you can right click on ones you want to remove and choose "mark for complete removal" to uninstall them.  doing that will also remove the lines from grub.  like was said already, be sure to leave at least one older working kernel....just in case.

---

### Post by jgrabham on 2008-10-16
> **LeeHamo said:**
> 
So does this mean the old one that I probably will never boot into (whats the point?) is using up drive space for no reason?
If you have problems with the new versions of the kernel, X, drivers etc, you can easily go back to the config where it worked.
> 

And in future updates I will end up with another boot option?

So potentially I could end up with a whopping great list of boot options, then at the very bottom windows XP, lol where it belongs I suppose.

The kernel isn't updated that often, if, and when you upgrade distros, redundant ones will be removed - there aren't normally more than 2 per distro, so 2 kernel options with recovery options and Windows, means five options.> 
Does most people keep all the old ones? are they all huge files?



Yes, and no, the different kernel versions are quite small.

---

### Post by kansasnoob on 2008-10-16
AQnother way to deal with this is to install startupmanger from synaptic or:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration >

[ATTACH]88571[/ATTACH]

[ATTACH]88572[/ATTACH]

You see in the second screenshot you can select how many kernels to show? I generally just keep it on 1, but when I get a kernel upgrade I always change it to 2 before restarting so I can select the older kernel if the new kernel has problems with my hardware. Once I know the new kernel is working well I change it back to 1.

---


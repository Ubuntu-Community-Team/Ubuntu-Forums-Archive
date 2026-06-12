---
title: "Switching kernels"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by seattle vic on 2008-08-09
I loaded hardy ubuntu server by mistake.  Seems to work ok, but I'd like to load the regular version.  I realize the kernel is different, so how do I load up the right kernel without having to go through the entire dvd load again?  And are there any ubuntu files that would have to be changed out as well?

Thanks in advance,

Vic

---

### Post by Crafty Kisses on 2008-08-09
This thread may be useful to you < [http://ubuntuforums.org/showthread.php?t=693713](http://ubuntuforums.org/showthread.php?t=693713)

---

### Post by cariboo on 2008-08-09
Just go to System-->Administration-->Synaptic Package Manager and search for linux image. Just choose the generic kernel with the same number as your server kernel, if you're not sure which one you've got, in a terminal type:

```
uname -a
```

This will give you the kernel version.

Jim

---

### Post by Vivaldi Gloria on 2008-08-10
I suggest you also keep the server kernel as a fallback incase the generic kernel fails. It is always good policy to keep at least two kernels.

---

### Post by sdennie on 2008-08-10
It should be as simple as:

```

sudo apt-get install linux-generic linux-restricted-modules-generic linux-headers-generic

```

The -generic kernel may not be the default one so, you may have to select it at boot time by hitting Escape when the grub menu comes up.  You can remove the -server kernel and use just -generic later but, as stated above, it's best to keep something around that is known to work.

---

### Post by seattle vic on 2008-08-10
> **vor said:**
> It should be as simple as:

```

sudo apt-get install linux-generic linux-restricted-modules-generic linux-headers-generic

```

The -generic kernel may not be the default one so, you may have to select it at boot time by hitting Escape when the grub menu comes up.  You can remove the -server kernel and use just -generic later but, as stated above, it's best to keep something around that is known to work.

I loaded the new generic kernel and changed grub to default to it.  However, ubuntu does not behave like my other computer which runs generic.  It doesn't automatically tell me when updates are available, and the graphics aren't the same either.  Are there some x or ubuntu programs that are different with different kernels?

---


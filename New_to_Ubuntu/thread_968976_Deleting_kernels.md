---
title: "Deleting kernels"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by brodiesel on 2008-11-03
So, every time I boot up, I am given the option for two different kernels and their recovery modes, and xp. now, the old one is the first  option, and it automatically boots if i dont hit anything within five seconds. The problem is that wireless doesnt work for the old kernel, so i never use it unless by accident when its a pain in the ***. additionally, i'm thinking of upgrading to Ibex soon.

Long story short, how do I delete the old kernel, and is there any reason not to?

---

### Post by sica07 on 2008-11-03
Yesterday there was a post about the very same problem (and the solutions too :P ):
[http://ubuntuforums.org/showthread.php?t=967628](http://ubuntuforums.org/showthread.php?t=967628)
Success!

---

### Post by Nepherte on 2008-11-03
Ubuntu doesn't remove the older kernel versions when a new one is installed. The reason is that when a new one breaks your system, you can still use the older one. If the latest one works for you, you can safely remove the other ones. In synaptic search for linux-headers and linux-image, look carefully at the version number and remove the ones you don't need.

Instead of completely removing the older kernels, you can also choose to hide them in the grub boot menu, as shown in the post above me.

---

### Post by brodiesel on 2008-11-03
so i'm a little slow... how does one use synaptic to remove kernels? i opened it and searched for 'kernel' but then i got 1300 results and was lost...

---

### Post by Nepherte on 2008-11-03
Search for linux-image. That will turn up your old kernels and the one you are using now. Check the version number to be sure what to remove. To figure out which kernel you are using, type in a terminal:
```
uname -r
```

---


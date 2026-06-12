---
title: "Editing GRUB"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by R6V2 on 2008-05-04
When my computer starts up, it says: GRUB Loading Stage 2...

Is there a way I can edit a file to make it say:

Loading Current Operating Systems...

?

Thanks!

---

### Post by overdrank on 2008-05-04
> **R6V2 said:**
> When my computer starts up, it says: GRUB Loading Stage 2...

Is there a way I can edit a file to make it say:

Loading Current Operating Systems...

?

Thanks!

Hi and you can edit you grub and this link has some good info
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by R6V2 on 2008-05-04
That doesn't have anything in there about what I want. At least I don't think. I didn't take 5 hours looking either.

---

### Post by PeterJS on 2008-05-04
Looks like the "Loading stage2" string is hard coded in to the stage2 binary. If you want to change that you'll have to download the grub source, change it there, and then recompile grub.

```

peter@Osirus:~$ strings /boot/grub/stage2 | grep Loading
Loading stage2
Loading below 1MB is not supported

```

---

### Post by Joeb454 on 2008-05-04
I'm not sure you can, I think it's part of a GRUB binary file, meaning you can't edit it without modding the source code

---

### Post by R6V2 on 2008-05-04
Oh, Okay then.

---

### Post by Joeb454 on 2008-05-04
I can see what you're trying to do - it'd be nice to be able to change it.

---


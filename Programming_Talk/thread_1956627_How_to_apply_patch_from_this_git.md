---
title: "How to apply patch from this git"
date: 2012-04-11
forum: Programming Talk
---

### Post by silverair on 2012-04-11
I need to apply the patch called "Character Devices in user space"
to the kernel, from [http://lwn.net/Articles/328404/]("http://lwn.net/Articles/328404/"). 
the link tells me that i need to apply 6 patches from the patch set.
from my understanding, i need tar.bz files to patch.

how do i get those  say, from here : [http://git.kernel.org/?p=linux/kernel/git/tj/misc.git;a=commit;h=4c324728bb913e71b2e0cabf452dfe0866fe0c1e](http://git.kernel.org/?p=linux/kernel/git/tj/misc.git;a=commit;h=4c324728bb913e71b2e0cabf452dfe0866fe0c1e) ?
I see the link called patch which shows text when i click it. I understand how the + and - in the patch works. 
Should i just copy the text to a file and apply patch as "patch -p1 patchfile"  ? 
is the patch version independent, since the version no is not mentioned? i.e can it be applied to any kernel version?

---

### Post by silverair on 2012-04-11
Never mind i installed patch. i used git checkout <head mentioned in patcset description>, then patch p1 patchname (i copied the text to patchfile)

then, 
copied my  old .config
make -j4 all
make bzImage
make modules_install install


Now, i am having problems with booting from the compiled kernel
It never moves past the boot screen (never stops initializing ram)

---


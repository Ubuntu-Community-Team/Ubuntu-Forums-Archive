---
title: "Swap space with linux"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by davidc60 on 2012-01-03
I have installed several Linux distros ((Ubuntu; Fedora; Peppermint 2 and Linux Mint) onto logical drives on an extended partition on my HDD. Up to now I have allocated a separate 'swap space' for each one but I wonder whether it would have been possible to simply have just the one 'swap space' in one logical drive on that extended partition which could be used by any of the Linux distros as and when required? Thanks, davidc

---

### Post by cortman on 2012-01-03
> **davidc60 said:**
> I have installed several Linux distros ((Ubuntu; Fedora; Peppermint 2 and Linux Mint) onto logical drives on an extended partition on my HDD. Up to now I have allocated a separate 'swap space' for each one but I wonder whether it would have been possible to simply have just the one 'swap space' in one logical drive on that extended partition which could be used by any of the Linux distros as and when required? Thanks, davidc

I believe they share a single swap partition by default if there is only one available.

---

### Post by wolfen69 on 2012-01-03
> **cortman said:**
> I believe they share a single swap partition by default if there is only one available.

That would be true. You only need *one*.

---

### Post by davidc60 on 2012-01-04
Thanks for your replies.
davidc

---

### Post by 1clue on 2012-01-04
That's not necessarily true.

If you hibernate one OS and then boot into another, then you will crash when you try to boot back into the hibernated one.  Hibernate stores the RAM image into SWAP and then shuts down.

---

### Post by davidc60 on 2012-01-04
Noted! - thanks for your input.
davidc

---


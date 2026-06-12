---
title: "Is &quot;all_generic_ide&quot; a good solution?"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by cait on 2008-06-29
I just built my first ever computer, and the hardware all seems to be installed and working ok. I decided to use try Ubuntu as my only OS for now, but I had trouble running or installing it at first. It kept going straight to BusyBox (this happened with two different versions), and I finally found a forum that suggested adding **all_generic_ide** to the boot options, and this worked.  I talked to a friend who knows a lot more about this sort of thing than I do, and he said he doesn't think that's a very solid solution and that it might slow down my computer a lot. He said that he thinks something needs fixed in the kernel drivers, but I have no idea how to do that. Does anyone know much about the **all_generic_ide** option and have any input about whether I should try to find a better solution to things? I'd like a second opinion before I spend ages trying to figure out how to fix the kernel drivers.  Thanks!

---

### Post by bumanie on 2008-06-29
I don't know too much about all_generic_ide, but do know that at it was a work-around posted on launchpad for getting some types of hard drives (maxtor drives from memory) working in ubuntu. Can't see how it would slow things down too much though, however, I don't really know for sure. Certainly there was no mention of that in launchpad.

---

### Post by mkantor1 on 2009-01-20
I've had to use this on two separate machines in both 8.04 and 8.10 and I can say that for me it causes boot to take a LOT longer than it it should (between two and five minutes versus about 30 seconds without the option).

---


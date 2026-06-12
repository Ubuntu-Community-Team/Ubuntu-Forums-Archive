---
title: "How can I remove XP dual boot without removing something I should not?"
date: 2014-03-25
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-03-25
I installed XP first, then 12.04 as dual boot.  After a while I decided to install XP in VB and that works so well that I want to free up some disc space by removing every trace of the original XP install.  How can I do that and be sure I'm not taking out something still needed?  Is the XP in VB somehow protected in its own space?

---

### Post by Mark Phelps on 2014-03-25
>  Is the XP in VB somehow protected in its own space? 

Yes -- it is entirely separate from the XP you have installed in its own partition.

To remove XP, simply boot into Ubuntu, run GParted, and remove the partition containing XP.

---

### Post by monkeybrain20122 on 2014-03-25
You can remove xp easily by running gparted from the ubuntu partition (you have to install gparted), the hard question is how do you fill in the space it left.

Depending on the layout of the partitions it can be tricky. In dualboots usually WinXP lives in the first partition,--since it is installed first,--that means if you want to reclaim the space without reinstalling Ubuntu you would need to expand Ubuntu's partition to the left. You need to run gparted from a live usb to carry that out and it is somewhat risky when you expand a bootable partition to the left.

My solution would be to clone your Ubuntu partition (with fsarchiver or in this case clonezilla will do as well) then reformat your hard drive and restore the clone. It should be faster and a lot safer. If this is what you want to do start a new thread and we can help.

---


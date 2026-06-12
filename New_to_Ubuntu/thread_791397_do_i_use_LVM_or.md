---
title: "do i use LVM or ???????????????????????"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by pintsise on 2008-05-12
hip hip horay think i will get it sorted today.
i have been trying to put linux back on my think pad for approx three weeks tried all flavor linux i had it before i upgraded ram and new hd spent 3 weeks thing it was the hd as i couldnot get to the partioning bit my last ditch attept was posted yesterday when it was sugested i do a mem test with just looks like as a mass of meaingless numbers to myself but yea i notice it showed a mass of errors i removed the new ram chip a now we are cooking on gas. 

why am i ranting on ? well without the help of another user i would be still  bashing my head up the wall and just wanted to say what can be achived if we all pull together to help.Ubuntu probs today tomrrow world PEACE 

sorry now back to ubuntu i have now been met with a screen asking me weather i want to A erase the entire disk IDE1 master (hda)
B erase the entire disk and use LVM  Ide master hda 

Please can someone tell me what is what i want to run only linux with no secondery os

---

### Post by brian_p on 2008-05-12
> **pintsise said:**
> hip hip horay think i will get it sorted today.
i have been trying to put linux back on my think pad for approx three weeks tried all flavor linux i had it before i upgraded ram and new hd spent 3 weeks thing it was the hd as i couldnot get to the partioning bit my last ditch attept was posted yesterday when it was sugested i do a mem test with just looks like as a mass of meaingless numbers to myself but yea i notice it showed a mass of errors i removed the new ram chip a now we are cooking on gas. 

why am i ranting on ? well without the help of another user i would be still  bashing my head up the wall and just wanted to say what can be achived if we all pull together to help.Ubuntu probs today tomrrow world PEACE 

sorry now back to ubuntu i have now been met with a screen asking me weather i want to A erase the entire disk IDE1 master (hda)
B erase the entire disk and use LVM  Ide master hda 

Please can someone tell me what is what i want to run only linux with no secondery os

After all your problems I'd take the simplest route and have Ubuntu on one large partition (you could use the whole disk) and ignore the LVM option. At least you find out how the installation goes. LVM really needs to be read about thoroughly to get the best out of it and you can easily do without it.

---

### Post by didac on 2008-05-12
LVM will allow you to grow/shrink the partition. If, for instance, you install another hard disk when you run out of space, the new hard disk will be part of the LVM partition, not a new one.

If you are new to Linux, follow brian_p advice. If you want to try new ways, format as LVM. I'm very happy with LVM after four years using it.

---


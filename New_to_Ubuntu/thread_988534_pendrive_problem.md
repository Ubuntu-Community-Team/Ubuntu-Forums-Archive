---
title: "pendrive problem"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by xieu90 on 2008-11-20
hi everyone
i have a pendrive and it has some problems

when i stick it into xp/vista then it will run something like autorun forever
when i stick it to ubuntu then i can  not del or do a thing with it like it is locked like floopy

how can i format or do something taht i can continue using it ?

 (xp and vista are useless against my pendrive so my hope now is ubuntu)
i dont care if i lose everything in that pendrive

---

### Post by bobnutfield on 2008-11-20
Try using the Gparted partition editor to see if you can delete any existing partitions and re-format.

---

### Post by xieu90 on 2008-11-20
i cannot delete it
only unmout/set flag or information

what should i do now

---

### Post by bobnutfield on 2008-11-20
You cannot delete a mounted partition.  Unmount it, then delete it or format it.

EDIT:  I just noticed the keys in the first column.  Are you sure there is not a "lock" of some sort on the USB stick which prevent overwriting?

---

### Post by xieu90 on 2008-11-20
what now ?

---

### Post by bobnutfield on 2008-11-20
It appears that you have successfully deleted the partition.  But, input/output errors usually means a problem with the drive itself.  If this is an older USB stick, it may have been written to past its usable life.  USB sticks have limited number of writes to them before they eventually fail.  This number varies with the quality of the drive.

The only thing you can do now that it is unpartitioned is to try to format it now with Gparted.  Then try and insert it and see if it can be written to.  If not, then I would guess that it is unusable.

---

### Post by xieu90 on 2008-11-21
well after being deleted like in picture i cannot read/write mount it
so i pull it out and stick it in and the data is there again, and of course locked
may be it is like you said, it has reached its life limit
>.<

but i wont give it a nice funeral yet. :lolflag:

---


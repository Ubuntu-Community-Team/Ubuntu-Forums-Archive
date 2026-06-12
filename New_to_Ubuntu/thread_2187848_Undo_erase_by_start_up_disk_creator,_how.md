---
title: "Undo erase by start up disk creator, how?"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by kruget on 2013-11-14
Accidentally, i erased a 1 TB HDD (connected on usb) while i try to create bootable usb using start up disk creator. 
Now it is empty. I have not write anything at it yet, Only browser it using Thunar.

Is there anything i could try to recover the hdd's content?

---

### Post by Mark Phelps on 2013-11-14
Recovery tools tend to be filesystem-specific, so what filesystem was used on the external drive?

---

### Post by kruget on 2013-11-14
I am not really sure, but guess it is NTFS since i could use it on windows also.

---

### Post by newb85 on 2013-11-14
Then NTFS seems most likely (especially on such a large drive).

I'll throw out a suggestion, although it seems to run contrary to Mark Phelps' valid point.

If not already done, install gparted and gpart.  (Gpart is designed to find lost partitions and guess your partition table, and can act as an extension for gparted.)
```
sudo apt-get install gparted gpart
```

Then open gparted and go to Device>Attempt Data Rescue...

---

### Post by nerdtron on 2013-11-15
Do not write anything yet on the external hard drive. Now plug it in a windows computer and then install Recuva. I have used it before to recover data successfully.

---

### Post by chris_coulson2 on 2013-11-15
Seconding the suggestion to use Recuva. I've also used it with positive results.

---

### Post by kruget on 2013-11-17
Tried gpart with gparted. Failed, and found nothing. Then i got tetter result with recuva, it took more than 18-20 hours with many files found. Unfortunately many of the files got red status, unrecoverable. Maybe somehow i wrote on the disk before trying the rescue attempt. I think recuva would get better result if the disk still fresh.
 
Thank you @All for your time and attention. I set this as resolved.

---


---
title: "Formatting a USB Flash Memory?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by SamerBerjawi on 2008-05-15
How can I do that?

---

### Post by reacocard on 2008-05-15
Install gparted:
```
sudo apt-get install gparted
```
Now open gparted via System->Adminstration->Partition Editor. In the upper right of the window there's a menu. Select your flash drive from that menu. Now down in the main part right-click on the partition and there's an option to format. You probably want to format it as fat32 or ntfs if you need compatibility with windows.

---

### Post by SamerBerjawi on 2008-05-16
Thank you very much

---


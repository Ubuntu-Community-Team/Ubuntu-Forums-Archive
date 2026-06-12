---
title: "installing linux mint12 in separate partition"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-11-27
need some help everytime i try to do this with mint i mess things up badly so that ubuntu is not bootable. at bottom is output for gparted. i want to install mint on dev/sda5. when i try to do from live cd and select install to dev/sda5 i get this error message
no root file system defined
pls correct from the partitioning menu
i dont want to make ubuntu 11.10 unbootable and still want it to appear in the grub menu tks

---

### Post by rburkartjo on 2011-11-27
note i have already formated that partition to ext4 and it is blank now

---

### Post by ajgreeny on 2011-11-27
Are you using the "Something else" option on the disk preparation page of the install?

You should not have any problems if using that if you choose to:-
1.  Use this partition as an ext4 partition.
2.  Mountpoint / (from drop down box)
3.  Click on the "Format" tick box if it is not already selected.

The dialog box you see will be a bit like the one in the pic I have attached, and should be self explanatory, though you will also see a Format tick box which is not showing here..

---

### Post by rburkartjo on 2011-11-27
tks aj. yes i am using the something else options. been using linux for over 6 years and still have problems with the mount point so thank you. will give it a whirl

---

### Post by rburkartjo on 2011-12-04
aj worked like a charm,tks

---


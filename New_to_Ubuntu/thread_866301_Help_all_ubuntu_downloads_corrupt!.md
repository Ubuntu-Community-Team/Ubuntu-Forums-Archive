---
title: "Help all ubuntu downloads corrupt!"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by wbutchart on 2008-07-21
Hi i have downloaded several ubuntu (and xubuntu) iso's and each is failing the disk check as i attempt to install.

Im getting the bios 81 error which i have read is ok (through it makes the screen strange is that normal for that error)

When i run the disk check i get the error - 

ndisgtk-0.8.3-1.i386.deb failed test.

Does anyone know why this is failing.  I have downloaded and then redownloaded ubuntu and get the same problem.  I have already downloaded ubuntu on a few operating systems so know that bit fair well.  Anyone know whats goingin on?.

Thanks.

---

### Post by ibutho on 2008-07-21
Check the md5sums of the isos and try to burn the isos to disc at a low speed e.g. 4x.

---

### Post by wbutchart on 2008-07-21
> **ibutho said:**
> Check the md5sums of the isos and try to burn the isos to disc at a low speed e.g. 4x.
How do i check that?

---

### Post by ibutho on 2008-07-21
To check the md5sums, you would do
```
md5sum somefile.iso
```
You would then compare the output with the md5sums listed [here]("http://releases.ubuntu.com/hardy/"). If the md5sums are correct, then try burning your discs at a lower speed. If the md5sums are not correct use a download manager to download the isos again.

---


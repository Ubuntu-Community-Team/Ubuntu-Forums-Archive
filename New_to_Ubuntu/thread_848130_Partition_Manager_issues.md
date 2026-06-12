---
title: "Partition Manager issues"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by shawfield on 2008-07-03
I am attempting to install Ubuntu 8.04 alognside my problem PCLinux installation ( keeps freezing ). I have problems with the P{artition menu.

I choose to leave 10% of disk space for the old PCLinuxOS & create a new set of partitions for Ubuntu in the remaining 130 gb.

The partioner gives me an error telling me that problems exist with the disk & I need to 'go back' & resolve those problems before proceeding. 

But when I 'go back', there is no menu item to allow me to correct errors. What is the system actually telling me to do here ?

I had the same problem with my laptop, but because I didnt need any of the files in the existing partition ( windows ) I just used the 'whole disk' option & overwrote everything. I'd rather keep the PCLinuxOS partition if possible.

Thanks

---

### Post by bumanie on 2008-07-03
May be you need to do a fsck - read the man page as to how to. It will check out your disk and will try to fix errors if they exist. > man fsckin terminal.

---

### Post by JohnLM_the_Ghost on 2008-07-03
lame question, but did you assign the **/** and **swap** partitions?

EDIT: The best is to setup your partitions manually with **gparted**
and then just in install set mount points.

---

### Post by shawfield on 2008-07-03
Thanks for the replies.

I didnt manage to get fsck to do anything, so I used the GPARTED app from the boot CD, to do a 'checkdisk' ( sorry for using the language of rival OS's ! ) & it fixed the errors it found.

After that the installation & partitioning went very smoothly & I was very impressed that I was offerred the Nvidia restricted drivers more or less immediately after my first re boot. They installed perfectly. Much better than PClinuxOS, which required me to use synaptics etc etc.  Well done Ubuntu community. Very usable.

Mike

---


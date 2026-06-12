---
title: "downloading packages from a non-linux machine"
date: 2005-01-26
forum: Repositories &amp; Backports
---

### Post by synd7 on 2005-01-26
my laptop has no ethernet and the wireless driver needs to be re compiled each time i upgrade the kernel, stupidly i forgot to dl the kernel headers so i cant recompile it.
i was wondering if i could download the headers from a windows machine and burn them to a cd then install the headers on my ubuntu laptop

any help would be greatly appreciated

---

### Post by az on 2005-01-26
Yes, you can.

The command line for installing a deb package is:

sudo dpkg -i packagenema.deb



so you would do 

cd /media/cdrom
sudo dpkg -i kernel*

---

### Post by synd7 on 2005-01-26
huzaah for me!!!!!! (that the cool lingo \\:D/ )
i found it!
it was in "http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/"

thanks for the info azz

---


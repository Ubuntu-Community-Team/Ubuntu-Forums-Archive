---
title: "can distro be moved from primary to logical - or change primary to logical?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by johnlvs2run on 2008-08-03
I'm planning to add mint, arch, and maybe something else.

What I'd like to do is 
> move ubuntu from #1 to #5, and my files from #1 to #6 
or > make #1 the extended partition;
or > move my files to #6 and reinstall ubuntu to #4.

My current set up is like this:

1- boot partition with ubuntu and files - 40gb
2- 1gb swap
3- extended
. 5 / distro 1 - 17gb
. 6 /home - 20gb
. 7 / distro 2
. 8 /home
. 9 / distro 3
. 10 /home
. 11 / distro 4
. 12 /home
4- /shared - 43gb

What is the best way to go about doing this?

Also, when I put mint in #7, will it know it's files are to go in #8?

---

### Post by spiderbatdad on 2008-08-03
afaik each distro of linux does not need its own /home, one should suffice. I don't think that would work trying to create so many homes, but I've never tried it. Check out gparted live cd for your partitioning needs.

---

### Post by johnlvs2run on 2008-08-03
moving thread to here:
[http://ubuntuforums.org/showthread.php?t=874442](http://ubuntuforums.org/showthread.php?t=874442)

---

### Post by louieb on 2008-08-03
> **johnlvs2run said:**
> 

Also, when I put mint in #7, will it know it's files are to go in #8?

No.  Unless you use the manual partitioning option during the install and tell it to mount #8 as home.

Good dual boot stuff here [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")  
Your going to want to go through the GRUB page. In particular do a find on **configfile** and look at the configfile and chainload options of GRUB. 

With that many distros installed on 1 PC it would be a good idea to use a deicated GRUB partition too. There information on that site about doing that.
Have fun, Good Luck.

---


---
title: "Want to install xubuntu 8.04 but can't backup my MBR"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Greyhoundthethird on 2008-04-25
Hi,

I really want to try xubuntu 8.04, but want to save my MBR of xp just in case it all messes up and xp doesn't boot up!

I went to this website [http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd](http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd) which tells you how to back up your MBR.

However this command doesn't work  - sudo dd if=/dev/hda of=/home/ubuntu/OLDMBR.img bs=446 count=1    

---it says this --- 

'/dev/hda': No such file or directory

How can i get around this problem?

Thanks

---

### Post by gn2 on 2008-04-25
You don't need an MBR back-up.

The "fixmbr" command can re-instate the Windows Xp bootloader.

fixmbr can be run from a variety of different media and there are full instructions for it on Herman's excellent website: [http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)

The Supergrub CD is a tool well worth having, it can run fixmbr and many other useful things, again, there's lots of info about it on Herman's site.

---

### Post by Greyhoundthethird on 2008-04-25
Thanks for the help gn2 :)

---


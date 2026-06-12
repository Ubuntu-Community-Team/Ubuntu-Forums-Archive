---
title: "dual boot xp and ubuntu"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by persia sand on 2008-08-23
ive seen a guide  how to install ubuntu with xp so i can dual boot, in the guide it tells me to make a partition named root   and one named sawp and the other one home.

could i just make two partitions one for xp and one for ubuntu?
cuz i dont really think it would be nessecary to have that many partitions.

guide : [http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

---

### Post by bpowell2005 on 2008-08-23
Those three partitions are just for the Ubuntu installation. When installing XP and Ubuntu, install XP first onto the hard drive, then install Ubuntu. Ubuntu will ask you to resize the hard drive (making a Ubuntu partition and shrinking the XP partition) you can adjust the sizes as you see fit. Let Ubuntu handle the resizing and partition creation. It's worked great for me several times!

I've heard of problems with people trying to install XP after Ubuntu, so I recommend doing XP first.

---

### Post by Too Late on 2008-08-23
A separate home partition is not required. For example, I never make one.

But swap partition is almost mandatory, although Ubuntu will work fine without swap, as long as your RAM doesn't get full. But I can't see any reason why you wouldn't make that one, because it doesn't need to be large.

---

### Post by persia sand on 2008-08-23
so swap is some pagefile?

---

### Post by sandysandy on 2008-08-23
basically root [COLOR="Red"]/[/COLOR] is important. SWAP is recommended if ur RAM is small and also if u need to hibernate. 

see these links on dual booting

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

[http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php](http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php)


de fragement windows, if u need to resize it.

Take BACKUP


regards

---

### Post by persia sand on 2008-08-23
thanks sandy

---

### Post by jamesrfla on 2008-08-23
All I had to do was create a EXT3 partition then a SWAP partition and that is all I had to do when I install Ubuntu 7.04 a long time ago.

---


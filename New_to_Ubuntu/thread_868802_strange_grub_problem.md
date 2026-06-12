---
title: "strange grub problem"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Elric27 on 2008-07-24
Hi. I have this strange problem with, and I can't find any post really related to this particular problem.
I have a tri-boot machine, windowsxp, ubuntu and a third partition where I now have debian installed. I hace installed over this last partition a few times, and edited menu.lst without problems to boot. 
Then, I installed gfxboot, followed the instructions but did setup (hdx) on the windows partition. Grub loaded, only worked with Ubuntu but I ran windowsxp cd with fixboot, and it all went fine.
The thing now is that I can't boot debian now. The menu.lst is the same I used to boot debian before gfxboot, but it says error 2, bad file or directory, when I try to boot debian.
Even stranger, if I do "find /boot/grub/stage1" it returns mistake, as if I didn't have it installed. I know the partion nomenclature is fine in menu.lst. but if I try to "root (hd0,3), that's the sd4 ubuntu partition, is says no device found. device.map shows (hd0) /dev/sda.
The thing is, grub is installed and works with ubuntu, but it can't find itself, only run, but no install grub or anythig. Ubuntu is working, but I would like to regain control on my grub. Oh, super grub cannot load debian either. It also seems to be an initrd problem, (it's when is says error 2) so i wouldn't mind to erase that debian I',ve been playing with, but the fact that my grub dosen't recognize its own archives, or that I cannot run its commands is worrisome. 
I guess root (hd0,3) tells grub where its files are, and setup (hd0) installs it in mbr. however, if i try any of the above, it says invalid device requested, error12. the device hd0 is /dev/sda  in device.map
Thanx and excuse the lengthy post.

---

### Post by Elric27 on 2008-07-24
sorry for replying myself. Forgot to say gfxboot works fine, but I installed it with the .deb , not repository one, since nobody even mentioned it, Can anyone explain how the repository one is different?

---

### Post by phidia on 2008-07-24
> I try to "root (hd0,3), that's the sd4 ubuntu partition, is says no device found. device.map shows (hd0) /dev/sda.

That line is incorrect. Maybe it's a typo? sd4 = (hd3) in grub notation. Maybe you meant to type "sda4" because that would = (hd0,3).
Anyway If you have a correctly burned/downloaded super grub disk and it won't find your debian install that's obviously not good. 

Are you able to mount and view that partition? 

If you boot into the ubuntu install you can mount the debian partition and then sudo chroot to it (read man chroot) from there you might be able to reinstall grub. 

I like to install grub for each install to it's own partition and then use the active menu.lst to chainload the others. Just my preference but it works.

---

### Post by phidia on 2008-07-24
> **Elric27 said:**
> sorry for replying myself. Forgot to say gfxboot works fine, but I installed it with the .deb , not repository one, since nobody even mentioned it, Can anyone explain how the repository one is different?

It's considered better to install from the package manager when possible-for system integrity but in this specific case it probably doesn't make much difference.

---

### Post by Elric27 on 2008-07-24
Hi. Thanx for the help. The sd4 thing was a typo. I could mount the partition and everything. Anyway, I got bored in the meantime and installed Fedora 9 on that partition, installed the grub and chainloaded ubuntu's grub to fedora's bootloader, that's a nice advise.
Anyway, the fact that grub works but dosent' find its own files is still a mystery to me.
Thanx for the help, i think the grub find /boot/grub/stage1 won't work unless I reinstall, though my grub is so messed I think I won't touch it for a while.
Thanx for the support, I'm a newbie and this forum has helped countlessly times, though this is my first post
Cheers

---


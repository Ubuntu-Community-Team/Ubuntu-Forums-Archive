---
title: "[SOLVED] preparation for reinstalling windows XP[while dual booting with UBUNTU]"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by macvr on 2008-08-25
hi, 
i dual boot XP and UBUNTU
i need to reinstall my windows XP,
 i'v read posts saying that grub might be lost, is there anyway to avoid this, 

few questions:
1- will windows recognize ONLY the present alloted NTFS partition, or will it ask for formatting ?
2- will my ubuntu install be unharmed?
3- easiest way of getting back grub to work as it does now?

anything else i should be aware of , before reinstalling

---

### Post by overdrank on 2008-08-25
> **macvr said:**
> hi, 
i dual boot XP and UBUNTU
i need to reinstall my windows XP,
 i'v read posts saying that grub might be lost, is there anyway to avoid this, 

few questions:
1- will windows recognize ONLY the present alloted NTFS partition, or will it ask for formatting ?
2- will my ubuntu install be unharmed?
3- easiest way of getting back grub to work as it does now?

anything else i should be aware of , before reinstalling

Hi and this link may help
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
And of course always **Back up your data** there is always a chance of a mishap. :)

---

### Post by Sunfist on 2008-08-25
I just did exactly what you are going to do, you can read about my problems if you search for my recent posts..something about grub error 17. But to answer your questions, no XP will not reformat the entire disk (unless you tell it to) it cant even see your linux formated partition. You will get a menu (of sorts) that lists the partitions it does see, and it will show the linux partition file type as unknown. Just make sure you pick the old windows partition (probably the NTFS one). It will wipe out grub however. You can try supergrub to reinstall it, which didnt quite work for me, or you can do it manually if you have a live cd. I'd try supergrub, it cant hurt and it might work for you. Then if that fails ask back here and someone can steer you in the right direction to do it manually. SuperGrub worked for me I just had to edit the menu.lst file to get it to work right.

---

### Post by sandysandy on 2008-08-25
see this for installing XP after ubuntu

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

see this for How to restore Grub from a live Ubuntu cd.(XP will overwrite GRUB) 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by macvr on 2008-08-29
sorry guys, i dint realize that i got a reply!!!

i usually set the threads to instantly notify on replies,and check on receiving mail notifications but seem to have missed it with this one!:(

i was just checking my profile,i didnt even know there was a reply till now!

for the reinstallation, i did more search and found similar links to what has been posted above,but didnt find the the above ones!though the solutions were similar

i first tried super grub , but that didnt work for me.

now all is fine with grub,

thankx for the help guys, and once again sorry for missing it

---


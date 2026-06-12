---
title: "grub prompt blues"
date: 2006-09-09
forum: Other OS Talk
---

### Post by hellfried on 2006-09-09
i have been wasting a great amount of time downloading various distros and burning them to cds only to find that i cannot boot into them. i will end up with only a grub prompt and nothing i enter seem to work. this has happened with the current versions of freespire, pclinuxos and simply mepis. i have read various suggestions in the specific forums but come away all confused. is there any surefire way that i can use to boot into these cds?
ubuntu does not seem to be affected by this problem. some have suggested that it is something to do with BIOS. funny thing is that the older version of pclinuxos works fine.

---

### Post by slimdog360 on 2006-09-10
have you tried formatting the hard drive completly? or the section with grub on it?

---

### Post by hellfried on 2006-09-11
> **slimdog360 said:**
> have you tried formatting the hard drive completly? or the section with grub on it?

r u suggesting that i reformat my windows partition where the mbr is? wow that is rather drastic. call me chicken but i am still not totally cut off from windows yet. there r still things that i need to do on my winxp os.

---

### Post by amo-ej1 on 2006-09-11
In order to get this straight. You haven't installed any kind of linux on you hard disc. All you did was download bootable iso's, burn them and try them ? Most of them failed except the ubuntu iso, right ?

If that is the case modifying anything on your harddrive will not work. And the only thing you can do in this case is:
a) ensure the iso's are downloaded correctly and the cd you're burning it on is descent (e.g. fully erase a cd-rw)
b) ensure the bootorder is correct in the bios

and there isn't that much else you can do.


oh and the MBR is not part of any partition, and the mbr is rather empty when  talking about a windows context all it does is 'fall through'.

---

### Post by hellfried on 2006-09-12
i have winxp on sda1, ubuntu dapper on sda3, swap on sda4 and sda5 (logical volume)is empty. with this set up i have tried to boot the burnt iso's but failed. however when i use livecds of kubuntu and edgy eft they boot right up.

---


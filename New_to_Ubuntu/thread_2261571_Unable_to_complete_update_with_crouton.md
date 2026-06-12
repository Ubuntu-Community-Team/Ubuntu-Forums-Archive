---
title: "Unable to complete update with crouton"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by colin.gauthier.bar on 2015-01-19
Hi all,
I am new with Ubuntu and even forum discussions. I successfully installed Unity on my C720 Chromebook a few weeks ago. I tried to update from 12.04 to 14.04 using this : [https://github.com/dnschneid/crouton/wiki/Upgrade-chroot-release](https://github.com/dnschneid/crouton/wiki/Upgrade-chroot-release)

I went through it all and this is what I finally get : 

[COLOR=#444444][FONT=UbuntuRegular]/mnt/stateful_partition/crouton/chroots not found. 
/usr/local/chroots/precise does not exist; cannot update. 
Valid chroots: 

[/FONT][/COLOR][FONT=UbuntuRegular]What does that mean?! Now, when I try to switch from Chrome OS to Unity, I get a black screen.

Thanks for any support.[/FONT][COLOR=#444444][FONT=UbuntuRegular][/FONT][/COLOR]

---

### Post by newbie-user on 2015-01-20
> /mnt/stateful_partition/crouton/chroots not found.This means it cannot find the chroots file/folder in the specified location
> /usr/local/chroots/precise does not exist; cannot update.This means there is no chroot called "precise".

According to the site [https://github.com/dnschneid/crouton/wiki/Upgrade-chroot-release]("https://github.com/dnschneid/crouton/wiki/Upgrade-chroot-release"), when you do a distribution upgrade, the name of the chroot changes. Since you went from precise to trusty, you need to update crouton so that it knows there's a newly named chroot: ```
sudo -e ~/Downloads/crouton -u -n trusty
```

---


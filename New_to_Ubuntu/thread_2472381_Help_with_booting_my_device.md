---
title: "Help with booting my device"
date: 2022-02-25
forum: New to Ubuntu
---

### Post by thebear1 on 2022-02-25
So recently i have installed Ubuntu on my LENOVO IdeaPad Duet 3 10IGL5-872 with Intel Celeron N4020 - RAM: 4 GB - 64 GB eMMC - Intel UHD Graphics 600 hibrid laptop  and my first boot was completely fine. But when i tried to do a second boot something happened to the system and i can not boot into the laptop. Plus whenever i boot from the flash drive it tells me that there's a file missing and that might cause some errors.
Here is the the link of the boot repair that i did from the live USB---> [https://paste.ubuntu.com/p/Tqm5T8jsd7/](https://paste.ubuntu.com/p/Tqm5T8jsd7/)
Here is what the screen looks like---> [https://imgur.com/gallery/zGt8aEH](https://imgur.com/gallery/zGt8aEH)

---

### Post by oldfred on 2022-02-25
That looks like a graphic driver issue, but normally Intel video just works.
Does live installer work ok?

Can you boot recovery mode?
You set grub timeout to 0, so may not be able to get to grub menu as you do not have any time to press escape key to get menu.
I use 3 sec for timeout but have to be quick if I want menu.

Have you updated UEFI firmware? That may fix some issues.

Also with a lightweight system, often better to use a lightweight distribution.
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
Ubuntu's community for flavors:
[https://wiki.ubuntu.com/RecognizedFlavors](https://wiki.ubuntu.com/RecognizedFlavors)

I found Kubuntu a middleweight system to work well even on my very old 2006 system that would not even load full Ubuntu.

---

### Post by thebear1 on 2022-02-26
The live installer works good on both that laptop and my other laptop and i can boot the recovery mode as well. I haven't updated the UEFI firmware so i'll try to do that as well. In terms of the lightweight distros i'll look into one that i might like and try it out.

---


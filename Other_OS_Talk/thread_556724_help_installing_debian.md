---
title: "help installing debian"
date: 2007-09-21
forum: Other OS Talk
---

### Post by wolfen69 on 2007-09-21
i have installed debian before, but it was on a pc that had only 1 HD. now i want to install it on my main PC. i have 4 hard drives: 3 sata/1 ide. 1 with ubuntu. 1 with xp. 1 for storage. and 1 i want debian on.

however, when i install debian, i boot to it, grub starts, i choose the debian drive and get error 17. i cant boot to any of the OS's listed. same error every time. 

why doesnt debian like being on the same machine as other OS's?. ive tried re-installing many times. nothing works. btw, debian is the only distro that gives me problems. thanks.

---

### Post by Mud.Knee.Havoc on 2007-09-21
With over 1000 posts, I'm sure you've already googled it, but [here's a possibility]("http://ubuntuforums.org/showthread.php?t=442945").

---

### Post by kerry_s on 2007-09-21
what installer are you using?
did you burn the cd as a image at 4x, any faster can give you bad burns.

gnome net installer-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

kde-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-kde-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-kde-CD-1.iso)

xfce4-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

type> installgui <for the pretty installer

---

### Post by wolfen69 on 2007-09-21
yeah, i saw that and tried it, but still same error. i've never had a grub error before, so i'm not really up on any fixes. i tried google, but still nothing. i even tried the debian forums. that was as fruitful as asking a linux question in a windows forum.

i'm going to re-install for a 6th time. i'll be back.

---

### Post by wolfen69 on 2007-09-21
yes i burned at 4x, checked MD5 and verified burn. i'm trying to load regular etch.

---

### Post by wolfen69 on 2007-09-21
i got it. i re-installed and found out that it installs grub to hd0, which is my xp drive. i set the bios to boot to xp first and the grub menu came up and everything works great. one more thing i know now. peace.

---

### Post by danny joe ritchie on 2007-09-22
I am happy to see that you found the answer, I am going to try to reinstall Debian on my system in a couple of weeks !

---


---
title: "Upgrade with no CD"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2008-11-28
I'm trying to upgrade but lost my CD.


What can i do...i can't even find xubuntu 7 to download

---

### Post by overdrank on 2008-11-28
> **AutumnPhoenix said:**
> I'm trying to upgrade but lost my CD.


What can i do...i can't even find xubuntu 7 to download

Hi and what version are you trying to upgrade from and xubuntu Feisty 7.04 has reached the end of life.

---

### Post by kestrel1 on 2008-11-28
What are you trying to upgrade to & from what?
More info is required

---

### Post by AutumnPhoenix on 2008-11-28
I know 7 has reached end of life.

I have 7 but it won't let me upgrade to 8 without my CD

---

### Post by AutumnPhoenix on 2008-11-28
Failed to fetch cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by kestrel1 on 2008-11-28
Try this link:
[http://cdimage.ubuntu.com/xubuntu/releases/gutsy/release/](http://cdimage.ubuntu.com/xubuntu/releases/gutsy/release/)

---

### Post by AutumnPhoenix on 2008-11-28
bump

---

### Post by Kareeser on 2008-11-28
Follow the instructions here:
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

We can't give you detailed help because we **don't know what version you are using**. Ubuntu 7.04 or 7.10?!

---

### Post by handydan918 on 2008-11-28
post the output of  ```
cat /etc/apt/sources.list
```

---

### Post by kestrel1 on 2008-11-28
Did you try the link above for the 7.10 CD?
If its the 7.04 CD you need look here:
[http://download.chip.eu/en/download_getfile_en_2038065.html?s=http://dl01.chip.eu&f=/44927/xubuntu-7.04-alternate-i386_en.iso&t=49307311&sign=403580c2b1cbe48e0a5d41bc1f884560&dl_type=dl_hs](http://download.chip.eu/en/download_getfile_en_2038065.html?s=http://dl01.chip.eu&f=/44927/xubuntu-7.04-alternate-i386_en.iso&t=49307311&sign=403580c2b1cbe48e0a5d41bc1f884560&dl_type=dl_hs)

---

### Post by halitech on 2008-11-28
> **handydan918 said:**
> post the output of  ```
cat /etc/apt/sources.list
```

to go one step farther, once we see your sources.list file we probably just need to comment out the lines for your cd so it doesn't look for it anymore

---

### Post by AutumnPhoenix on 2008-11-28
> deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


this is the output

---

### Post by AutumnPhoenix on 2008-11-28
what should I do next?

---

### Post by halitech on 2008-11-28
press ALT-F2 to get a run window and type in 
```
gksu gedit /etc/apt/sources.list
```
and put a # in front of ```
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

this will stop it from looking for your cd

---

### Post by AutumnPhoenix on 2008-11-28
-could not save file /etc/apt/sources.list
Unexpected error: File not found

---

### Post by halitech on 2008-11-28
did you prefix the command with gksu?

---

### Post by AutumnPhoenix on 2008-11-28
yeah, it opened up a big white box in which I typed the other command

---

### Post by halitech on 2008-11-28
type it all in together

---

### Post by AutumnPhoenix on 2008-11-28
> sudo: unable to resolve host PhoenixWolf

thats what it does now...how do I resolve my host?

thanks for sticking with me :)

---

### Post by halitech on 2008-11-28
can you post the output of
```
cat /etc/hosts
```

---

### Post by AutumnPhoenix on 2008-11-28
> # The following lines are desirable for IPv6 capable hosts
127.0.1.1 phoenixwolf-n


this is what it sais

---

### Post by halitech on 2008-11-28
ok, I see a problem. time to make some notes cause you will need to reboot into recovery mode since sudo isn't working.

1. Reboot into recovery mode.
2. nano /etc/hosts
 - add 127.0.1.1   localhost
 - save and reboot
3. try the previous command and see if sudo is working

---

### Post by AutumnPhoenix on 2008-11-28
how do i reboot into recovery mode?

---

### Post by halitech on 2008-11-28
reboot and when you get to grub, you should see an option for recovery mode or single user mode (not sure on the wording) if you select that it will take you to a command line system. You may need to hit esc to see all the grub options.

---

### Post by kestrel1 on 2008-11-29
You may need to press the esc key to see the grub menu, just after post has finished.

---


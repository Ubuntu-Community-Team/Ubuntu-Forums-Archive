---
title: "Upgrading to 8.04 from 7.10 problems HELP!!"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by chaddiesel on 2008-09-25
Well, I've attempted to upgrade to 8.04 with horrible results......I've started a thread in another place with no help.:confused:

[http://ubuntuforums.org/showthread.php?t=819596](http://ubuntuforums.org/showthread.php?t=819596)

I'm hoping that someone will have some sort of information (even if it's re-install 7.10). I don't want to reinstall 7.10 again because I've gotten MatLab working and want it in 8.04. Also, I want 8.04 so that I can use the latest version of wine and install Steam. :)

---

### Post by Primefalcon on 2008-09-25
if you have too many issues try going to shipit and requesting their cd

as for the upgrade command

```
sudo apt-get dist-upgrade
```

---

### Post by kansasnoob on 2008-09-25
I've had only about a 50% success rate with distribution upgrades, therefor I don't even try anymore.

I always just burn the new CD and do some repartitioning to allow for the new install. Like if you look at my screenshot:

[ATTACH]86354[/ATTACH]

You see sda1 is windows, I then use an extended partition for my Linux stuff (so I don't have to worry about the 4 primary partition limit), but sda5 is 8.04 and sda7 is 8.10 Alpha6. 

Should I decide to keep 8.10 after final release I'll just remove sda5 and it's SWAP (sda6), or if I decide to just stick with 8.04 I'll restore Grub to it and ditch the new Intrepid (doubtful because I'm very impressed so far).

---

### Post by chaddiesel on 2008-09-25
I would love to be able to install 8.04 with the live CD but everytime I try the partitioner never loads the partitions that exist already. Has anyone fixed this problem?

---

### Post by kansasnoob on 2008-09-25
I always "pre-partition" using gparted (aka: Partition Editor) from the Live CD. Like when I installed Intrepid Alpha I shrunk my sda5, then moved sda6 right next to it, then shrunk the extended partition (sda2).

That left me with about 20GB of free space, totally unformatted (greyed out) free space. Then when I installed and got to screen where it gives four choices:

> Guided resize and use freed space
Guided - use entire disk
Guided - use the largest continuous free space
Manual

I just make sure to choose "Guided - use the largest continuous free space".

But it all depends on what kind of installation you're doing.

---

### Post by prshah on 2008-09-25
> **chaddiesel said:**
> 
[http://ubuntuforums.org/showthread.php?t=819596](http://ubuntuforums.org/showthread.php?t=819596)



Based on that (locked) thread, at the busybox prompt, hit Ctrl+D to continue booting; if it fails, post the error message(s) displayed.

---

### Post by chaddiesel on 2008-09-25
I went ahead and tried to reboot this morning and hitting Ctrl+d after the error message but it displays the exact same message again. Nothing happens it's just at a stand still.

As far as the partitioner with the 8.04 live cd.....I'm used to doing it manually because I have my HDD seperated in two parts with windows and linux. I'm almost afraid to let it do any thinking for me on that part.

---


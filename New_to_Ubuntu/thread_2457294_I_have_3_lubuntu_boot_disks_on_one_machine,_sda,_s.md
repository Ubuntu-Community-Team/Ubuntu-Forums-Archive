---
title: "I have 3 lubuntu boot disks on one machine, sda, sdb, sdc, how so set which to use?"
date: 2021-01-29
forum: New to Ubuntu
---

### Post by jleslie48 on 2021-01-29
[COLOR=#242729][FONT=Arial]BLUF: I have 3 boot disks on a single machine, how do I pick which one I boot from, or more directly, what do I change on what partition of two of the disks to keep those disks from being the boot disk?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]We have 2 identical machines. each is running lbuntu 16.04. each has slots for 4 disk drives and each has 2 identical 1tb drives for a total of 4 1tb drives. When the machines boot up. the bood device is sda (/sda3) and there are 3 partions, sda1, sda2, sda3. The second disk comes in as sdb, it is unmounted and is unused, brand new. The only differences between the machines is one uses a static address of 192.168.1.104, and the other is using a static address of 192.168.1.105 we'll call them machines 104 and 105.
I figured out how to identify which disks are which so I label the sda and sdb disks on both machines. Now I take the disk out of the 105 machine, and put it in the third slot of the 104 machine. When I boot 104 now, with fdisk -l I can see I have 3 disks: sda, sdb, and sdc. I also see that only sda is mounted, and I also know the ip address is .104, so I know that sda is the 104 machine. I also see that sdc has 3 partitions so I even without it mounted, that sdc is the boot disk from the 105 machine.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I then do a dd clone disk of sdc to sdb.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I then remove the 104 boot disk (sda) and the 105 boot disk (sdc) and leave the clone of of 105 (sdb) in the machine and reboot. I am very happy as the machine boots with ip address 105 (since its a clone of the 105 machine,) and then change its static ip address to 106. We should note that since I only have the one drive in the machine, it is coming in as sda.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I then put the 104 boot disk in a slot, and the 105 boot disk in a slot, and reboot the machine. It boots off the new 106 boot disk, on sda, and the two other disks are unmounted as sdb and sdc.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I do not care about the sda, sdb, or sdc device association particularly, but I do want to be able to set which device is the one I boot from. How do I do this?[/FONT][/COLOR]

---

### Post by guiverc on 2021-01-29
Lubuntu 16.04 LTS being a *flavor* of Ubuntu had only 3 years of supported life

- [https://lubuntu.me/xenial-5-released/](https://lubuntu.me/xenial-5-released/)
- [http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)

which ended 2019-April.

Ubuntu 16.04 LTS Server (no desktop) or Desktop (Unity 7), & Ubuntu-Kylin have 5 years of supported life and are still supported. Refer release notes, or use `ubuntu-support-status` or your own system to confirm this is the case. I suggest you move to a supported release of Lubuntu for security reasons, unless you're off-line or are aware of risks.

How disks are detected is controlled by BIOS/uEFI configs (ie. sda, sdb, sdc etc), the same BIOS/uEFI also controls which of those is booted from, or in other words its hardware/firmware controlled and specific to your boxes. Some boxes provide great control, others have a simpler functions (*just as some allow boxes to be controlled remotely; IDRAC/IPMI/iLO* etc)

Lubuntu 16.04 LTS is however *end-of-life*.

---

### Post by grahammechanical on 2021-01-29
You will need to read the motherboard user manual for each machine to understand the settings in UEFI settings utility and how to change them. It would not be wise for someone else to give you line by line instructions. Without having a copy of the motherboard manual. Otherwise, they may give inaccurate instructions.

If you do not have a motherboard manual you could visit the motherboard manufacturer's web site. They may offer a PDF version that you can download. Have you never entered the UEFI settings utility even out of curiosity?

Regards

---

### Post by guiverc on 2021-01-30
Question can also be found at [https://askubuntu.com/questions/1312306/i-have-3-lubuntu-bootable-disk-drives-on-one-machine-sda-sdb-sdc-how-can-cho](https://askubuntu.com/questions/1312306/i-have-3-lubuntu-bootable-disk-drives-on-one-machine-sda-sdb-sdc-how-can-cho)

---

### Post by cwmoser on 2021-01-31
If you have cloned those disks, do make sure you have unique UUIDs else Ubuntu will have trouble with which one to boot.

---

### Post by jleslie48 on 2021-01-31
@cwmoser, thank you.    how I do I change the UUID's and then define which one to boot?

---


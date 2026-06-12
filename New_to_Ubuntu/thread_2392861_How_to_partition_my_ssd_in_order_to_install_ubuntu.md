---
title: "How to partition my ssd in order to install ubuntu 17.10"
date: 2018-05-26
forum: New to Ubuntu
---

### Post by simone93 on 2018-05-26
Good morning to everyone,
i' ve already tried to install ubuntu 17.10 on my ssd (Samsung 860 evo, 250 Gb), but i was unlucky because it overheats, firefox doesn't run properly and i wasn't able to mount the /home on the HDD.
So i wanted to ask you for help, in particular** how to install ubuntu 17.10 on ssd ( focusing on the partition) and how to put the /home on the HDD.**
I've an Asus X541UV and for installation it needs UEFI mode.

Thanks in advance, tell me if you need other informations.

---

### Post by TheFu on 2018-05-26
Support for 17.10 ends in about 6 weeks.  Might want to start with a different OS at this point.  That's either 16.04 (lots of guides, most issues  solved), or 18.04.  Both are LTS releases, unlike 17.10.

All Ubuntu installs are basically the same. When the partitioning options are shown, you want to select "do something else", then use the provided tool to manually layout which partitions are used for what. You'll need to understand disk and partition naming to avoid problems. You'll need to know which device is your SSD and which device is the HDD.

It isn't clear if you want to wipe everything and start fresh, or if you just want to move the current /home off the SSD over to the HDD.  There's a guide for that somewhere. Let me google it: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by simone93 on 2018-05-26
Thanks for your answer.
i've already tried to install ubuntu 18.04 LTS, but during the installation it freezes and i can't move on, so i've decided to install 17.10 and after upgraded to 18.04... but if you know how to solve my problem i' m very happy for it. 
I' ve to install in UEFI mode i don't know how to partition it in a proper way, i do:
-dev/sda1 560MB in efi partition;
-dev/sda2 560 in ext4 for /boot ;
-dev/sda3 220 Gb in ext4 for / ;
unallocated 20 Gb for ssd overprovisioning ;

-dev/sdb1 1Tb in ext4 for /home.
dev/sda is the ssd and dev/sdb is HDD.

But it doesn't work.

Are you suggesting to install the /home in the ssd and moves it in an other moment?

---

### Post by oldfred on 2018-05-26
Your partitioning is ok, you probably do not need separate /boot partition. I often do not allocate entire drive initially, but I have an idea of how much data I need for partitions now after years of use.
 
I prefer smaller / (root) partition (25 to 30GB), primarily as I like to have multiple installs of Ubuntu and create a shared data partition, but do not share /home.
I have on one system all three LTS versions which all still boot. I primarily have working system and then have install of newer system to see changes before converting it to be main working system.

Google says specs vary by country, but show nVidia? Do you have nVidia for video?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You will need nomodeset after install and until you install nVidia proprietary driver.
Do not install nVidia driver directly from nVidia. Use Ubuntu repository. If you have very new nVidia card/chip, you may need ppa.
       
 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
Fermi based should use 390.xx not newer
[https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus](https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus)

---

### Post by simone93 on 2018-05-26
> **oldfred said:**
> Your partitioning is ok, you probably do not need separate /boot partition. I often do not allocate entire drive initially, but I have an idea of how much data I need for partitions now after years of use.
 
I prefer smaller / (root) partition (25 to 30GB), primarily as I like to have multiple installs of Ubuntu and create a shared data partition, but do not share /home.
I have on one system all three LTS versions which all still boot. I primarily have working system and then have install of newer system to see changes before converting it to be main working system.

Google says specs vary by country, but show nVidia? Do you have nVidia for video?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You will need nomodeset after install and until you install nVidia proprietary driver.
Do not install nVidia driver directly from nVidia. Use Ubuntu repository. If you have very new nVidia card/chip, you may need ppa.
       
 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
Fermi based should use 390.xx not newer
[https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus](https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus)

Thanks for your detailed answer.
Yes, my pc has a NVIDIA geforce 920mx. (during installation i have to skip "install third party software for graphics and wifi hardware" option ?)
So, if i replace nomodeset in my boot options could I be able to install ubuntu 17.10 (or better 18.04) without separated /boot partition?
Can it solves freezing problems for ubuntu 18.04?

My new partition table will be:

-dev/sda1 560MB in efi partition;
-dev/sda3 50 Gb in ext4 for / ;
-unallocated 20Gb for ssd overprovisioning ;
-the remaing ~180Gb ?? (i want only one ubuntu installation)

-dev/sdb1 1Tb in ext4 for /home.

---

### Post by oldfred on 2018-05-26
My one build has 128GB SSD, and I do not use all of it.
My newest build has a 250GB SSD and I do not know what to do with all the space. I do store some info I do want on faster drive in a data partition or two but have most of my data on HDD in several partitions.

Freezing can be nVidia driver issue or you may need additional boot parameters.
My one system with nVidia, I only eventually figured out the boot parameter, as I noticed flash drive  was still working, but monitor was off.

Some model Asus have needed additional boot parameters or other settings.
Almost all systems need UEFI updated, not just to install Linux but for KPTI/Retpoline for Meltdown/Spectre mitigation which requires updated kernels & UEFI/BIOS for most newer systems.
Note that UEFI update resets many settings back to defaults. I have many settings I have to redo after a UEFI update, so I keep a list.

       ASUS VivoMini UN45 UEFI update required to see NVMe drive
[https://ubuntuforums.org/showthread.php?t=2355295](https://ubuntuforums.org/showthread.php?t=2355295)
Asus/Samsung problem with every NVME SSD and G752! 
[https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551](https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551)
[http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04)
Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/)
Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)

---

### Post by TheFu on 2018-05-26
"but it doesn't work" is a little vague about the 17.10 install failing.  Can you clarify?
 
A few ideas.   You must tell the installer to use each partition, in the specific way you want. I find it easier to let the automatic installer do what it does, then come back and fix it later.  That's me. Others will have different choices.  Pay now or pay later choice.

I'm with Oldfred (as usual).  / should be 15G-25G.  Making it larger just isn't necessary.  If you need more space than that, then you should setup the extra partition(s) for that extra space and mount it where needed.  
For example, if you use virtual machines, the default location for those is /var/lib/libvirt/ ... so making /var/ large enough for your VM needs makes perfect sense or you could add a mounted partition directly to /var/lib/libvirt/.   Mount points for a partition can be on any directory, doesn't matter how deep it is.  So the mount point for the efi partition is /boot/efi ... 

For me, the way I setup partitions (or logical volumes under LVM) is all about my backup requirements. Backing up the OS is very different from backing up virtual machines or media files, so I keep those things in different partitions. Logical Volumes, LVs, most of the time can be treated just like a partition, just 100x more flexible.

On my development laptop (perl webapps), I have 38G used, which includes 31G in my HOME.  So ... the OS is just 8GB.   See why Oldfred and I are recommending much smaller / partitioning?  You'll never use 50G and I doubt you'll use even 25G.  I **never** have, not for the OS and applications.

Linux isn't Windows.

OTOH, Java (libraries) is known to suck a bunch of storage, which is why you'd put that onto the HDD and maybe into the HOME.  I'd start with 100G to begin, not the full 1T.  That way as storage gets tight, you'll have clear warnings. If using LVM, then added more storage to a specific LV is pretty quick and easy. With partitions, a little pre-thought can be helpful.  Leave 10-20G empty between every partition, so you can add some quickly when you first run out and plan to migrate to larger quickly. LVM is much more flexible and less wasteful, but a little more complex.

I did Android development for about a year, which I don't do anymore.  On the server-side, we didn't use Java and needed only a few GB for development. On the client-side, all the tools and different versions of the different tools did suck up about 20G pretty quickly, but this was in my development area, not the OS/applications areas.

But only you know the real requirements.

---

### Post by simone93 on 2018-05-27
TheFu > **simone93 said:**
> I' ve already tried to install ubuntu 17.10 on my ssd (Samsung 860 evo, 250 Gb), but i was unlucky because it overheats, firefox doesn't run properly and i wasn't able to mount the /home on the HDD. this are the problems that i've with the ubuntu 17.10 installation. Talking about how to partition the SSD I must admit that I was unprepared and for this reason I was asking you... Now i undestrand that i don't need too much space for the SO, thanks a lot.


I tried to install the nVidia driver as oldfred suggested but when i restarted my pc appear an error screen "pcie bus error severity=corrected type=physical layer id=00e5(receiver id)" and doesn't go on. 
Is it possible that i've to change the grub option NOMODESET with QUIET SPLASH before restarting the pc ?

Before installing ubuntu i would like to be sure of what i have to do, I really appreciate your help!

---

### Post by TheFu on 2018-05-27
Someone else will need to help with install and GPU issues.  I've been using Intel integrated GPUs for the last 8 yrs, so those issues aren't something I've had to deal with in a very long time.

Plus, I just moved to 16.04 from 14.04 last Feb on most of my systems.  I haven't been an early adopter in a very long time - 1990s. *New* is the enemy of *stable*. That applies to using new-to-the-world hardware too.

---

### Post by oldfred on 2018-05-27
Have you updated UEFI from Asus?

For Asus I have seen several other boot parameters that may be required.
You may need to experiment on which one, or combination.
Many Asus have needed: pci=nomsi to prevent run-away log files filling drive.

pcie_aspm=off
[https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

reported as bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173)
May be fast boot setting in UEFI?

 ASUS X540U pci=noaer instead of pci=nomsi and it also worked
[https://ubuntuforums.org/showthread.php?t=2391201](https://ubuntuforums.org/showthread.php?t=2391201)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)

---

### Post by simone93 on 2018-05-27
> **TheFu said:**
> Someone else will need to help with install and GPU issues.  I've been using Intel integrated GPUs for the last 8 yrs, so those issues aren't something I've had to deal with in a very long time.

Plus, I just moved to 16.04 from 14.04 last Feb on most of my systems.  I haven't been an early adopter in a very long time - 1990s. *New* is the enemy of *stable*. That applies to using new-to-the-world hardware too.

I understand what are you saying and you convinced me, i've installed ubuntu 16.04.4 LTS, because i need a stable OS... I'm waiting for ubuntu 18.04.1 at least.

> **oldfred said:**
> Have you updated UEFI from Asus?

For Asus I have seen several other boot parameters that may be required.
You may need to experiment on which one, or combination.
Many Asus have needed: pci=nomsi to prevent run-away log files filling drive.

pcie_aspm=off
[https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

reported as bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173)
May be fast boot setting in UEFI?

 ASUS X540U pci=noaer instead of pci=nomsi and it also worked
[https://ubuntuforums.org/showthread.php?t=2391201](https://ubuntuforums.org/showthread.php?t=2391201)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)

The fast boot is disabled.

Now i've ubuntu 16.04.4 and i do not have the same problems but i'am looking for the best boot parameters for my pc.
I want to optimize the use of SSD, e.g., introducing noatime option in the fstab file ... i've to create a new post or i can use this ?

Thanks a lot to oldfred and TheFu =)

---

### Post by simone93 on 2018-05-27
```
systemd-analyze
Startup finished in 4.493s (firmware) + 4.249s (loader) + 2.956s (kernel) + 2.318s (userspace) = 14.017s

```

Why my pc takes time to startup firmware and loader ?? With the HDD it didn't, it only started kernel and userspace.
It's normal with SSD or can i do something ?

---

### Post by oldfred on 2018-05-27
That may be the fast start up time?
Once configured and you are not changing things you can experiment with turning it back on.
My Asus motherboard has fast start up but also settings for delay so you can still have time to press a key to reconfigure system.

 [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) 


I primarily do just noatime in fstab. And relatime for hard drive partitions.

I do not put swap on SSD, but new version uses swap file not swap partition.
And I have a lot of RAM, so add /tmp in fstab to mount in RAM.
I often do my own daily task for trim.  Note that trim is erasing data on drive, so then you can not use tools like photorec to recovery data. If just / (root) I do not care as I will just reinstall. But if you have other data, be sure to have good backup procedures. TheFu has lots of good suggestions on backup.

---

### Post by TheFu on 2018-05-28
> **simone93 said:**
> ```
systemd-analyze
Startup finished in 4.493s (firmware) + 4.249s (loader) + 2.956s (kernel) + 2.318s (userspace) = 14.017s

```

Why my pc takes time to startup firmware and loader ?? With the HDD it didn't, it only started kernel and userspace.
It's normal with SSD or can i do something ?

The only startup I've seen that was faster was on a chromebook and that's where the OS it custom built exactly for the hardware used.  Standbye mode is almost instant on most devices.  I know it works on mine.  I don't use hibernate due to security considerations.
Mine: 
```
$ systemd-analyze 
Startup finished in 30.756s (kernel) + 8.166s (userspace) = 38.922s
```

Run **systemd-analyze blame** to see where time is being spent.

---

### Post by simone93 on 2018-05-28
I would like to thank you again, I really appreciated your advice!!

Right now I finished installing ubuntu 16.04.4 with all the ssd optimizations, i was also able to install the nvidia drivers, setting in the file /etc/default/grub the option pci=nomsi (the only one that works) =)

Talking about systemd command:
```
systemd-analyze 
Startup finished in 3.157s (firmware) + 4.442s (loader) + 2.186s (kernel) + 1.557s (userspace) = 11.343s
```

```
systemd-analyze blame
          1.748s fwupd.service
           783ms dev-sda3.device
           510ms systemd-backlight@backlight:intel_backlight.service
           180ms networking.service
           175ms systemd-fsck@dev-disk-by\x2duuid-0f3002d7\x2ddfd3\x2d4cd7\x2dbf
           159ms snapd.service
           144ms apparmor.service
           140ms systemd-logind.service
           135ms accounts-daemon.service
           128ms systemd-rfkill.service
           115ms irqbalance.service
           114ms lightdm.service
           109ms NetworkManager.service
           109ms plymouth-read-write.service
           108ms grub-common.service
           105ms bluetooth.service
            98ms ondemand.service
            88ms systemd-fsck@dev-disk-by\x2duuid-BA33\x2d3B31.service
            86ms user@1000.service
            85ms speech-dispatcher.service
            84ms preload.service
            83ms plymouth-quit-wait.service
            72ms systemd-fsck@dev-disk-by\x2duuid-35bac354\x2dd693\x2d4c3f\x2d94
            71ms apport.service
            69ms gpu-manager.service
            68ms console-setup.service
            62ms systemd-udev-trigger.service
            59ms udisks2.service
            56ms systemd-journald.service
            52ms keyboard-setup.service
            48ms alsa-restore.service
            43ms systemd-user-sessions.service
            43ms pppd-dns.service
            39ms rsyslog.service
            37ms home.mount
            37ms upower.service
            36ms systemd-timesyncd.service
            33ms systemd-udevd.service
            33ms plymouth-start.service
            31ms systemd-update-utmp.service
            28ms setvtrgb.service
            25ms avahi-daemon.service
            21ms systemd-modules-load.service
            20ms polkitd.service
            18ms user@108.service
            17ms boot.mount
            17ms systemd-tmpfiles-setup-dev.service
            15ms thermald.service
            15ms systemd-update-utmp-runlevel.service
            15ms systemd-update-utmp-runlevel.service
            13ms systemd-journal-flush.service
            13ms boot-efi.mount
            12ms systemd-sysctl.service
            11ms dev-hugepages.mount
            10ms ufw.service
            10ms sys-kernel-debug.mount
            10ms dev-mqueue.mount
            10ms resolvconf.service
             7ms dev-disk-by\x2duuid-811f3d22\x2dea79\x2d44eb\x2d8dee\x2df3fda3b
             7ms colord.service
             7ms dns-clean.service
             7ms systemd-tmpfiles-setup.service
             6ms kmod-static-nodes.service
             6ms systemd-random-seed.service
             5ms wpa_supplicant.service
             5ms sys-fs-fuse-connections.mount
             4ms systemd-remount-fs.service
             4ms ureadahead-stop.service
             4ms rtkit-daemon.service
             2ms nvidia-persistenced.service
             2ms snapd.socket
             1ms sys-kernel-config.mount
             1ms rc-local.service
```

```
 systemd-analyze critical-chain 
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @1.524s
&#9492;&#9472;multi-user.target @1.524s
  &#9492;&#9472;getty.target @1.524s
    &#9492;&#9472;getty@tty1.service @1.523s
      &#9492;&#9472;rc-local.service @1.435s +1ms
        &#9492;&#9472;network-online.target @1.434s
          &#9492;&#9472;network.target @1.434s
            &#9492;&#9472;networking.service @1.253s +180ms
              &#9492;&#9472;apparmor.service @1.108s +144ms
                &#9492;&#9472;local-fs.target @1.106s
                  &#9492;&#9472;home.mount @1.067s +37ms
                    &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-0f3002d7\x2ddfd3\x2d4cd7\
                      &#9492;&#9472;dev-disk-by\x2duuid-0f3002d7\x2ddfd3\x2d4cd7\x2dbfd5\x2d
```

I think it's all right!


I partitioned my pc in this way:
```
sudo fdisk -l
[sudo] password for simone: 
Disk /dev/sda: 232,9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 32A78EBD-1672-432C-B9ED-259493820E19

Device       Start      End  Sectors  Size Type
/dev/sda1     2048  1093631  1091584  533M EFI System
/dev/sda2  1093632  2187263  1093632  534M Linux filesystem
/dev/sda3  2187264 97771519 95584256 45,6G Linux filesystem


Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 5F9ED7D6-B174-4D65-8875-600FFD121419

Device        Start        End    Sectors   Size Type
/dev/sdb1      2048   46874623   46872576  22,4G Linux swap
/dev/sdb2  46874624 1894930431 1848055808 881,2G Linux filesystem
```

Before changing the thread title in [Solved], I wanted to ask if I could set up hibernation without problems for the SSD, since the SWAP partition is in the HDD and if so how?

---

### Post by oldfred on 2018-05-28
I would not use hibernation, it may not even speed boot as SSDs are so fast now.
And many systems seem to have issues with hibernation.

Your 11 sec boot is fast.

---

### Post by simone93 on 2018-05-28
Thanks a lot! :D

---

### Post by simone93 on 2018-06-18
> **simone93 said:**
> ```
systemd-analyze
Startup finished in 4.493s (firmware) + 4.249s (loader) + 2.956s (kernel) + 2.318s (userspace) = 14.017s

```

Why my pc takes time to startup firmware and loader ?? With the HDD it didn't, it only started kernel and userspace.
It's normal with SSD or can i do something ?

Good morning,
i solved this problem, just upgrade bios version from 300 to 305, using the official guide [https://www.asus.com/support/FAQ/1008859/](https://www.asus.com/support/FAQ/1008859/) .
Now this is my boot time:
```
systemd-analyze
Startup finished in 2.789s (kernel) + 1.671s (userspace) = 4.460s

```

Maybe this can helps someone.

---


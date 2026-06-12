---
title: "Problem installing double boot windows 7 / Ubuntu 12.10 on Sony Vaio"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by gbgb on 2013-01-22
Hi,

Level: total beginner.
I am trying to install Ubuntu 12.10 on my Sony Laptop with a windows 7 pro pre installed.
Unfortunately, the installation freeze on the second screen (when being asked to plug / size disk / Internet connection)
I am using the Ubuntu-64-remix.
Being a total beginner, I have followed the advise on the forum and ran a boot info via the boot checker : [http://paste.ubuntu.com/1529463](http://paste.ubuntu.com/1529463)

Could you plead advise on the next steps ?
Please let me know if you need more information (config / version )

Many thanks,
G.

---

### Post by irv on 2013-01-22
Can you boot into the live session? to make sure all your hardware is working with Ubuntu.

---

### Post by gbgb on 2013-01-22
Hi irv,
I can boot into the live session without any problem
G.

---

### Post by oldfred on 2013-01-22
Are you booting live installer in UEFI mode not BIOS mode. Your Windows is in UEFI with gpt partitioning and you need to install Ubuntu in UEFI mode.

It looks like you created swap and two ext3 partitions, I might use ext4, but it should work with ext3.

It looks like Boot-Repair wanted to run fsck on your partitions which indicated some sort of file corruption. Does install see drive ok now? You need to use Something Else or manual install and choose the partitions you have created, what format and what mount point.

I think these were with the older version of grub2, with 12.10 it works with secure boot and Windows 8 most of the time.
       Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)
Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)

---

### Post by gbgb on 2013-01-23
> **oldfred said:**
> Are you booting live installer in UEFI mode not BIOS mode. 
I am booting in UEFI 

> **oldfred said:**
> It looks like you created swap and two ext3 partitions, I might use ext4, but it should work with ext3.
ok

> **oldfred said:**
> It looks like Boot-Repair wanted to run fsck on your partitions which indicated some sort of file corruption. Does install see drive ok now?

Not sure what you mean by that.
Do you want me to run a fsck on my partitions?

> **oldfred said:**
> You need to use Something Else or manual install and choose the partitions you have created, what format and what mount point.
What do you mean by something else?
I will look on how to perform a manual install.

> **oldfred said:**
> I think these were with the older version of grub2, with 12.10 it works with secure boot and Windows 8 most of the time.
       Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)
Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)

Thanks a lot for all those references, I will start to read them and post whenever I am stuck.

G.

---

### Post by oldfred on 2013-01-23
SomeThing Else is on of the install options, it is the manual install that gives the option of manually creating & formatting partitions, adding more than just the default / (root) & swap and choosing where to install the grub2 boot loader. But with UEFI boot loader should auto install to efi partition.

If you can see partitions ok, then you should not need a fsck. Not sure why Boot-Repair did that, but maybe because it could not see install.

When you boot the flash drive or DVD to install it should give two options to boot, one UEFI and the other legacy/BIOS/CSM or whatever it calls it. You want UEFI, so it will install in UEFI mode.

---

### Post by gbgb on 2013-01-23
Hi oldfred,
Thanks a lot again for your insights.
I will follow your advice and post when I am stuck.
G.

---


---
title: "repairing grub"
date: 2018-06-01
forum: New to Ubuntu
---

### Post by nag92 on 2018-06-01
I am trying to repair Grub after attepting to repair windows. After booting from a live USB I tried to boot repair. I got the following error.

```GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.```

I get the following error

[URL="http://paste.ubuntu.com/p/YbkctR27dH/"]

http://paste.ubuntu.com/p/YbkctR27dH/[/URL] 

Can anyone help me repair these issues?

---

### Post by SuperFreak on 2018-06-01
Pastebin says your report does not exist

---

### Post by nag92 on 2018-06-01
updated the link

---

### Post by nag92 on 2018-06-01
I still cannot get things working. I am not sure how to fix this

---

### Post by Cavsfan on 2018-06-01
If you can get the partitions mounted, this is the grub install command. Although the location of the x86_64-efi file may be different. You just have to look for these folders:
```
cavsfan@cavsfan-Cosmic-Cuttlefish:~$ sudo su
[sudo] password for cavsfan: 
root@cavsfan-Cosmic-Cuttlefish:/home/cavsfan# cd /boot/efi
root@cavsfan-Cosmic-Cuttlefish:/boot/efi# ls
EFI  grub  grub.grub.cfg  initramfs-linux-fallback.img  initramfs-linux.img  intel-ucode.img  vmlinuz-linux
root@cavsfan-Cosmic-Cuttlefish:/boot/efi# cd EFI
root@cavsfan-Cosmic-Cuttlefish:/boot/efi/EFI# ls
[COLOR=#0000ff]Arch_grub  bionic  Boot  cosmic  Microsoft  ubuntu  xenial[/COLOR]
```

I have Windows 10, Arch Linux, 16.04, 18.04 and 18.10 installed, which is why I have so many folders. I made a copy of each ubuntu folder after each installation.
But, since you have only one Ubuntu installation it should just show Microsoft and ubuntu.
The directory where the ubuntu folder is what you're looking for and this is the command to use:
```
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi/EFI/ubuntu --bootloader-id=ubuntu

```

You may have to modify the location to suit your needs.

---

### Post by Cavsfan on 2018-06-01
I meant these 3 partitions. I have mine on sdc also:
```
root@cavsfan-Cosmic-Cuttlefish:/boot/efi/EFI# lsblk | grep sdc
sdc       8:32   0 447.1G  0 disk 
&#9500;&#9472;sdc1    8:33   0   550M  0 part [COLOR=#ff0000]/boot/efi[/COLOR]
&#9500;&#9472;sdc2    8:34   0    16M  0 part 
&#9500;&#9472;sdc3    8:35   0   150G  0 part 
&#9500;&#9472;sdc4    8:36   0   466M  0 part 
&#9500;&#9472;sdc5    8:37   0     4G  0 part [COLOR=#ff0000][SWAP][/COLOR]
&#9500;&#9472;sdc6    8:38   0   155G  0 part 
&#9500;&#9472;sdc7    8:39   0    20G  0 part 
&#9500;&#9472;sdc8    8:40   0    20G  0 part 
&#9500;&#9472;sdc9    8:41   0    15G  0 part[COLOR=#ff0000] /[/COLOR]
&#9492;&#9472;sdc10   8:42   0    40G  0 part 



```

---

### Post by Cavsfan on 2018-06-01
For you that would be these 3 like this according to your /etc/fstab:
  
```
&#9500;&#9472;[COLOR=#FF0000]sda1[/COLOR]    [COLOR=#ff0000]/boot/efi[/COLOR]
&#9500;&#9472;[COLOR=#ff0000]sdc3[/COLOR]    [COLOR=#ff0000]/[/COLOR]
&#9492;&#9472;[COLOR=#ff0000]sdc4[/COLOR]   [[COLOR=#ff0000]SWAP[/COLOR]]
```

---

### Post by oldfred on 2018-06-01
If it is asking for a bios_grub partition, that is trying to install the BIOS boot version of grub onto a gpt partitioned drive. You do not want that as you have UEFI and all drives are gpt partitioned.

What model Lenovo?

Have you tried with UEFI Secure Boot off?

This may be because you have and ESP on both the Windows drive sda & the Ubuntu drive sdc. Choose to install grub in UEFI mode to sdc so it installs to ESP on sdc.
>  GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option. 



You also have lots of kernels, best to houseclean.
       [URL="https://help.ubuntu.com/community/RemoveOldKernels"]https://help.ubuntu.com/community/RemoveOldKernels
[/URL]
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do, then run without -s
sudo apt-get -s autoremove 


[URL="https://help.ubuntu.com/community/RemoveOldKernels"]
[/URL]

---

### Post by nag92 on 2018-06-01
How do I mount the partitions? when I code 

```

sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi/EFI/ubuntu --bootloader-id=ubuntu

```

I get 

```

grub-install: error: /usr/lib/grub/x86_64-efi/modinfo.sh doesn't exist. Please specify --target or --directory.



```

---

### Post by nag92 on 2018-06-01
I have a thinkpad P50

---

### Post by Cavsfan on 2018-06-01
> **nag92 said:**
> How do I mount the partitions? when I code 

```

sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi/EFI/ubuntu --bootloader-id=ubuntu

```

I get 

```

grub-install: error: /usr/lib/grub/x86_64-efi/modinfo.sh doesn't exist. Please specify --target or --directory.



```

You will have to find your **x86_64-efi** file in your /boot folder.

Oldfred has better answers to how to do this stuff than I do. I'm new to EFI boot but, I knew you had to mount those three partitions and then install grub with a command similar to that one.

As oldfred stated, you have a lot of old kernels and you only need 2 as that's all that are usable. The rest just take up space and each takes up about 200mb for each kernel.

I use this command:
```
sudo apt-get --purge autoremove
```
the purge part gets rid of the config files too.
But, you've got to be able to boot into it first.

---

### Post by oldfred on 2018-06-01
I have in my notes some older threads on P50s. Not sure if all those issues are now resolved. Some seem unique to Lenovo.

Boot-Repair now does a copy of /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi. The bootx64.efi is a hard drive or fallback boot entry that many systems seem to need to use as vendors violate UEFI standard and "ubuntu" description is not valid as a default boot.

 Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061) 
      
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by nag92 on 2018-06-03
I was able to solve the problem with the advance options of te start up repair

---


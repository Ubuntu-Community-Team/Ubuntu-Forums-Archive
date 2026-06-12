---
title: "boot"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by jtbrooks101 on 2013-05-17
How do I clean out the boot. It is full and i can not install update. Is there a way to expand it? Right now it is 217MB

---

### Post by dino99 on 2013-05-17
to give you some usefull help, first tell us about your hardware/installation
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by jtbrooks101 on 2013-05-17
hp pavilion dv6 newest version. used a flash drive to install

---

### Post by ajgreeny on 2013-05-17
Do you have a separate /boot partition?

Let's see the output of command **m****ount**.

---

### Post by miegiel on 2013-05-17
You probably have old (backup) kernels in */boot/* that are safe to remove (it's recommended to keep at least 1 old kernel).

To view do:
```
ls -al /boot/
```
To remove old kernels do **[COLOR="#FF0000"]for example[/COLOR]**:
```
sudo rm /boot/*-3.2.0-40-generic
```
Where *3.2.0-40-generic* is the kernel version you want to remove.

Not necessary to make room, but you might want to cleanup the old kernel entries from the GRUB menu by doing:
```
sudo update-grub
```

---

### Post by Impavidus on 2013-05-17
Removing old kernels using the package manager is cleaner than using rm.```
sudo apt-get purge linux-image-3.2.0-40-generic
```
Substitute your old kernel versions. Keep one old kernel as backup. This will update grub automatically.

---

### Post by Shivakumara on 2013-05-17
As Miegiel explained, remove the unwanted  and oldest vmlinuz*, initrd.img*, System.map* and config*. after this update the grub with update-grub command.

It will make you some space to update the kernel

Thanks
Shivu

---

### Post by matt_symes on 2013-05-17
Hi

> **Shivakumara said:**
> As Miegiel explained, remove the unwanted  and oldest vmlinuz*, initrd.img*, System.map* and config*. after this update the grub with update-grub command.

It will make you some space to update the kernel

Thanks
Shivu

The problem is that will not cleanly remove the kernels as it will leave other files dotted around the filing system.

It will also leave the package manager in an inconsistent state. It will have the kernels flagged as installed when they are not.

Although what you and Miegel propose will work, I would advocate doing a proper job and remove them using the suggestion in post #6 or a variation of it using dpkg. 

@OP. Please post the output of

```
dpkg -l | grep -E linux-"headers-|image-"
```

You can copy and paste it into the terminal and copy and paste the results back here.

It will also show the kernel headers you have installed as they may need cleaning up as well.

Kind regards

---

### Post by jtbrooks101 on 2013-05-18
```
ii  linux-image-3.5.0-17-generic                                3.5.0-17.28                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-24-generic                                3.5.0-24.37                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-25-generic                                3.5.0-25.39                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-26-generic                                3.5.0-26.42                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-27-generic                                3.5.0-27.46                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
iF  linux-image-3.8.0-19-generic                                3.8.0-19.30                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-17-generic                          3.5.0-17.28                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-24-generic                          3.5.0-24.37                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-25-generic                          3.5.0-25.39                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-26-generic                          3.5.0-26.42                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-27-generic                          3.5.0-27.46                            amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
iU  linux-image-extra-3.8.0-19-generic                          3.8.0-19.30                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
iU  linux-image-generic                                         3.8.0.19.35                            amd64        Generic Linux kernel image
jtbrooks101@jtbrooks101-HP-Pavilion-dv6-Notebook-PC:~$ 
```

that is what  i got

---

### Post by ajgreeny on 2013-05-18
I would suggest you use synaptic, which you may need to install first, as it is quite simply the best package manager available and gives you a lot of flexibility that the software-centre does not.  Now search for and remove:-

> 
linux-image-3.5.0-17-generic                                 3.5.0-17.28                            amd64        Linux kernel image  for version 3.5.0 on 64 bit x86 SMP
linux-image-3.5.0-24-generic                                 3.5.0-24.37                            amd64        Linux kernel image  for version 3.5.0 on 64 bit x86 SMP
linux-image-3.5.0-25-generic                                 3.5.0-25.39                            amd64        Linux kernel image  for version 3.5.0 on 64 bit x86 SMP
linux-image-3.5.0-26-generic                                 3.5.0-26.42                            amd64        Linux kernel image  for version 3.5.0 on 64 bit x86 SMP
linux-image-extra-3.5.0-17-generic                           3.5.0-17.28                            amd64        Linux kernel image  for version 3.5.0 on 64 bit x86 SMP
linux-image-extra-3.5.0-24-generic                           3.5.0-24.37                            amd64        Linux kernel image  for version 3.5.0 on 64 bit x86 SMP
linux-image-extra-3.5.0-25-generic                           3.5.0-25.39                            amd64        Linux kernel image  for version 3.5.0 on 64 bit x86 SMP
linux-image-extra-3.5.0-26-generic                           3.5.0-26.42                            amd64        Linux kernel image  for version 3.5.0 on 64 bit x86 SMP

along with any same numbered header packages.  That will leave you with two kernels only and should clean out a great deal of space on your system.

---

### Post by Paqman on 2013-05-18
You also might want to decide if you need to have /boot on a separate partition at all. It's normally only necessary if you are using some unusual filesystem or disk configuration for the rest of your system that the bootloader cannot itself boot. If you've not got some weird setup then having /boot on your normal root partition (as is the default setup) would be simpler and more reliable.

---

### Post by matt_symes on 2013-05-18
Hi

If you want a one liner to remove the kernels, copy and paste this into your terminal. (Captial P below)

```
sudo dpkg -P linux-image-{,extra-}3.5.0-{17,24,25,26}-generic
```

I don't understand why no headers were display with that command I posted.

Can you post the output of

```
dpkg -l | grep linux-headers
```Kind regards

---

### Post by jtbrooks101 on 2013-05-18
```
jtbrooks101@jtbrooks101-HP-Pavilion-dv6-Notebook-PC:~$ sudo dpkg -P linux-image-{,extra-}3.5.0-{17,24,25,26}-generic
[sudo] password for jtbrooks101: 
(Reading database ... 162685 files and directories currently installed.)
Removing linux-image-extra-3.5.0-17-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found initrd image: /boot/initrd.img-3.5.0-24-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.5.0-17-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
Removing linux-image-extra-3.5.0-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.5.0-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
Removing linux-image-extra-3.5.0-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.5.0-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
Removing linux-image-extra-3.5.0-26-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.5.0-26-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
Removing linux-image-3.5.0-17-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.5.0-17-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
Removing linux-image-3.5.0-24-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.5.0-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
Removing linux-image-3.5.0-25-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.5.0-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
Removing linux-image-3.5.0-26-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.5.0-26-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
```

---

### Post by matt_symes on 2013-05-19
Hi

That looks fine to me. It looks like you have two kernels installed now and that is generally accepted as good practice.

You can double check by running this command again and looking to the numbers next to linux-image and linux-image-extra.

```
dpkg -l | grep -E linux-"headers-|image-"
```

You can also look in your boot partition again.

```
ls -l /boot
```

Also, to check disk space

```
df -h
```

Kind regards

---

### Post by ajgreeny on 2013-05-19
A quick and good way to see how many kernels you have installed and showing in the grub menu, even if you don't normally see that menu is to run ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
```

---


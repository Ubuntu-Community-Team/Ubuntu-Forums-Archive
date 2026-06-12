---
title: "Grub reports no Operating System"
date: 2010-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by phillw on 2010-05-15
So, you deleted **all** the kernels ? or possibly it's so messed up Grub can't find a kernel? If after re-installing Grub you still cannot boot, then it is possibly time to re-install the kernel.

Boot from LiveCD, open a terminal session (Accessories --> Terminal) and gain root privalidges 

```
sudo -i
```

Firstly, find where the Linux installation is..
```
fdisk -l 
```(That is a little L and not the number one)

You will see something like this :

```

/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

```

Look for the entry that ends **83 Linux** which is **/dev/sda1** in the above example.

For this Tutorial I am assuming that /dev/sda1 is where your '83' is. _Do not use /dev/sda1 **unless** that is what it shows, use whichever is yours._

Next, mount the partition
```

mount /dev/sda1 /mnt

```

Next, you need to prepare the system for the new kernel.
```

for fs in sys proc dev dev/pts; do mount --bind /$fs /mnt/$fs; done
chroot /mnt

```

> If you are to upgrade any services it's best to divert the init application to prevent it from poking anything in the live system.
So ....
```

dpkg-divert --local --rename --add /sbin/init
ln -s /bin/true /sbin/init

```

And now, you can install the linux kernel.
```

apt-get install linux-image

```

At the end of this you should see something like
```

Setting up linux-image-generic (2.6.31.19.32) ...
Setting up linux-image (2.6.31.19.32) ...

```
(The exact numbers will quite likely be different as linux kernels are updated)

Next, you need to tell grub to update grub.cfg to allow you to use the new kernel.
```

update-grub

```

The important lines to look for are..
```

Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic

```
(This time the numbers will be like what you saw above, make a note of the number part e.g. 2.6.31-19)

Remove the link and divert...
```

unlink /sbin/init
dpkg-divert --rename --remove /sbin/init
exit

```

All done !! Select Restart you will have the option to boot into the new kernel, it will be the one with the numbers that you noted above.

---


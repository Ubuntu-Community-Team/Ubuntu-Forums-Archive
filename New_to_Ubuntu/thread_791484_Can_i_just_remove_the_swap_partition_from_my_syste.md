---
title: "Can i just remove the swap partition from my system?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by pedrotuga on 2008-05-12
I installed ubuntu on my eeepc, I decided to use a swap partition, but now, because storage is so small i am thinking of removing it. Can I just remove it whith gparted or so?
Are there any consequences besides being impossible to use hibernate?

---

### Post by philinux on 2008-05-12
You can remove it, like you said hibernate needs it. Why not shrink it.

---

### Post by Joeb454 on 2008-05-12
Suspend also needs it.

If it works of course ;) I only have a 256Mb Swap :)

---

### Post by philinux on 2008-05-12
A better idea than removing it is to tweak it. You can always tweak it back to normal. Much safer than removing

```
6. Swappiness
The default value for vm.swappiness is 60 in Ubuntu Feisty whic is a good default value but if you want to tweak the performance a little bit more you can change this value to a lower value to reduce the load of the swap. If you run the follwing command:
sysctl -q vm.swappiness
You will se that the value is set to 60. And by running:
sudo sysctl vm.swappiness=10
You will change the value from 60 to 10 which will make your system write to swap a lot less and I would recommend this to everyone that has 512 mb of memory or more. If you find that you have very little use of swap set the value to 0. This will not disable the swap but it will make your system write to the swap as little as possible and keep as much as possible in memory. This makes a huge improvment when switching between applications since they are now likley to be in physical ram instead of on the swap partition.

To set your value permanent you need to change the sysctl.conf file:
sudo kate /etc/sysctl.conf
Add the line
vm.swappiness=10
To the end of the file. This way it will be set upon boot.

I’ve found that the value of 5 works very good for my use and I have 1 GB of memory. the partition as you'll have to edit fstab too.


```
[http://blog.kutakutik.or.id/linux/tune-the-speed-and-performance-of-kubuntuubuntu/](http://blog.kutakutik.or.id/linux/tune-the-speed-and-performance-of-kubuntuubuntu/)

---

### Post by pedrotuga on 2008-05-12
So I can just go on my partition manager and remove it, or do i need to adjust some settings somewhere?

As for twaking it, I want to give a try to a system without swap.

---

### Post by miesnerd on 2008-05-12
im not 100% on this, but I bet there's a way to boot into your system without swap, just to try it out. You'll probably have to append it to the boot options, but if you're just looking to try it for the heck of it, I'd go that route, instead of deleting the partition. Even if you do delete the partition, you can always go back with Gparted and make another one, so no big deal.\

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=147621](http://ubuntuforums.org/showthread.php?t=147621)

---


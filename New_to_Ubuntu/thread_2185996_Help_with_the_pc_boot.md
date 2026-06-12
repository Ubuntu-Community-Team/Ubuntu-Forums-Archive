---
title: "Help with the pc boot"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by Ceerda on 2013-11-05
Hello, this is my first post here. I'm sure that you guys can see this. :)
I have a notebook and it came with Windows 7, but i wanted to learn more about Ubuntu and the Linux distros. So I installed the wubi on my machine in a partitioned drive and deleted the windows partition with the GParted program.
Now, when the PC is booting, it shows the option to boot on Ubuntu or Windows and I want to exclude the Windows option, doing the pc boot with the Ubuntu only. 
I know I made a horrible mistake excluding the Windows partition, but I want your help.
Thanks.

---

### Post by 513247209 on 2013-11-05
U should not have installed the Ubuntu with wubi from the beginning !

---

### Post by coffeecat on 2013-11-05
First question. Which Windows drive (C:, D: or E: and so on) did you install wubi to and is the partition you deleted the Windows C: partition?

Wubi is really only meant for a short term tryout of Ubuntu while still retaining Windows, and the whole point of it is for the user to be able to dual-boot Windows and Ubuntu in an easy-to-setup manner. With wubi, Ubuntu is sitting in a virtual partition within the Windows NTFS filesystem, which is not efficient. If you don't want Windows at all, it is better to install Ubuntu to its own real partition formatted with a Linux filesystem where it will run far better than in a wubi setup.

I'm surprised that you're seeing the wubi Windows/Ubuntu menu at all. Rather than us advise how to remove Windows from the menu, it might be better if you start over with a proper installation of Ubuntu. Do you want help with that? Do you really mean to erase Windows from that machine altogether?

---


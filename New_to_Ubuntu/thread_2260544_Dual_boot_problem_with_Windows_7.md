---
title: "Dual boot problem with Windows 7"
date: 2015-01-12
forum: New to Ubuntu
---

### Post by dragisa on 2015-01-12
Hi,
I have tried to set up dual boot with windows 7 but ran into several problemas. I have installed Ubuntu 14.04 on a new partition and created a swap area, but Windows booted automatically. I tried to fix this problem with Boot-Repair,
but now I can choose to boot Ubuntu, but dont have an option to choose Windows boot. Here is my Boot-Repair file - [http://paste.ubuntu.com/9720924](http://paste.ubuntu.com/9720924). I am new to Ubuntu and any help will be appreciated.
Thanks.

---

### Post by oldfred on 2015-01-12
I do not see why os-prober is not seeing your Windows partitions. Since you have boot files in both sda1 and sda2 it should add both to the grub menu.

It does not show Windows is hibernated or needs chkdsk as either of those often cause issues.
You might double check and use your Windows repair disk to run chkdsk on both sda1 & sda2.

If you run this does it give any errors?
sudo update-grub

---

### Post by prestotron7 on 2015-01-12
There is an easy way to install Ubuntu and dual boot it.

There was a program called Wubi that allowed you to install Ubuntu alongside Windows. It has been taken down from the Ubuntu website, and I am not sure why, but it is still downloadable online from CNet and several other sources. Here is a link:

[http://download.cnet.com/Wubi/3000-2094_4-10701841.]("http://download.cnet.com/Wubi/3000-2094_4-10701841.html")

Cheers,
Preston Cammarata
- Computer and Software Engineer

---

### Post by yancek on 2015-01-12
> There was a program called Wubi that allowed you to install Ubuntu alongside Windows. 

Actually, not Alongside but installed inside windows as a program.  It was not meant to be a dual-boot but a means of testing Ubuntu.  The Ubuntu site states that is won't work on windows 8 and it has actually not been supported for several versions and I expect it was more work for the developers than it was worth so they dropped it.

---

### Post by dragisa on 2015-01-13
@ oldfred[**[COLOR=#C61919][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") when i run sudo update-grub 				  i get - /usr/sbin/grub-probe: error: failed to get canonical path of `/cow'. I will try Windows repair disc.
@[**[COLOR=#000000] prestotron7[/COLOR]**]("http://ubuntuforums.org/member.php?u=1964430")  and [**[COLOR=#000000]yancek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1928724")  i am interested only in dual boot system but thank you anyway

---

### Post by oldfred on 2015-01-13
/cow would be the live installer, you cannot run sudo update-grub on live installer, but only from inside your working install.

So are you booting into your install or just the live installer?

---

### Post by hakuna_matata on 2015-01-13
> **dragisa said:**
> 
but dont have an option to choose Windows boot.
It is not difficult to create your own Windows 7 menu entry:

[LIST]
[*]Create a new file e.g. **/etc/grub.d/45_windows**  with an editor: 
[/LIST]
```
gksudo gedit /etc/grub.d/45_windows

```

[LIST]
[*]Insert these lines: (note **78ee85ebee85a1cc** is UUID of your partition with **bootmgr**) 
[/LIST]
[PHP]#! /bin/sh -e 
echo "add Windows 7" >&2
cat << EOF
menuentry "Windows 7" {
    insmod part_msdos
    insmod ntfs
    search --no-floppy --fs-uuid --set=root 78ee85ebee85a1cc 
    parttool \${root} hidden-
    drivemap -s (hd0) \${root}
    chainloader +1
}
EOF
#
[/PHP]

[LIST]
[*]Save it, make it executeable:```
sudo chmod +x /etc/grub.d/45_windows
```
[*]Update your menu entries:```
sudo update-grub
```
[/LIST]

edit: Note: You should use the commands above from inside your working  install, too.

---

### Post by dragisa on 2015-01-13
I managed to fix problem with Windows repair disc - from Comand promt with **[COLOR=#660000]bootrec /FixMbr[/COLOR][COLOR=#000000].[/COLOR]**[COLOR=#000000] Then in Windows i installed [/COLOR][COLOR=#000000][/COLOR]**EasyBCD **and fixed this problem.
Thanks all you for the effort!!!

---

### Post by Stevenukas on 2015-01-14
> **dragisa said:**
> I managed to fix problem with Windows repair disc - from Comand promt with **[COLOR=#660000]bootrec /FixMbr[/COLOR][COLOR=#000000].[/COLOR]**[COLOR=#000000] Then in Windows i installed [/COLOR]**EasyBCD **and fixed this problem.
Thanks all you for the effort!!!

Mark this as solved please so people dont waste time reading thread :)

---


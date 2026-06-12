---
title: "[SOLVED] Ubuntu won't boot..."
date: 2008-07-09
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-09
Hi ubunters.
While booting busybox appears.
It might be my specs so ... here they are:
- Asus P5Q-E
- Intel Core2 Quad Q6600 
- Radeon HD4850 512MB
- 4GB ddr2-800
- 500GB sata2 16MB cache
Is there a way to solve this? Should i change os? Which one? Debian?
Thanks.

---

### Post by cristo-father on 2008-07-09
bump

---

### Post by Tatty on 2008-07-09
Hi christo-father,

Are there any more details you can add to this.  what do you mean by "busybox appears"?

Are you getting a specific error message etc...?

---

### Post by cristo-father on 2008-07-09
> **Tatty said:**
> Hi christo-father,

Are you getting a specific error message etc...?

"Busybox v1.1.3 (Debian...)...
Enter 'help' for a list of built-in commands.

(initramfs)"

---

### Post by cristo-father on 2008-07-10
bump

---

### Post by Troll_the_Great on 2008-07-10
When this "busy box" appears?When you boot-up?After you log in?In between?What Ubuntu do you use?

---

### Post by cristo-father on 2008-07-10
> **Troll_the_Great said:**
> When this "busy box" appears?When you boot-up?After you log in?In between?What Ubuntu do you use?
Right after the screen with the ubuntu logo and the bar(beneath).
I use ubuntu 8.04.1 amd64 version.

---

### Post by Tatty on 2008-07-10
[https://answers.launchpad.net/ubuntu/+question/21058](https://answers.launchpad.net/ubuntu/+question/21058)

Have a look at this thread in launchpad and see if it helps at all.

---

### Post by cristo-father on 2008-07-10
> **Tatty said:**
> [https://answers.launchpad.net/ubuntu/+question/21058](https://answers.launchpad.net/ubuntu/+question/21058)

Have a look at this thread in launchpad and see if it helps at all.

My situation is diferent i already have ubuntu installed.

---

### Post by Troll_the_Great on 2008-07-10
Did you try booting up in recovery mode?At boot-up you should have at least 3 options:
current kernel: 2.6.24-19 generic
recovery mode:  2.6.24-19 recovery mode
memory test: memtest86
Try recovery mode and see what happens, and then post the results.

---

### Post by cristo-father on 2008-07-10
> **Troll_the_Great said:**
> Did you try booting up in recovery mode?At boot-up you should have at least 3 options:
current kernel: 2.6.24-19 generic
recovery mode:  2.6.24-19 recovery mode
memory test: memtest86
Try recovery mode and see what happens, and then post the results.
I followed the 4th post and got a slightly different problem.
[http://ubuntuforums.org/showthread.php?t=851022&highlight=busybox](http://ubuntuforums.org/showthread.php?t=851022&highlight=busybox)
I got:

"ALERT! /dev/disk/by-uuid/... does not exist. Dropping to a shell!"
and then busybox appears once more.

I also tried recovery mode right after this and got the same thing.

---

### Post by cristo-father on 2008-07-10
bump

---

### Post by freak42 on 2008-07-10
Care to give a bit more information?

Did your ubuntu ever boot correctly? 
Is this after a fresh install or update?
Which version of Ubuntu?
Did you change something on your system before the error appeared?

---

### Post by cristo-father on 2008-07-10
> **freak42 said:**
> 
Did your ubuntu ever boot correctly? 
No

> **freak42 said:**
> Is this after a fresh install or update?

The first error is after fresh install, the new one is after the change i mentioned in a post in this thread.

> **freak42 said:**
> Which version of Ubuntu?

Ubuntu 8.04.1 amd64 desktop

> **freak42 said:**
> Did you change something on your system before the error appeared?

I didn't change anything before the first error,but i did before the second(see 1st post in the second page).

---

### Post by decoherence on 2008-07-10
Perhaps LVM is messed up?

At the busybox prompt, type 'vi /etc/fstab' and look for the lines that look something like 

```
# /dev/sda1
UUID=52108da2-5a4d-4bd9-9210-e52666dc1cb9 / ext3    relatime,errors=remount-ro 0 1

```

The actual line will be spaced out a lot more. Anyway, change it to look like 

```
/dev/sda1 / ext3 relatime,errors=remount-ro 0 1
```

Basically, we're just taking out the "UUID=52108da2-5a4d-4bd9-9210-e52666dc1cb9" and replacing it with "/dev/sda1" You numbers may be different.

vi is a difficult editor to use if you don't know how, but here are the very basics. You can navigate with the arrow keys, press 'x' to delete a character and 'i' to start typing. When you're done typing, press escape, then type ':wq' to save and quit.

ADD: if it's a fresh install, it shouldn't be this problem. but you never know.

---

### Post by cristo-father on 2008-07-10
> **decoherence said:**
> Perhaps LVM is messed up?

At the busybox prompt, type 'vi /etc/fstab' and look for the lines that look something like 

```
# /dev/sda1
UUID=52108da2-5a4d-4bd9-9210-e52666dc1cb9 / ext3    relatime,errors=remount-ro 0 1

```

The actual line will be spaced out a lot more. Anyway, change it to look like 

```
/dev/sda1 / ext3 relatime,errors=remount-ro 0 1
```

Basically, we're just taking out the "UUID=52108da2-5a4d-4bd9-9210-e52666dc1cb9" and replacing it with "/dev/sda1" You numbers may be different.

vi is a difficult editor to use if you don't know how, but here are the very basics. You can navigate with the arrow keys, press 'x' to delete a character and 'i' to start typing. When you're done typing, press escape, then type ':wq' to save and quit.

Can i use nano?

---

### Post by freak42 on 2008-07-10
ok, 
somehow ubuntu thinks your harddisk is a different one than it should be.

(now.. I'm no expert in these things, but since no one else currently is helping: we can try going on).

first, please find out what kind of disks your system sees, you can do this in the shell that you get dropped after the save boot fails.

```
ls -l /dev/disk/by-uuid/
```

it should output one or more lines in the form:
lrwxrwxrwx 1 root root 10 2008-07-10 10:19 324393b6-0276-4d5s-bab5-07de0cdb20d1 -> ../../sda1

The path above (../../sda1) (the letters can be differnt, like hda1, sda5, sdb1) refers to your partitions. One of these is your root partition, most likely sda1 or hda1 (if it exists)


in grub, while booting you can try replacing the part in the kernel line (like in the other thread):
```
root=324393b6-0276-4d5s-bab5-07de0cdb20d1
``` (the hex-string will be different)

with ```
root=/dev/sda1
``` <- but replace "sda1" with your root partition identifier, as you have found with ls -l /dev/disk/by-uuid/

It may help.
You can also post your output from the ls command here.

If the above works you can update your /boot/grub/menu.lst to make your change permanent, but let's first find out if it works at all.

---

### Post by freak42 on 2008-07-10
yes you can use nano for all your command line editing needs.

---

### Post by Lostincyberspace on 2008-07-10
If you can post your /boot/grub/menu/lst that can help allot with boot problems.

Also I had a similar problem but mine was even stranger it would happen only evry few times with no consistent pattern. I then got the the official ubuntu 32bit initrmfs update (I am using LinuxMint). so if you are able to get in download the 32bit initramfs and it should be fine.

---

### Post by cristo-father on 2008-07-10
> **decoherence said:**
> type 'vi /etc/fstab' 

It says "/bin/sh: vi: not found"

---

### Post by cristo-father on 2008-07-10
> **Lostincyberspace said:**
> If you can post your /boot/grub/menu/lst that can help allot with boot problems.

Also I had a similar problem but mine was even stranger it would happen only evry few times with no consistent pattern. I then got the the official ubuntu 32bit initrmfs update (I am using LinuxMint). so if you are able to get in download the 32bit initramfs and it should be fine.
what is 32bit initramfs?

---

### Post by cristo-father on 2008-07-10
bump

---

### Post by cristo-father on 2008-07-10
bump

---

### Post by Lostincyberspace on 2008-07-10
It is the same package just instead of 64bit it is 32bit. The 64bit is what you have so you might just try installing the 32bit version if you can and seeing if that fixes it.

---

### Post by cristo-father on 2008-07-10
Problem solved on this topic.
[http://ubuntuforums.org/showthread.php?t=855412](http://ubuntuforums.org/showthread.php?t=855412)

---

### Post by decoherence on 2008-07-11
> **cristo-father said:**
> It says "/bin/sh: vi: not found"

huh, i guess ubuntu doesn't have vi in their busybox... surely they have some editor? anyone?

anyway, glad you solved it.

---


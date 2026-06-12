---
title: "Alternative CD installation claims no free disk space"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by djbloc on 2008-09-02
Hi,

I've been trying to install Ubuntu 8.4.1 using the alternative CD in "expert" mode. I'm using two new formatted partitions on an 8GB USB drive. The first is 250MB and mounted ext3 as "/boot". The second partition is 2GB and mounted encrypted ext3 as "/".

During the "install base components" process the screen goes red inidicating the disk is full. Switching to another terminal and typing "df" shows only about 120MB out of 2100MB (6%) of the "/" partition is in use.

Is this a known problem? I could not find anything on Launchpad.

Any help would be appreciated.

Thanks

---

### Post by bumanie on 2008-09-02
I think / is too small. Ubuntu takes something like around 3gb to install to, as the base install and that's before installing anything extra. Most users have a 6-8gb / Also, unless booting multiple OSes, a boot partition is generally unnecessary. If you plan on multiple OSes, a grub partition may be better - [see here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"). There are also links to making a separate boot partition too.

---

### Post by ajgreeny on 2008-09-02
I suggest you need to make the / partition the 250GB one and the 2GB as swap, and personally I would not bother with a separate /boot partition.

What most people seem to be doing these days is making a root / partition of about 10GB, a swap partition of up to 1GB, and a separate /home partition of the rest of the disk.  2GB is not enough for ubuntu / partition as that is where the operating system files are placed and a simple install of an unamended ubuntu install with no home documents or photos, etc etc is about 2.6GB.

Have a look at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) for more information on partition planning.

---

### Post by Oldsoldier2003 on 2008-09-02
> **bumanie said:**
>  Also, unless booting multiple OSes, a boot partition is generally unnecessary. If you plan on multiple OSes, a grub partition may be better - [see here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"). There are also links to making a separate boot partition too.
Fedora and Ubuntu don't play well when you share a boot partition. Other combinations are problematic as well- I strongly advise against using a boot partition unless absolutely necessary.

---

### Post by mellowd on 2008-09-02
Are you guys sure about the install size? I just installed ubuntu server fresh on my new 750GB and it only took up 800MB

---

### Post by snowpine on 2008-09-02
> **mellowd said:**
> Are you guys sure about the install size? I just installed ubuntu server fresh on my new 750GB and it only took up 800MB

Ubuntu server has no GUI, therefore it is smaller! :)

---

### Post by mellowd on 2008-09-02
> **snowpine said:**
> Ubuntu server has no GUI, therefore it is smaller! :)

but 2GB smaller?

---

### Post by ajgreeny on 2008-09-02
> but 2GB smaller? 	
I can assure you that my ubuntu install with a separate /home was about 2.6GB immediately after installation, no extra application s and no documents or added extras were included, so the GUI must take up the extra space, as far as I can make out.

---

### Post by mellowd on 2008-09-02
> **ajgreeny said:**
> I can assure you that my ubuntu install with a separate /home was about 2.6GB immediately after installation, no extra application s and no documents or added extras were included, so the GUI must take up the extra space, as far as I can make out.

Thinking about it, you're probably right. It's not just the gui of course, but all the graphics for all the games/gui apps. 

It makes quite a big difference :)

---

### Post by snowpine on 2008-09-02
> **mellowd said:**
> but 2GB smaller?

The OP's experience suggests it is so. ;)

---

### Post by philinux on 2008-09-02
After a few weeks of use, installing extras etc. My / is now using 3.7GiB. I gave it 10GiB when i installed.

---

### Post by djbloc on 2008-09-04
I've realised that I forgot to mention the drive is a USB stick (I've edited the original post)

I'm still clueless why the installer stop after only using 6% of the "/" partition. Is there any reason for this? Would altering the “/” partition to 3GB be sufficient to install the basic install with GUI?

To answer the question why I created a "/boot" partition. The installer asked me to create one since the "/" root partition is encrypted.

---

### Post by bumanie on 2008-09-04
check out [www.pendrivelinux.com](www.pendrivelinux.com)

---

### Post by djbloc on 2008-09-04
Thanks, I will have a look at pendrivelinux.com. In the mean time I tried again this evening using the "Alternative CD 8.40.1".

Partitions created on 8GB USB Drive:

4GB fat32
3.7GB encrypted (aes) drive using ext3 mounted as "/"
300MB using ext2 mounted as "/boot"
No swap partition

Everything is fine until during the "Install base system". Half way through the screen goes red claiming no space left on device. Switching to console and typing "df" results in:

```
filesystem    used    available    use%   mounted
tmpfs    40    257748   0%  /dev
/dev/scd0   715280     0    100%   /cdrom
/dev/mapper/sdb2-crypt    171724   3260460  5%  /target
/dev/sdb3    13    270784   0%   /target/boot
```

Switch to the log terminal shows the line:

```
debootstrap:  tar: ./usr/share/zoneinfo/Africa/Kinshasa: No space left on device
```

To my untrained eye I do not understand why I get the "no space left" message when only 5% space is used on root. Any ideas?

---

### Post by kansasnoob on 2008-09-04
> **Oldsoldier2003 said:**
> Fedora and Ubuntu don't play well when you share a boot partition. Other combinations are problematic as well- I strongly advise against using a boot partition unless absolutely necessary.

+1. I almost lost my mind!

I did finally get Fedora and Ubuntu to play well togethrer only after recreating them in separate extended partitions, and then only if I installed Ubuntu last!

I'd never even try it again!

---


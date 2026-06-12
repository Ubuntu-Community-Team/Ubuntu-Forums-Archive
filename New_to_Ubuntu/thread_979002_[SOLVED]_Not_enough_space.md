---
title: "[SOLVED] Not enough space"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by perito on 2008-11-11
Its so weird, I think i did a mistake while partitioning .. or some place else, everything is ok except I get that I don't gave enough space while doing certain things like

There is not enough room on the disk to save /tmp/zF3fSopj.part.

Remove unnecessary files from the disk and try again, or try saving in a different location.

I have lots of space in my home directory. what is with /tmp/ directory ??
How can I increase the space there?

---

### Post by CLomax on 2008-11-11
Please enter the following into the terminal and paste the result here:

```
sudo fdisk -l
```

The /tmp/ you are referring to might be on the root partition assuming you separated the /home from /root.

---

### Post by zvacet on 2008-11-11
```
sudo apt-get autoclean
sudo apt-get autoremove
```

This should give you some free space.

---

### Post by bumanie on 2008-11-11
Output the results of these > df -h / > df- h /home

---

### Post by handydan918 on 2008-11-11
> **CLomax said:**
> Please enter the following into the terminal and paste the result here:

```
sudo fdisk -l
```

The /tmp/ you are referring to might be on the root partition assuming you separated the /home from /root.
Yes, /tmp is on the root partition. Unless you put it elsewhere, so this doesn't happen...

---

### Post by perito on 2008-11-12
> ubuntu@ubuntu-laptop:~$ sudo fdisk -l
[sudo] password for ubuntu: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfff0b24f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       10238    80696320    7  HPFS/NTFS
/dev/sda3           10239       10481     1951897+  82  Linux swap / Solaris
/dev/sda4           10482       19457    72099720    5  Extended
/dev/sda5           10482       10846     2931831   83  Linux
/dev/sda6           10847       19457    69167826   83  Linux
ubuntu@ubuntu-laptop:~$ 

> ubuntu@ubuntu-laptop:~$ df -h / 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.8G  2.7G     0 100% /
ubuntu@ubuntu-laptop:~$ 

> ubuntu@ubuntu-laptop:~$ df -h /home
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              65G   12G   51G  19% /home
ubuntu@ubuntu-laptop:~$ 


here are all the results ... now what ?

---

### Post by blackened on 2008-11-12
Looks like you've undersized the root partition. Do you have a live cd handy? If so, run gparted from it and grow the / partition to around 5-10GB. You may have to first shrink the home partition by the same amount to create empty space for the / partition to grow into.

---

### Post by perito on 2008-11-12
how do I do that?
I do have the ubuntu live cd. So I put it in and then what ?
how do i run gparted and how do I modify the partisioning ?
Will anything be removed or formated ?

---

### Post by CLomax on 2008-11-12
> **blackened said:**
> Looks like you've undersized the root partition. Do you have a live cd handy? If so, run gparted from it and grow the / partition to around 5-10GB. You may have to first shrink the home partition by the same amount to create empty space for the / partition to grow into.

Had a feeling.

> how do I do that?
I do have the ubuntu live cd. So I put it in and then what ?
how do i run gparted and how do I modify the partisioning ?
Will anything be removed or formated ?

[B]>System -> Administration -> Partition Editor;
>Right click on the partition you want to change and 'Resize/move';
>You should be able to drag a slider, give root some more room;
>Apply the changes and do not cancel or disturb it in any way.[/B]

---

### Post by Paqman on 2008-11-12
Wow, that is one seriously tiny root partition.

---

### Post by boof1988 on 2008-11-12
Keep in mind that it may take a long time to resize the partitions.  Possibly hours.

Sometimes (Not sure if it'll help you) it's good to do one step at a time.  [LIST=1]
[*]Choose shrink partition #1
[*]apply the changes
[*]Choose increase size of partition #2
[*]apply the changes
[/LIST]

I believe that this is good advice.  Someone please tell me if I'm incorrect.

---

### Post by CLomax on 2008-11-12
> **boof1988 said:**
> Keep in mind that it may take a long time to resize the partitions.  Possibly hours.

Sometimes (Not sure if it'll help you) it's good to do one step at a time.  [LIST=1]
[*]Choose shrink partition #1
[*]apply the changes
[*]Choose increase size of partition #2
[*]apply the changes
[/LIST]

I believe that this is good advice.  Someone please tell me if I'm incorrect.

That's actually better practice.

---


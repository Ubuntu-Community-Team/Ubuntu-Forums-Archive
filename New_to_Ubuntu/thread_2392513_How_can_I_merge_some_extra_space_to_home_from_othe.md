---
title: "How can I merge some extra space to /home from other volume?"
date: 2018-05-22
forum: New to Ubuntu
---

### Post by mnislam01 on 2018-05-22
I have installed **Ubuntu 18.04** very recently and am very new to Linux. I have a partition at **dev/sda3 **which is NTFS type and has gone read only. Learned that windows fastboot feature did that. Now, what I want to is: I want to format that partition (Cause, I don't need any file are saved there) and merge all the spaces to [B]/home.

[/B]Alas, I don't know how to that and I want help for the following tasks:

1. I want to** format/delete** it so that I can have free space.
2. I want to **merge** those free space to [B]/home

[/B]Thank you very much in advance.

---

### Post by Impavidus on 2018-05-22
You can't change partitions mounted by the running system, so you have to do this from a live disk. You can probably use the same one you used to install Ubuntu. Boot using the live disk and open a program called gparted. That's an easy tool for partitioning drives. You can then delete the ntfs partition. If the ntfs partition and the /home partition were adjacent, you can then expand the /home partition into the empty space. If not adjacent, it can get a little harder as you may have to shuffle things around.

In any case, make sure you have backups of your important files on the /home partition. The files should be safe, but if a power failure happens during partitioning you may loose everything.

---

### Post by SeijiSensei on 2018-05-22
Here's another solution that doesn't require repartitioning:

First, convert the filesystem to ext4:

```
sudo mkfs -t ext4 /dev/sda3
```

Next, create a "mount point," an empty directory, in your home directory where the filesystem will be mounted.  Let's call it "data".

```
cd ~
mkdir data

```

Now add this line to /etc/fstab with an editor as root with sudo ("sudo nano /etc/fstab") to mount that filesystem at boot:

```
/dev/sda3     /home/yourusername/data     ext4     defaults,uid=1000,gid=1000   0 0
```

Replace "yourusername" with your own username.  If you're the only user on the machine, you'll have ID 1000.  If there are others, you can see the IDs with

```

ls -n /home

```

Now mount the filesystem with 

```
sudo mount -t ext4 -a
```

It will be automatically mounted at boot in the future. You'll now have a "data" folder in your home directory.  Writing files there will place them in the new filesystem on /dev/sda3.

---


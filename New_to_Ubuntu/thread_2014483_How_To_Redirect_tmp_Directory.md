---
title: "How To Redirect /tmp Directory?"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by johny why on 2012-07-02
hi, sorry if this question has already been answered, could not find it.*

i'm attempting to redirect the /tmp directory to a partition with more free space, using these steps:*
```
mv /tmp /mnt/new/location/tmp
ln -s /mnt/new/location/tmp /tmp
```

i tried this after exiting to a command prompt, but getting "file in use".*

when tmp is not in-use, i get:*
"inter-device move failed... unable to remove target... Is a directory"*

i'm thinking to put the commands into a bash script that executes during boot, after /tmp is created, but before anything is accessing it. However, not quite sure (translation: no idea) where to put the boot script. noob thoughts.*

/root/Startup/README.txt says:*
to execute something at bootup and prior to X desktop loading, edit /etc/rc.d/rc.local*

so, i put the commands into rc.local. I believe it did not work. Also tried making a separate bash file in*/etc/rc.d

during the boot, before xWindows starts, i saw the message "cannot move" or "cannot remove".*

also posted to the saluki forum and linuxforums.org.*

suggestions welcomed.*
_________________
asus eeepc 1001PXB*
2x Intel(R) Atom(TM) CPU N450 @ 1.66GHz*
2064MB RAM, 1024x600 Display*
Detailed HardInfo: [https://sites.google.com/site/johnywhy/my-asus-pc](https://sites.google.com/site/johnywhy/my-asus-pc)

---

### Post by Paqman on 2012-07-02
To switch /tmp to a different partition you need to add a line to the file /etc/fstab. To edit fstab hit Alt-F2 and:

```
gksudo gedit /etc/fstab
```

For exmaple:

```
/dev/partition_number /tmp ext4 defaults 0 0
```

You'll see most other partitions in fstab listed by their UUID instead of /dev/whatever (a UUID is a long strin of numbers). Either works fine if you're not messing with the actual disk, if you want to use the UUID you can obtain it by:
```
sudo blkid
```

After you've edited fstab check it with:

```
sudo mount -a
```

And if it returns no errors you can safely reboot and your /tmp will now be on the partition you want.

---

### Post by johny why on 2012-07-02
would this be correct?

```
/dev/sda1 /tmp ntfs defaults 0 0
```

will this create a tmp directory in sda1?

after editing fstab, mount -a returns errors::
> # mount -a
mount: /dev/sda1 already mounted or /tmp busy
mount: according to mtab, tmpfs is already mounted on /tmp
Does that mean it will not work?

[This post]("http://www.linuxforums.org/forum/other-linux-distributions/190050-how-redirect-tmp-directory.html#post896380") says i must ensure that sda1 is mounted early enough during boot, because tmp is needed during boot. How can i ensure that?

many thanks!

---

### Post by Paqman on 2012-07-02
I'm not sure if you can mount /tmp on a Windows filesystem. Reformat to ext4 and you'll be fine.

Mounting through fstab will mount it early enough, after all / is mounted through fstab, and that's where your kernel images are!

---


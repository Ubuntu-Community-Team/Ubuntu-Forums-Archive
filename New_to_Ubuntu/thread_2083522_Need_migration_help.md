---
title: "Need migration help"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by hairylugs82 on 2012-11-12
I just installed 12.10 onto windows, created partitions for the move (sda5 and sda6), but I keep getting
```
bash: wubi-move.sh: No such file or directory
```

---

### Post by Frogs Hair on 2012-11-12
Hello and Welcome 

Here are some related links.  

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

[http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition](http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition)

---

### Post by bcbc on 2012-11-12
> **hairylugs82 said:**
> I just installed 12.10 onto windows, created partitions for the move (sda5 and sda6), but I keep getting
```
bash: wubi-move.sh: No such file or directory
```

This means that you don't have the wubi-move.sh script in the current directory. So most likely you downloaded the compressed file in your **Downloads** folder and extracted to the **wubi-move-1.6** folder, so you would get there as follows:
```
cd ~/Downloads/wubi-move-1.6
```

Then you can try again.

---

### Post by newb85 on 2012-11-13
Also, once you're in the directory with the shell script, you'll probably have to execute it using
```
sudo ./wubi-move.sh
```
not just
```
sudo wubi-move.sh
```

---

### Post by bcbc on 2012-11-13
Actually, it's
```
sudo bash wubi-move.sh /dev/sda5 /dev/sda6
```

Otherwise you have to make the script executable first:
```
chmod +x wubi-move.sh
sudo ./wubi-move.sh /dev/sda5 /dev/sda6
```

Just follow the guide: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by supermango on 2012-11-30
> **bcbc said:**
> https://help.ubuntu.com/community/MigrateWubi[/url]

I just did the migration and restarted... everything looks the same. Shouldn't some of the icons go away? Am I in the right partition?

**How does one check to see if the migration worked properly?**

---

### Post by bcbc on 2012-11-30
> **supermango said:**
> I just did the migration and restarted... everything looks the same. Shouldn't some of the icons go away? Am I in the right partition?

**How does one check to see if the migration worked properly?**

It does look the same. There's no noticeable difference between a Wubi install or a normal dual boot, except some performance improvement (not significant but it depends on what you're doing).

So... if you migrated with default settings (installed the grub bootloader), then you'll see a different menu at startup - the Grub menu - instead of the Windows Boot Manager. That's the first clue.

Once booted, if you go to a terminal and run:
```
df -h
```
It should show "/" mounted on /dev/sda# (instead of /dev/loop0). There will be no /host mounted. You could also enter this:
```
mount | grep ' / '
```

If you look in /etc/fstab it will show /dev/sda# instead of /host/ubuntu/disks/root.disk.
```
cat /etc/fstab
```
e.g. something like this:
```
...
# root was on /dev/sda5 when wubi migrated
UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sda6 when wubi migrated
UUID=8810c3fc-2171-426a-99ee-c3b56dcccc96    none    swap    sw    0    0

```Your Wubi install will still be there - the same as it was when you migrated. When you boot Windows, it will still offer to boot Ubuntu, and that defaults to your Wubi install.



PS a correction to the post I made 2 weeks ago. The folder name was ~/Downloads/wubi-move-2.3, not 1.6 as I mentioned before. (But I can't go back and edit it now). Sorry for any confusion.

---

### Post by supermango on 2012-11-30
Okay. Looks like I am running it off the partition.

The performance threw me off. I was expecting it to go much faster, but it's about the same as the wubi.

My reasons to stay with linux as opposed to windows:
[LIST]
[*]boot time
[*]performance
[*]ease of use
[*]wifi syncs within a few seconds (vs. ~ 30s - 60s on windows)
[/LIST]

Thank you for the reply.

---

### Post by bcbc on 2012-11-30
> **supermango said:**
> 
The performance threw me off. I was expecting it to go much faster, but it's about the same as the wubi.


In general, there is a lot of misinformation out there about Wubi. People don't like it, so exaggerate the negatives. There is certainly a performance difference, but it's not really noticeable to me unless I'm doing some major file-intensive work like archiving, compiling etc.

[Phoronix did a study]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1") of the performance differences and found, in some cases, Wubi performed better than a normal install. Either way, you are better off with a normal install due to the one major issue with Wubi - and that is the reliability and integrity of the root.disk.

---


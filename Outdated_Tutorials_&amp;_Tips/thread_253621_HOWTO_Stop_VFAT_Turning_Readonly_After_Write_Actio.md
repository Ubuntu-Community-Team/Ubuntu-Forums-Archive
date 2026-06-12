---
title: "HOWTO: Stop VFAT Turning Readonly After Write Actions"
date: 2006-09-08
forum: Outdated Tutorials &amp; Tips
---

### Post by lukew on 2006-09-08
Hi,

This is my first howto, so please dont be to critical.

(I am using fat 32 on this disc as I have to otherwise I would format it with ext3 like my other ext hds ;) )

I was having problems performing cp and rsync ton a ext usb hd which was formatted with fat32. I initally had copied 80gb onto it with no problems, then suddenly I was getting readonly error messages. 

After remounting I could create a document or file on the parition but performing rynsc or cp commands onto the parition would result in the parition becoming readonly. I would then not beable to create a file or directory, which literally seconds before I previously could do.

It turns out my HD has errors on it and needed to be fixed! Here is howto.


Plug in the disc; you will need it unmounted.

To identify what to unmount

	~$ umount 

Unmount you usb connected disc. In my case:

	~$ umount /dev/sdc1

Identify the physical location of the device.

	~$ fdisk =l.

Perform a fsck.vfat check on your disc. In my case

	~$  /sbin/fsck.vfat -a /dev/sdc1

If you get error messages like the one below it is working ok and the chances are you will beable to perform write operations once more.


****  Contains a free cluster (2380656). Assuming EOF.
***    File size is 3053800 bytes, cluster chain length is 0 bytes.
Truncating file to 0 bytes.
Reclaimed 12063 unused clusters (395280384 bytes) in 56 chains.
Free cluster summary wrong (5755867 vs. really 5755845)
  Auto-correcting.
Performing changes.
/dev/sdc1: 19417 files, 1873416/7629261 clusters


I hope this helps some people, I was scratching my head for a few hours wondering which this error was happening.

Luke

---


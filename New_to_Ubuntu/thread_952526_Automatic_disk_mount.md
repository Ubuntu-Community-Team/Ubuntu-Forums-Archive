---
title: "Automatic disk mount"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by belier on 2008-10-19
Hi.

I've formatted a disk with kubuntu. It works fine, but the problem is that I need to mount it each time I start OS. Is there anyway to make it mounts automatically?

Thans in advance

---

### Post by bpowell2005 on 2008-10-19
> **belier said:**
> Hi.

I've formatted a disk with kubuntu. It works fine, but the problem is that I need to mount it each time I start OS. Is there anyway to make it mounts automatically?

Thans in advance

Yes, you can make a drive auto-mount by adding the correct mount command to your /etc/fstab file. If you could post the output of the command "mount" here, (after you've manually mounted the drive) it would be easier to determine the correct command to add to your /etc/fstab.

---

### Post by bsharp on 2008-10-19
You could also take a look at this guide:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting%20partitions%20manually](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting%20partitions%20manually)

---

### Post by Jim_in_Germany on 2008-10-19
If it's formatted with NTFS, you could always try the NTFS configuration tool "ntfs-config", which can be found via synaptic.
Worked for me.

---

### Post by belier on 2008-10-19
Thx for the answer.

File system is ext3. I don't know hom to mount it using konsole.

I mount it through Dolphin->Storage Media.

On Properties dialog of the disk once mounted the disk info is:

URL base: file:///media/disk
Device node: /dev/sde1

I've tried to add a line at the /etc/fstab but it didn't work.

---

### Post by drs305 on 2008-10-19
> **belier said:**
> T

I've tried to add a line at the /etc/fstab but it didn't work.

This line, added to fstab, should work:
```
/dev/sde1 /media/**disk** ext3 defaults 0 2
```

A couple of notes:
It may be better to use a different mount point than "disk" since "disk" is a mountpoint sometimes used by the system to mount removable drives. Ubuntu should compensate, but I always try to avoid potential problems when I can.

If you change the mountpoint to something else, make sure you create the mountpoint as well using the commands below. Substitute your desired name for **mountpoint**:
```

sudo mkdir /media/**mountpoint**
sudo chown -R *yourusername*: /media/**mountpoint**
chmod -R 750 /media/**mountpoint**

```

Once you have saved fstab with the new entry, run the following command. If it works, you won't see any input after hitting enter and you should be able to view your newly-mounted drive with your file browser. If it fails, you will get an error message which will tell us what the problem is.
```

sudo mount /dev/sde1

```


For more information about fstab:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by belier on 2008-10-19
> **drs305 said:**
> THE SOLUTION
=D>
Thx a lot for the help. I've changed /media/disk for something more explicit. Did everything and it's working ok.

Now I only need to know how to add applications to autostart folder and I'll be more than happy with [k]ubuntu.

[http://ubuntuforums.org/showthread.php?p=5993791#post5993791](http://ubuntuforums.org/showthread.php?p=5993791#post5993791)

---

### Post by drs305 on 2008-10-19
> **belier said:**
> Now I only need to know how to add applications to autostart folder and I'll be more than happy with [k]ubuntu.


If it's the same as ubuntu, System, Preferences, Sessions. Click on +Add in the StartUp Programs tab.

---

### Post by belier on 2008-10-19
System->Preferences? Through main menu? I don't have it...

---


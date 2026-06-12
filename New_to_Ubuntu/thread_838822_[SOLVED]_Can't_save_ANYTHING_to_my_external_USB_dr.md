---
title: "[SOLVED] Can't save ANYTHING to my external USB drive"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Nxion on 2008-06-23
OK, I have a 160gb external hard drive and formated it with ext3. After I did that now I can not do anything with it. I checked the owner and the owner is root. ALSO I checked and when I plug it in it mounts as "/media/disk" I think that is the issue. Do I need to add it to FSTAB? if so, how. 

Thanks

---

### Post by neurostu on 2008-06-23
Have you tried:
```

sudo chown -R <YourUsername> /media/disk

```
you will become owner of the disk and should be able to write to it.

---

### Post by iaculallad on 2008-06-23
What happens if you try to change its permission to:

```
sudo chmod 777 /media/disk
```

---

### Post by Nxion on 2008-06-23
> **neurostu said:**
> Have you tried:
```

sudo chown -R <YourUsername> /media/disk

```you will become owner of the disk and should be able to write to it.


Tryed that, no change, owner is still root.

---

### Post by Nxion on 2008-06-23
> **iaculallad said:**
> What happens if you try to change its permission to:

```
sudo chmod 777 /media/disk
```


Tried that as well, No change.

---

### Post by neurostu on 2008-06-23
> **Nxion said:**
> Tryed that, no change, owner is still root.

Hmm.. that is really weird.

What you can try doing is...
unmount the drive with:
```

sudo umount /media/disk

```
create a folder in your home dir
```

mkdir usbDrive

```
then mount the usb drive to that directory (you might or might not have to be root if the directory is in your home dir)
```

mount -t ext3 /dev/<whateveryourdriveis> /home/<yourName>/usbDrive

```

Give that a try, if you have to use sudo then try the chown after that...

---

### Post by iaculallad on 2008-06-23
Try to post your /etc/fstab file.

---

### Post by Nxion on 2008-06-25
> **neurostu said:**
> Hmm.. that is really weird.

What you can try doing is...
unmount the drive with:
```

sudo umount /media/disk

```create a folder in your home dir
```

mkdir usbDrive

```then mount the usb drive to that directory (you might or might not have to be root if the directory is in your home dir)
```

mount -t ext3 /dev/<whateveryourdriveis> /home/<yourName>/usbDrive

```Give that a try, if you have to use sudo then try the chown after that...


ok I will give that a try.

---

### Post by Nxion on 2008-06-25
> **iaculallad said:**
> Try to post your /etc/fstab file.


I am not at my machine at the moment, its at home and I am at work. Once I get home ill try it. Thanks all for the assistance on this. It is a strange issue.

---

### Post by chrisccoulson on 2008-06-25
When you tried to chown and chmod it, did it spit out any error messages? If so, please post them here.

---

### Post by Nxion on 2008-06-25
> **chrisccoulson said:**
> When you tried to chown and chmod it, did it spit out any error messages? If so, please post them here.

Nope, no errors. After I ran either chown or chmod it just went back to the command prompt.

---

### Post by chrisccoulson on 2008-06-25
You need to post a bit more information to enable people to help you I think. When you say that you can't do anything with the drive, could you elaborate? IE, what exactly are you doing? And what error message do you see?

Could you also post the output from the following:
```
ls -l /media
mount -l
cat /etc/fstab
```

---

### Post by cariboo on 2008-06-25
I noticed when you where trying to change permissions of /media/disk you didn't use the -R for recursive. in a terminal try:

```
sudo chmod -R 777 /media/disk
```

Jim

---

### Post by Nxion on 2008-06-26
> **cariboo907 said:**
> I noticed when you where trying to change permissions of /media/disk you didn't use the -R for recursive. in a terminal try:

```
sudo chmod -R 777 /media/disk
```Jim

Tried that, same thing, no change :(

---

### Post by Nxion on 2008-06-26
> **chrisccoulson said:**
> You need to post a bit more information to enable people to help you I think. When you say that you can't do anything with the drive, could you elaborate? IE, what exactly are you doing? And what error message do you see?



I can't save anything to the drive itself at all.

---

### Post by chrisccoulson on 2008-06-26
That doesn't help a lot. There must be an error message. What does it say? Can you describe the steps you're taking? We could do with some more information in order to help you. In addition to the information I requested in my post above, could you also post the output of:
```
touch /media/disk/testfile1
sudo touch /media/disk/testfile2
```
If you can't write to the drive, then one or both of the above will fail with an error message. If only the first one fails, it is a permissions issue. If both fail, it could be because the volume is read-only.

Could you also try disconnecting the drive, opening a terminal, and running the following:
```
tail -f /var/log/syslog
```
With this running, re-connect the drive and monitor what gets written in to the syslog, then post the output here. 

Without providing the information we're asking for (including output from certain commands), we're going to get nowhere.

---

### Post by neurostu on 2008-06-27
Does the drive work in windows?

When you go root:
```

sudo -i

```

can you save things to the disk?

---

### Post by Nxion on 2008-06-28
> **neurostu said:**
> Hmm.. that is really weird.

```

mount -t ext3 /dev/<whateveryourdriveis> /home/<yourName>/usbDrive

```Give that a try, if you have to use sudo then try the chown after that...


Thanks, It worked perfect! I chowned it and I can write to it now!

---


---
title: "USB Problem"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Zoonosis on 2008-05-31
Anytime I put in a portable hard drive, it says "Cannot Mout". What's that mean?

Brandon Bovy
Zoonosis

---

### Post by wolfen69 on 2008-05-31
is it NTFS? if so, and it wasnt shutdown or unmounted properly, it will not mount unless you force mount it. i forgot the commands though.

---

### Post by Zoonosis on 2008-06-01
I was on a different site and it gave me the code to force it, but IDK how to log on as root.

---

### Post by superprash2003 on 2008-06-01
its always better to place that usb drive on a windows machine and do that "Safely Remove Hardware" thingy and bring it back to ubuntu

---

### Post by sayakb on 2008-06-01
Windows locks the NTFS drives when in use. Not removing it safely will need the force mount to be implemented:
```
sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

Where /dev/sdb1 should be your HDD. Plug you HDD in and issue:
```
sudo fdisk -l
```
To check the device link of your hard drive.

---

### Post by Dedoimedo on 2008-06-01
Hello,

Maybe you can try this method:

sudo fdisk -l

This will list all your devices, using linux notation. I hope you are familiar with it: hda, sdb etc. Please identify your hard drive.

Let's assume its /dev/sdc.

Create a mount point for it, for instance in the /mnt/ directory:

sudo mkdir /mnt/external

Now, what filesystem do you use on the disk? NTFS? Assuming this is the case, try mounting:

sudo mount -t ntfs /dev/sdc /mnt/external

Now, try accessing /mnt/external and see if you can see the contents of the hard drive.

Dedoimedo

---

### Post by rraj.be on 2008-06-01
Just try using NTFS CONFIGURATION tool

you can specify mount point, enable mounting , read write acces etc using that.

to launch NTFS configuration tool just open

```
Applications --> System tools --> NTFS Configuration tools
```

Hope this will help you.

---


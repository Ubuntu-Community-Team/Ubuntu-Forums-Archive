---
title: "[SOLVED] Permission / recovery problems"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Woah Cats on 2008-07-08
Hello everyone,

Fool that I am, I managed to delete or corrupt some files in the OS and now I cannot boot Ubuntu. I intend to wipe the HDD and install Ubuntu again but I've got some photos on there which I haven't backed up and need to retrieve them before I do. I've ran Ubuntu from the CD but cannot access the photos as I don't have permission to read the files.

Is there a way to log on under my username or to bypass the permission in order to access my photos?

I hope this makes sense!

---

### Post by Bigtime_Scrub on 2008-07-08
When you boot into the live CD and if it says you don't have the right permissions, trying opening a terminal...

```
sudo gksu nautilus
```

This should pop open a window that is as root. You should then be able to move the files where ever you like ie. burn to CD, copy to USB flash, etc.

---

### Post by unutbu on 2008-07-08
How to mount your linux partition from a LiveCD:

Boot from the LiveCD, open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and type
```

sudo fdisk -l

``` (Note the last bit is a lower case "-L", not minus one).

You should see output that looks something like
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         660     5245222+   b  W95 FAT32
**/dev/sda3**   *         661       38536   304238970   83  **Linux**
/dev/sda4           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris
```
Note the device name (e.g. /dev/sda3) which corresponds to your linux partition. 

Armed with the name of your linux partition, now type (changing /dev/sda3 to the name of your linux partition)

```
sudo mkdir /Ubuntu
sudo mount /dev/sda3 /Ubuntu

```
Your Linux filesystem will now be mounted at /Ubuntu. 
Usually when you run Ubuntu, your filesystem is mounted at /. 
The above commands mount your filesystem at /Ubuntu because the LiveCD's filesystem is already mounted at /. So if your home directory is usually at /home/USERNAME, then after typing the above commands your home directory will be at /Ubuntu/home/USERNAME.

---


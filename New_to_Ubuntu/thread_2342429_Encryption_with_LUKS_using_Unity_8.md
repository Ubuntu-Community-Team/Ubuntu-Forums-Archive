---
title: "Encryption with LUKS using Unity 8"
date: 2016-11-06
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2016-11-06
Hello. I encrypt my external drives with Ubuntu which is where my files are stored at.

[http://www.howtogeek.com/115955/how-to-quickly-encrypt-removable-storage-devices-with-ubuntu/](http://www.howtogeek.com/115955/how-to-quickly-encrypt-removable-storage-devices-with-ubuntu/)

^^^ This is the method that I have used. In the above url it mentions multiple times that this way of encryption relies on gnome. I believe that Unity 8 uses qt and is not based on gnome, will a Unity 8 session prevent me from being able to decrypt my drives?

---

### Post by Jeroen_Mathon on 2016-12-07
Hey TheMTtakeover,

It seems you are confused with backend and frontend software.
What you are talking about is the gui frontend for CryptSetup(The linux utility that can encrypt and decrypt files, similar to dm-crypt)

In short, Yes you can still access your files by running the following instructions.
CRYPTNAME can be anything but i recomend crypt1
```

sudo su
cryptsetup luksOpen  /dev/DEVICENAME CRYPTNAME
mount /dev/mapper/CRYPTNAME /mnt

```

Then you can cd into /mnt or any directory that you wish to mount it to and access your files.

To close your container for example when you need to disconnect the drive simply run the following and make sure that you are not in the directory of that drive or that any process is using a file on that drive.
```

sudo su
umount /mnt
crytpsetup luksClose CRYPTNAME

```

I hope that these instructions are sufficient for your problem.

---


---
title: "how to use a CD ISO as USB"
date: 2014-08-14
forum: New to Ubuntu
---

### Post by agarrett5 on 2014-08-14
How do I create a bootable USB with a CD ISO?  I have an iso of Discryptor boot CD and need to create a bootable USB with it.  How do I go about doing this in Ubuntu?

---

### Post by sotiris2 on 2014-08-14
Discryptor seems to be a program for windows OS. As in probably would break any ubuntu installations. So if you have a windows system you need encrypted you can use their windows [guide](https://diskcryptor.net/wiki/LiveCD). If you actually want to encrypt your ubuntu system you can check this [guide](https://help.ubuntu.com/community/FullDiskEncryptionHowto) or wait for someone more knowledgable about encryption posts here.

---

### Post by coldraven on 2014-08-14
Ubuntu comes with "Startup Disc Creator", open the Dash and type "start".
If that does not work then install Unetbootin from the Ubuntu Software Centre.
You can read about if here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

They both make bootable USB sticks, I generally use Unetbootin these days.

Edit: Sorry but I did not realise that it's a windows tool. Ignore my advice, it won't work.

---

### Post by sotiris2 on 2014-08-14
Indeed not only is it targeted to windows OS but it also is a windows based live cd so it wouldn't work with unetbootin. Unlike some windows oriented virus scanners / partitions editors that are based on live linux distributions.

---

### Post by sudodus on 2014-08-14
In linux you can use mkusb, that works independently of how the boot iso file is made except one thing: it must be a hybrid iso file. See these links
[URL="http://ubuntuforums.org/showthread.php?t=1958073"]
Howto make USB boot drives[/URL]

Download the files from
[http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/)

and there are more details at
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

If it does not work, you can make it a hybrid iso file like this: Make a copy first, because isohybrid will overwrite its source file, and it might work. Otherwise you might need a CD or DVD drive to run it.

```
cp file.iso file-orig.iso
isohybrid file.iso

sudo ./mkusb file.iso
```

---


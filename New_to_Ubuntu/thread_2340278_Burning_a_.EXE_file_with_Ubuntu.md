---
title: "Burning a .EXE file with Ubuntu"
date: 2016-10-17
forum: New to Ubuntu
---

### Post by funky01 on 2016-10-17
Hello

I have Ubuntu on all of my devices but had to install Widows 7 on a laptop to use mail software. I have installed Win 7 but I have non of the original Dell drivers. Dell have said I can burn a driver to disc in Ubuntu to then install onto the Windows systrem.

However the download file is a .EXE and i'm having no luck.

Can I.. How do I burn a .EXE file to a cd using Ubuntu 16.04 please

Thanks

---

### Post by howefield on 2016-10-17
Don't think the file manager can burn to a CD so you'd need to install an application capable of doing that, eg Xfburn or Brasero although it would be easier to copy the file to a USB stick and then on to the Windows PC from there.

---

### Post by funky01 on 2016-10-17
Ahh I see

Would a DVD have been better to burn to maybe?

Thanks Howfield

---

### Post by howefield on 2016-10-17
> **funky01 said:**
> Would a DVD have been better to burn to maybe?

The issue is the same whether it is a DVD or CD, you need to install an application to do the burning, eg

```
sudo apt install xfburn
```

Then use that to burn the files to the optical media.

---

### Post by buzzingrobot on 2016-10-17
Are you sure you need to "burn" this file rather than simply copy it?

Burning is not a file copying procedure.  The file system is not involved.  The process copies X bytes from one device to another.

Sounds as if you really just need to get that file copied over to Windows, where you can click on it to launch the driver install process. If you can copy it to a CD/DVD Windows can read, that's one way of moving it.  Same thing should work with a USB stick formatted with FAT. More cumbersome, but workable, is to copy the file to Dropbox/Google Drive/etc and then downloaded on the Windows system.  Or even attach it to an email to yourself and grab it via a browser (assuming that kind of mail provider) on the Windows machine.

(You can use Gparted in Ubuntu to format a USB stick with FAT. I *think* if you format it in Windows it will use FAT by default.)

---

### Post by SeijiSensei on 2016-10-17
Or format it from the command line with:
```
sudo mkfs -t vfat /dev/sdb1
```
Replace "sdb1" with the correct partition name on the USB stick.

---

### Post by Habitual on 2016-10-17
Dell EXEs typicallly are self-extracting EXEs that contain the necessary drivers.
I believe copying to the medium is sufficient. Then copy to the OS and run each .EXE on the target host.

---

### Post by Bucky Ball on 2016-10-17
Just wondering, and could be missing something ... if you have Windows 7 installed on the machine and want to install Windows 7 drivers from .exe files, can't you navigate to the Dell site and download them *on the Windows machine* and install them directly??? Is the Win7 machine completely inoperable without the drivers? Is IE not working in Win7?

That's how I've done it in the past.

---

### Post by kevdog on 2016-10-17
Why am I getting an inkling [https://unetbootin.github.io/](https://unetbootin.github.io/) needs to be used here to make the disc executable?

---

### Post by buzzingrobot on 2016-10-18
> **Bucky Ball said:**
> Just wondering, and could be missing something ... if you have Windows 7 installed on the machine and want to install Windows 7 drivers from .exe files, can't you navigate to the Dell site and download them *on the Windows machine* and install them directly??? Is the Win7 machine completely inoperable without the drivers? Is IE not working in Win7?

That's how I've done it in the past.        

   In my experience, Win7's install image lacks, at least, network drivers for hardware that's newer than it is.  It will install per normal, but you'll have no network on the reboot, and no way of using that new install to get the drivers. If someone doesn't have a vendor's driver CD, then grabbing the drivers from the vendor site and copying them to a FAT-formatted USB stick before doing the install is the way to go.

---


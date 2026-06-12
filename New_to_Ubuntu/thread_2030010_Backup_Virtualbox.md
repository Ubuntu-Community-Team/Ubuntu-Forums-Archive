---
title: "Backup Virtualbox"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by hhhlga89 on 2012-07-20
Hello.. I want to install ubuntu in virtualbox on my windows 7 desktop to get acclimated with it. I am getting a laptop soon and want be familiar with Ubuntu before I install it on the laptop. How can I backup files and programs installed in the virtualbox so that I can transfer them to Ubuntu on my laptop when I receive it? If that's possible, I think it is:confused: and is it worth it? I don't want to dualboot..Thanks alot.

---

### Post by Lyfang on 2012-07-20
[https://wiki.ubuntu.com/WubiGuide#Misc.](https://wiki.ubuntu.com/WubiGuide#Misc.) & see: How do I migrate to a real partition, and/or get rid of Windows entirely?

If you start with a new Ubuntu installation on a brand new computer without backing up programs:
&#8226; Easy way: Copy over your files using an USB flash drive.

&#8226; Advanced: If you have access to the root.disk (C:\ubuntu\disks\root.disk) file from your old computer, you can mount it in Ubuntu & copy over all your personal files: [http://ubuntuforums.org/showpost.php?p=11984876&postcount=4](http://ubuntuforums.org/showpost.php?p=11984876&postcount=4) The drawback is you'll have to install all software using the repositories instead of migrating the software using wubi-move-2.2.tar.gz.

---

### Post by sudodus on 2012-07-20
wubi or virtualbox?

Anyway, if you have not installed any proprietary drivers, an Ubuntu installation is truly portable. You should be able to clone it to a USB drive (if there is space enough), and then clone it once more to the final destination in some computer.

You can clone a drive with ***Clonezilla***, but you can also make a compressed image (to squeeze more data into a limited space).

---

### Post by TheFu on 2012-07-20
> **hhhlga89 said:**
> Hello.. I want to install ubuntu in virtualbox on my windows 7 desktop to get acclimated with it. I am getting a laptop soon and want be familiar with Ubuntu before I install it on the laptop. How can I backup files and programs installed in the virtualbox so that I can transfer them to Ubuntu on my laptop when I receive it? If that's possible, I think it is:confused: and is it worth it? I don't want to dualboot..Thanks alot.

The other replies might be what you want, but I think you are just interested in exporting the entire VM that you created inside virtualbox and loading it into another virtualbox installed on the new laptop, correct?  That is easy.  In virtualbox's GUI, File --> Export Appliance.

Those files can be imported into virtualbox on the newer PC.

VirtualBox is perfect for this, but any other virtualization technology can accomplish the same thing. For desktop virtualization, VirtualBox is pretty easy. Enjoy.

None of this is done inside the virtual machine and the VM needs to be shutdown during this.  If you need a command line way on MS-Windows, use 
```

"c:/Program Files/Oracle/VirtualBox/VBoxManage.exe"  export "$vm"  -o "P:/VM-Backups/$vm.ovf"

```Just change the $vm into the name and output location desired your VM export.  BTW, that command is part of my weekly VM backup method. It works.

---

### Post by Lyfang on 2012-07-20
hhhlga89 was talking about Wubi at first. However since hhhlga89 edited & is now talking about VirtualBox, exporting a Virtual Machine could work in this case? Moving the VM to the newly installed VirtualBox on the new computer. Go to VirtualBox & see if you can find "Export Appliance" & "Import Appliance". May I ask why you would like to backup your programs, hhhlga89?

---

### Post by hhhlga89 on 2012-07-21
Thanks alot guys. All your post were very helpful. The first responce was more of what I was thinking about.

---

### Post by TheFu on 2012-07-23
> **hhhlga89 said:**
> Thanks alot guys. All your post were very helpful. The first responce was more of what I was thinking about.

So let me understand ... you aren't using virtualbox at all?

---

### Post by Bufeu on 2012-07-23
Yes, you can backup and move a VM to a "real" (host) machine.
Just boot up [CloneZilla]("http://sourceforge.net/projects/clonezilla/files/clonezilla_live_stable/1.2.12-67/") on the VM and clone the VM onto a external storage device. When you get your laptop, just plugin that storage device with the clone into the laptop. Boot up CloneZilla and use the "restoredisk"-option.

---


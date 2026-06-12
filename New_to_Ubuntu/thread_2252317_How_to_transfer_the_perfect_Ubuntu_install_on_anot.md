---
title: "How to transfer the perfect Ubuntu install on another computer?"
date: 2014-11-11
forum: New to Ubuntu
---

### Post by zircon_34 on 2014-11-11
Hi, its been a while I am switching back and forth between mac OSX and linux, the latter being more exciting desktop wise and also better programming environment for me! but I am still newbie to the linux workflow.

I have now Ubuntu 14.04 installed as dual boot and virtual desktop on 3 different computers. On one I have the perfect install of programs, desktop gnome with extensions etc... My question is how to transfer this perfect install on another computer? So I can avoid re installing all packages and re-select each software on all 3 computers.

Perhaps the best way would be to install ubuntu on an external hardrive and use this install to transfer to my other computers, Which software can you recommend for this? I heard about fsarchiver, is this the correct tool for the task?

Thanks for any suggestions :p

---

### Post by sudodus on 2014-11-11
Such copying is usually possible, but there are a few things, that might create problems.

- Avoid proprietary drivers (typically for graphics and wifi) unless the target computer needs the same drivers. You can (re-)install such drivers after porting the system.

- Systems installed from the Ubuntu flavour desktop iso files have portable network systems, but the system installed from Ubuntu mini.iso is not portable unless you tweak it (use network manager).

- If you have a dual boot system with MacOS or Windows, and it is running in UEFI mode, there can be problems with booting. Also you need to consider 64-bit versus 32-bit systems and computers.

If the computers are very different, it is easier to make separate installations. You can use an installed system on an external drive to test how it works before trying to install it into an internal drive.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

-o-

- if you want to clone the whole drive to another drive of the same size or bigger, you can use Clonezilla.

- fsarchiver can be used and there are threads here at the Ubuntu Forums describing how to use it.

- rsync is another option

- make a tarball with the One Button Installer and install from the tarball to another drive or partition

See this recent link
[URL="http://ubuntuforums.org/showthread.php?t=2252075"]
Suitable cloning software to move Ubuntu 14.04 to another partition?[/URL]

---

### Post by mastablasta on 2014-11-11
I used this to clone my windows xp from disk to disk directly. can be done with Linux as well.: [http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

---

### Post by zircon_34 on 2014-11-12
> **sudodus said:**
> Such copying is usually possible, but there are a few things, that might create problems.

- if you want to clone the whole drive to another drive of the same size or bigger, you can use Clonezilla.

- fsarchiver can be used and there are threads here at the Ubuntu Forums describing how to use it.

- rsync is another option

- make a tarball with the One Button Installer and install from the tarball to another drive or partition



Hey thanks! I heard that fsarchiver might be better as clonezilla might not work on drives with different sizes. I did not know that fsarchive also copies all the software and installed packages. I thought it was only used for backing up files. I will give it a try.

---

### Post by mastablasta on 2014-11-12
> **zircon_34 said:**
> ....as clonezilla might not work on drives with different size..
clone is a bit-by-bit copy of the disk. if disk is of same size or larger than original then clone will not be an issue in Clonezilla (I used it to clone an old 130 GB disk to 1TB disk and then I moved & expanded the partitions over the whole new disk). if target disk is smaller then it is a bit more harder to do it.

---

### Post by jimmyh1972 on 2014-11-12
I didnt understand if your Ubuntu is installed on your HD or its virtual-box
Assuming you have it on your HD you can use _**dd**_ commands to create an ISO of your system and to install it on another HD
if its a virtual -box you can export appliance and import it on another machine
you are very welcome to write to me in private to extend explanation and help

---

### Post by sudodus on 2014-11-12
***dd*** is a very powerful tool, and can clone whole drives as well as partitions. But it has no 'safety belt' and has caused many big disasters because it does what you tell it to do without questions - and you can tell it to do something else than what you intended to do by mistake or even a typing error. So it is nick-named 'disk destroyer'. When I use dd, I double-check and triple-check before running the command.

***Clonezilla*** is much safer to use. It has also the advantage, that it only copies used blocks, which makes it much faster than dd, particularly when only a small fraction of a partition is used.

---

### Post by sandyd on 2014-11-12
> **jimmyh1972 said:**
> I didnt understand if your Ubuntu is installed on your HD or its virtual-box
Assuming you have it on your HD you can use _**dd**_ commands to create an ISO of your system and to install it on another HD
if its a virtual -box you can export appliance and import it on another machine
you are very welcome to write to me in private to extend explanation and help

You can image a virtualbox image to disk if you want as well as long as it is some kind of Linux distro and the HDD is larger than the VM. The same goes for qcow2 and all the other formats the lovely virt-manager supports (though you have to convert qcow2 to RAW before dding the thing onto the HDD).

This also assumes that you are not dding onto the disk that contains the VM or a disk thats being used.

---

### Post by monkeybrain20122 on 2014-11-12
> **zircon_34 said:**
> Hey thanks! I heard that fsarchiver might be better as clonezilla might not work on drives with different sizes. I did not know that fsarchive also copies all the software and installed packages. I thought it was only used for backing up files. I will give it a try.

That's right. I use fsarchiver for exactly that purpose you describe. The only catch is that it works only with mbr so no gpt uefi etc.

---

### Post by zircon_34 on 2014-11-13
I have one install dual boot OSX and linux with GPT partition and the other installs on virtual desktops on the other computers within OSX. will check fs archiver and clonezilla this weekend. any reason to try rsync over fsarchiver? I read that rsync is incremental but not sure if it is usable for syncing a whole  filesystem.

---

### Post by sudodus on 2014-11-13
When you mention OSX and GPT, I think you have [U]EFI.

***rsync*** can be used for a whole file system. It is actually the engine under the hood of many backup application programs. It takes some time to learn, but it is well worth the effort, because it is a powerful and reliable tool. There are some tasks that must be done separately (by other tools than rsync). For example, you may need to edit the file **/etc/fstab** to match the UUIDs of the partitions used by the system. And you need to [re]install ***grub*** and update grub with separate tools.

---

### Post by Bucky Ball on 2014-11-13
Make ISO with Clonezilla and install it to the other partition (of equal or larger size) as has been suggested. Here are some helpful links.

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Size has been mentioned, but also keep this in mind. If you have a 50Gb partition you want to clone, even though the install might only be 15Gb on the 50Gb partition, _*the partition you clone TO MUST also be 50Gb or larger*_. The actual size of the install is irrelevant. It is the size of the partition you are cloning from and to that counts.

Consequently, you might want to boot from live media, get to a desktop, launch gparted and shrink the partition you want to clone prior to cloning with Clonezilla.

My 2cents. Good luck. ;)

---

### Post by zircon_34 on 2014-11-15
thanks for the links:popcorn:

---

### Post by matt_symes on 2014-11-16
Hi

Having used all the methods highlighted by sudodus to clone hard drives, except fsarchiver, i would also recommend clonezilla.

It's just easier as long as you don't mind the text driven interface.

Kind regards

---

### Post by gacb on 2015-02-16
There's a nice GUI application called Aptik which is available in the PPA's. If you have an external hard drive you can easily backup and restore with a few clicks. One caveat - use the same username when doing a fresh install.

---


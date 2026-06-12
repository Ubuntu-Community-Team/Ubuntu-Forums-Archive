---
title: "Fedora doesnt show on boot menu"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by muti88 on 2012-10-13
Hello! I have been reading for over two hours how to get fedora to show up boot menu.

[http://paste.ubuntu.com/1277445/](http://paste.ubuntu.com/1277445/) Here is my paste from boot-repair.

SDA is ssd (120g) and SDB is hdd (500g) which i have been formatted badly. If anyone could help me to get fedora showing on boot menu with windows and ubuntu, it would be great

And if someone can tell me how i can rename those partitions. I think that sdb3 and sdb is fedora. How i can confirm it?

Thanks:confused:

---

### Post by sandyd on 2012-10-13
I never got it to show either.

I eventually gave up and decided to use chainloading. Add this to /etc/grub.d/40_custom (while adjusting the root to match your fedora install)


```

menuentry "Fedora" {
set root=(hd,6)
chainloader +1
}

```

---

### Post by muti88 on 2012-10-13
> **sandyd said:**
> I never got it to show either.

I eventually gave up and decided to use chainloading. Add this to /etc/grub.d/40_custom (while adjusting the root to match your fedora install)


```



```

```
menuentry "Fedora" {
set root=(sdb3)
chainloader +1
}
```
Doesnt help anything. Should i use update-grub? Am i using right root?

---

### Post by sandyd on 2012-10-13
You have to add it to /etc/grub.d/40_custom, run update-grub.

I am not sure about the partition number, but you are using a LVM volume for Fedora.

As a result, your /boot partition for fedora is outside of the main LVM Volume (sdb6), and in (sdb5)


Perhaps, use 
```

menuentry "Fedora" {
set root=(1,5)
chainloader +1
}

```

---

### Post by muti88 on 2012-10-13
Error, no such disc found.
Would it help if format whole sdb, reinstall ubuntu and install fedora after that? Does fedora know/see ubuntu?

Thanks

---

### Post by ajgreeny on 2012-10-13
I presume sdb6 is fedora as it is the LVM volume which fedora uses by default.

That is a bit of a problem for me as I do not understand LVM and when I installed fedora in a multiboot system with Ubuntu 10.04 as the main OS, I chose to partition manually and use "standard" partitions. I also see that you have GPT partitions which once again I do not fully understand.

I have no idea if LVM is a problem in grub 2 as I have never used LVM, but I could not get fedora to boot from the ubuntu grub in my system to start with and only managed to do so by manually editing the grub configuration file **/etc/grub.d/40_custom**, making it executable, and removing execution permissions from **/etc/grub.d/30_os-prober.**

The stanza I added to 40_custom for fedora was
```
menuentry 'Fedora 17, sdb5' --class fedora --class gnu-linux --class gnu --class os {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    search --no-floppy --fs-uuid --set=root d64e1d1a-1faf-4990-a0b1-88f109461473
    linux    /boot/vmlinuz-3.5.4-2.fc17.i686 root=UUID=d64e1d1a-1faf-4990-a0b1-88f109461473 ro quiet splash $vt_handoff
    initrd /boot/initramfs-3.5.4-2.fc17.i686.img
}
```which is quite different from the entry that grub puts in the /boot/grub/grub.cfg file when you run sudo update-grub.  I only managed to get this grub entry working by trial and error, making it look as similar to those for ubuntu as I could.

The alternative, of course is to use grub from fedora on your system, which certainly has added ubuntu and may allow you to boot both OSs.  You may already have that available to you if you boot from the other disk, sda or sdb, depending on what you use at the moment.

If you prefer to use Ubuntu's grub, try what I did and edit the 40_custom file.  You will need to change the UUID and the **set root='hd1,msdos5'** to fit your system, and I am not sure how you do that with a GPT formatted disk or partition.

Sorry I can not be more helpful but fedora is difficult to deal with in my opinion, mainly because of the LVM partitioning, but also because I have just got so used to the *ubuntu family that I am a bit lost with others.

EDIT:
I have just seen you query about reinstalling, and my first thought is to reinstall fedora only by deleting the partitions that it made when you installed it and then manually partitioning to avoid the LVM.  There is no reason to reinstall ubuntu if that is working well.

To make life easier boot to ubuntu and run sudo grub-install /dev/sda then when you install fedora with manual partitions, make sure grub goes on to /dev/sdb.  You will now have a system with "normal" partitions and two grub bootloaders, one from ubuntu on sda, a second from fedora on sdb,

---

### Post by oldfred on 2012-10-13
Some have posted that installing the lvm2 driver and mounting the Fedora partition before running the sudo update-grub works. 

Some also have suggested when dual or multi-booting not to use LVM. The advantage of LVM is easily resized partitions but if the LVM is trapped inside other partitions that are not LVM you cannot easily use the resize feature and then it just is another level of complexity.

sudo apt-get install lvm2

---

### Post by NikTh on 2012-10-13
> **oldfred said:**
> mounting the Fedora partition before running the sudo update-grub works. 

Yes , that works. 

We assume that your Fedora partition is /dev/sda3 , from Ubuntu do 

```
sudo mount /dev/sda3 /mnt 
sudo update-grub
```

Thanks

---

### Post by muti88 on 2012-10-14
Thank you all.

Solved

---

### Post by ajgreeny on 2012-10-14
> **muti88 said:**
> Thank you all.

Solved
After all the answers given to you, how was it solved?  This is always useful for future users who have the same problem.

---


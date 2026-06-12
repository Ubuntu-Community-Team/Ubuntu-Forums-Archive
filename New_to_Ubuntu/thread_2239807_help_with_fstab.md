---
title: "help with fstab"
date: 2014-08-15
forum: New to Ubuntu
---

### Post by charliek2 on 2014-08-15
Hi,
my fstab is messed up and doesn't contain all my partitions, so I wanted to clean it up.
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=6697617d-165d-46b4-8fbb-3c0c0cc0a98f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=3C01-F4F3  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda8 during installation
UUID=70ae55ae-cea6-4790-b257-6a4481b60543 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=99087846-00d6-4535-bc3d-c9d6c39f8033 none            swap    sw              0       0
```

So I read some stuff, but I still would really like to get some help.

sudo blkid
```
/dev/sr0: LABEL="CDROM" TYPE="udf" 
/dev/sda1: UUID="3C01-F4F3" TYPE="vfat" 
/dev/sda3: UUID="86D8133FD8132D45" TYPE="ntfs" 
/dev/sda4: LABEL="Volume" UUID="6AAC3D8DAC3D54B3" TYPE="ntfs" 
/dev/sda5: UUID="6697617d-165d-46b4-8fbb-3c0c0cc0a98f" TYPE="ext4" 
/dev/sda7: UUID="eee2b672-e5f8-499d-8dc8-10d379becf1c" TYPE="swap" 
/dev/sda8: UUID="70ae55ae-cea6-4790-b257-6a4481b60543" TYPE="ext4"
```

gparted 
[http://image-upload.de/image/sQTweE/5bdf728bff.png](http://image-upload.de/image/sQTweE/5bdf728bff.png)

Could someone please give me one or two example lines with my partitions and a short explanation?

Thanks! :))

---

### Post by deadflowr on 2014-08-15
It looks like your swap partition UUID is wrong in fstab vs the UUID in blkid.

Beyond that, what do you find missing?

---

### Post by mansonfan78 on 2014-08-15
As deadflowr mentioned, your swap uuid is wrong - fix that first.  It should be noted that fstab only includes devices that are mounted automatically at startup, this does not normally include ntfs partitions/drives or cd/dvd drives (those typically get mounted only when you try to access them).  If you need them mounted at startup you could add them manually if you want or install ntfs-config and let it set it up for you.

---

### Post by charliek2 on 2014-08-16
Okay, thank you.
I changed the swap UUID in my fstab and it looks like everything is ok now. I guess I looked for something to blame for the error I get while compiling (I changed some partitions before) the kernel but never mind, I will do another thread therefore, I guess.


```
objcopy --add-gnu-debuglink=/home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/usr/lib/debug/lib/modules/3.15.9-no-bfs-kernel/kernel/drivers/pps/clients/pps-gpio.ko /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/kernel/drivers/pps/clients/pps-gpio.ko
objcopy --only-keep-debug /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/usr/lib/debug/lib/modules/3.15.9-no-bfs-kernel/kernel/drivers/pps/clients/pps-ldisc.ko
objcopy --add-gnu-debuglink=/home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/usr/lib/debug/lib/modules/3.15.9-no-bfs-kernel/kernel/drivers/pps/clients/pps-ldisc.ko /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/kernel/drivers/pps/clients/pps-ldisc.ko
objcopy --only-keep-debug /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/usr/lib/debug/lib/modules/3.15.9-no-bfs-kernel/kernel/drivers/pps/pps_core.ko
objcopy --add-gnu-debuglink=/home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/usr/lib/debug/lib/modules/3.15.9-no-bfs-kernel/kernel/drivers/pps/pps_core.ko /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/kernel/drivers/pps/pps_core.ko
rm -rf /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/usr/lib/debug
test ! -f tools/lguest/lguest ||                 \
        install -p    -o root -g root  -m  644 tools/lguest/lguest /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/lguest
test ! -f /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/lguest ||           \
        chmod 755 /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/lguest
test ! -e /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/source ||              \
       mv /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/source ./debian/source-link
test ! -e /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/build ||              \
       mv /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/build ./debian/build-link
test ! -e ./debian/source-link ||                           \
       mv ./debian/source-link /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/source
test ! -e  ./debian/build-link ||                           \
       mv  ./debian/build-link /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/modules/3.15.9-no-bfs-kernel/build
/sbin/depmod -q -FSystem.map -b /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel 3.15.9-no-bfs-kernel;
restore_upstream_debianization
test ! -f scripts/package/builddeb.kpkg-dist ||    mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/Makefile.kpkg-dist ||    mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
/usr/bin/make EXTRAVERSION=-no-bfs-kernel INSTALL_MOD_PATH=/home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel         \
        INSTALL_FW_PATH=/home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel/lib/firmware/3.15.9-no-bfs-kernel  \
        INSTALL_PATH=/home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel//boot  install
make[2]: Betrete Verzeichnis '/home/home/kernel/linux-3.15.9'
scripts/kconfig/conf --silentoldconfig Kconfig
make[2]: Verlasse Verzeichnis '/home/home/kernel/linux-3.15.9'
make[2]: Betrete Verzeichnis '/home/home/kernel/linux-3.15.9'
sh /home/home/kernel/linux-3.15.9/arch/x86/boot/install.sh 3.15.9-no-bfs-kernel arch/x86/boot/bzImage \
        System.map "/home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel//boot"
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.15.9-no-bfs-kernel /home/home/kernel/linux/debian/linux-image-3.15.9-no-bfs-kernel//boot/vmlinuz-3.15.9-no-bfs-kernel
**/etc/kernel/postinst.d/apt-auto-removal: 84: /etc/kernel/postinst.d/apt-auto-removal: cannot create /etc/apt/apt.conf.d//01autoremove-kernels.dpkg-new: Permission denied**
run-parts: /etc/kernel/postinst.d/apt-auto-removal exited with return code 2
make[3]: *** [install] Fehler 1
make[2]: *** [install] Fehler 2
make[2]: Verlasse Verzeichnis '/home/home/kernel/linux-3.15.9'
make[1]: *** [debian/stamp/install/linux-image-3.15.9-no-bfs-kernel] Fehler 2
make[1]: Verlasse Verzeichnis '/home/home/kernel/linux-3.15.9'
make: *** [kernel_image] Fehler 2
```
tyvm

---

### Post by sandyd on 2014-08-16
> **charliek2 said:**
> Okay, thank you.
I changed the swap UUID in my fstab and it looks like everything is ok now. I guess I looked for something to blame for the error I get while compiling (I changed some partitions before) the kernel but never mind, I will do another thread therefore, I guess.


```

**/etc/kernel/postinst.d/apt-auto-removal: 84: /etc/kernel/postinst.d/apt-auto-removal: cannot create /etc/apt/apt.conf.d//01autoremove-kernels.dpkg-new: Permission denied**

```
tyvm

From what it looks like, you need to run the command as sudo as a normal user has no rights to write to that folder.

---


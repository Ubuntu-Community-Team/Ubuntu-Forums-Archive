---
title: "making an Ubuntu 8.04 Live CD with custom kernel?"
date: 2008-06-17
forum: Packaging and Compiling Programs
---

### Post by gradedcheese on 2008-06-17
Hi.  I need to create a modified Ubuntu 8.04 Live CD with a custom kernel (2.6.26-rc5 at the moment).  I'm testing my modified ISO by booting it in quemu.  It boots but drops to the busybox shell.  

To build my kernel, I grab the kernel source, use my stock (2.6.24) config as a baseline and 'make oldconfig', make some changes, and then build packages of the kernel:

```

$ make-kpkg clean
$ fakeroot make-kpkg --initrd --append-to-version=-mytag kernel_image kernel_headers

```

I install this on my host PC and it boots fine.

I then followed instructions on [the Wiki]("https://help.ubuntu.com/community/LiveCDCustomization") for unpacking a stock Live CD ISO, chrooting to it, making changes, and packing up a new CD.  In my case, I remove the stock kernel and some other packages (openoffice, etc), install the new kernel, and make sure that /lib/modules and /lib/firmware have the right directories.  I also copy the initrd and vmlinuz to 'casper' on the 'new' CD.

Does anyone know how to troubleshoot the 'dropping to busybox' problem?  Given the instructions on the Wiki and the way I build the kernel packages, is there something I'm likely doing wrong?  Thanks!

---

### Post by LK.Atwork on 2008-06-27
Hi GradedCheese,

I am facing the identical problem and am wondering how you solved this issue.

thanks
LK

---

### Post by gradedcheese on 2008-06-27
I have solved it, though it's a bit of a pain:
1) patch the kernel to have squashfs support.  I did this by applying the WRT project's 2.6.26 squashfs patch and then updating the squashfs files with those from Ubuntu's development git.  The correct thing to do would have been to apply the squashfs stuff from development git to my kernel, and that's what I'd recommend.
2) patch the kernel to have unionfs support.  I did this by grabbing the unionfs git, but it can be brought over from the Ubuntu development git.  My kernel is newer than theirs, so I used the unionfs git.

When you configure the kernel, enable the loop mount block device, squashfs, and unionfs.  When you mksquashfs, use -nolzma if you're on Hardy (or using recent squashfs tools).  Otherwise, following the instructions on [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) works out well.

---

### Post by LK.Atwork on 2008-06-27
Thanks for the prompt response.

The link you gave me is the exact one I used to make my LiveCD.
This LiveCD is to be used on another platform that requires Intel SCH support.

Basically, I started out with Ubuntu 8.04 LTS desktop.
I then downloaded and built kernel 2.6.26.rc7 which has Intel SCH support.
I also added support for squashfs3.3 using the additional patch. I selected
squashfs to be a module (and maybe that is a mistake).
I rebooted the system with my new kernel and then followed the steps in the URL you gave me.

One extra step I added was to copy /lib/modules/<my custom kernel> to the LiveCD

Also I did not use unionfs.
When I get home this evening, I will try to add unionfs and see if it helps.

Have I done anyting wrong so far?

once again, thanks for your help
LK

---

### Post by gradedcheese on 2008-06-27
You need squashfs and unionfs, either built-in (not modules) or packed into the initrd.  I would build them in (along with the loop module) and not deal with initrd though.  If you boot and are dropped into a busybox shell, cat /casper.log or something like that (look in /) to see what the error was.  You'll see something about failing to mount the squashfs or failing to do a unionfs mount.  The messages are pretty helpful.

---

### Post by LK.Atwork on 2008-06-28
Hi,

I have never used git before.
How do I correctly install unionfs using git? Here is what I did:

cd /usr/src/linux
git clone git://git.kernel.org/pub/scm/linux/kernel/git/ezk/unionfs.git

This downloaded 198MB of data and it created /usr/src/linux/unionfs where it installed the full linux source code (including fs/unionfs)

All I want to do is to get the correct version of unionfs into /usr/src/linux/fs

Thanks for your help.
LK

---

### Post by LK.Atwork on 2008-06-29
Hi,

I was able to git union fs as follows:
untarred linux-2.6.26-rc7.tar.bz2
git-init
git add . 
git pull git://git.kernel.org/pub/scm/linux/kernel/git/ezk/unionfs.git

Although unionsfs was pulled down, my linux dropped from linux-2.6.26-rc7 to linux-2.6.26-rc1. Is there a way that I can avoid this?

thanks
LK

---

### Post by LK.Atwork on 2008-06-29
Hi,

I compiled in (built in) support for loopback device, squashfs and unionfs and I see messages indicating that they are up and running.

However, when I boot, I am still dropped to busybox and casper.log says

Begin: Running /scripts/casper-premount...
Done
Done
/Init: /Init: 1: cannot open /dev/sr0: no such file
this msg repeats like 20 times
....
Unable to find a medium containing a live file system

Basically, CD-ROM drive is being detected but not attached, due to which it does not find the squash file system.

I compared the output between a working kernel and mine and I see that in the working kernel, CD-ROM is being attached by the sr driver, while in my not working kernel, it being attached to a scsi driver.

On working system, the message is:
Uniform CD-ROM driver Revision: 3.20
sr 1:0:0:0 Attached scsi generic sg0 type 5

On not working system, the message is:
scsi 1:0:0:0 Attached scsi generic sg0 type 5
Uniform CD-ROM driver Revision: 3.20

In the not working kernel, the uniform cd-rom driver is brought up after the drive is attached.

Any idea how I can go about fixing this problem?

thanks
LK

---

### Post by gradedcheese on 2008-07-02
Did you copy your vmlinuz and initrd.gz to the casper directory?  That's the kernel and initrd that's actually used to boot.

---

### Post by ColleysForEver on 2008-12-05
Thanks to gradedcheese and LK.Atwork,

Apparently, this problem is already solved, but having the same thing to deal (creating a Custom Live CD with 2.6.26 kernel), I've managed to get it in a more classical way without using git (saving time and hundred of Mb). 

Get the linux sources archive from [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)
uncompress acrhive to /usr/src and symlink to /usr/src/linux
get the right unionfs source patch from
[http://download.filesystems.org/unionfs/stable/](http://download.filesystems.org/unionfs/stable/)
and uncompress it in /usr/src/linux
get the squashfs source patch from 
[http://sourceforge.net/project/showfiles.php?group_id=63835&package_id=60859&release_id=622329](http://sourceforge.net/project/showfiles.php?group_id=63835&package_id=60859&release_id=622329)
Extract the right patch from archive into /usr/src/linux

Patch the sources :
patch -p1 < {unionfspatchfile}
patch -p1 < {squashfspatchfile}

edit /usr/src/linux/security/security.c
After
int security_inode_permission (......) {
....
....
}
add the following line:
EXPORT_SYMBOL(security_inode_permission);

Otherwise, it will fail when compiling.

Follow 'classical' way to get .config, make config (enable squashfs, unionfs and loop device, either build-in or module), build image and headers packages, install created packages.

If you want to compile something else using the kernel-header, you must correct the kernel-header created:
first:
save /usr/src/linux/arch/x86/Makefile_32.cpu file
and copy it to /usr/src/linux-headers-{your rev}/arch/x86/
second:
make symblink between /usr/src/linux-headers-{your version}/include/asm and /usr/src/linux-headers-{your version}/include/asm-x86 

To create the Live CD, I use remastersys.

If you want to enable persistence in casper, you need to correct the initrd image. To make remastersys make the correction itself, add the following lines to /usr/bin/remastersys, right after the line  "cp /initrd.img $WORKDIR/ISOTMP/casper/initrd.gz" :
mkdir $WORKDIR/initrd-remake
cd $WORKDIR/initrd-remake
mkdir initrd-old
cp $WORKDIR/ISOTMP/casper/initrd.gz initrd_old.gz
cd initrd-old
gunzip < ../initrd_old.gz | cpio -i --make-directories
cd scripts
sed -i s/,mode=755// casper
cd ..
gzip initrd
cp initrd.gz $WORKDIR/ISOTMP/casper/


Enjoy your new customized liveCD ...

---

### Post by Schoappied on 2009-05-23
Hi,

I tried to install the linux-rt kernel from Ubuntu in Hardy and add that to the live-cd. It seems to go well, but when I boot it in vbox it awful slow. What could be the cause of this? (it's not an vbox problem)
Thanks in advance

edit: it seems to boot fine, but it takes about 30 - 60 min. no kidding :/
(setting system clock [fail], don't know if that's valuable info)

edit2: I think it has something to do with the fact that it is an RT kernel (from Ubuntu STudio). Solutions are welcome!

---

### Post by mdrake36 on 2010-04-25
Did you insert the Kernel that was on the Host RT system?
I want to do this exact thing?
BUMP.

---


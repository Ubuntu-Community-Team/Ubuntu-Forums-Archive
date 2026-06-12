---
title: "Just Installed, can't boot &quot;UUID does not exits"
date: 2022-08-12
forum: New to Ubuntu
---

### Post by anael03100 on 2022-08-12
Hi !
So, I've just decided that I wanted to start using linux so I installed Ubuntu 22.04 alongside my windows install and everything went well, until I tried to change my NVidia driver, after that whenever I try to boot it just stops after saying ```
"ALERT! UUID={Lots of characters that I don't wanna type} does not exist. Dropping to a shell!
```

I could just reinstall my OS but that's no fun, I wanna try and understand what's happening.

By googling a bit I already tried using the boot repair tool and it didn't solve the problem.

My machine is an Asus Vivobook Pro 16X with an Nvidia RTX 3050 and an [COLOR=#212529][FONT=Arial]Intel Core i7-11370H[/FONT][/COLOR].

Thanks in advance for the help and sorry if I don't understand everything, I'm very new to linux :).

---

### Post by oldfred on 2022-08-12
You do not normally just change nVidia driver.
Ubuntu installs correct driver as part of install if you select to install restricted drivers.
And if you do change drivers you have to totally purge old driver first or you get conflicts.

Did you install driver from Ubuntu repository?

But UUID not missing is probably not related to Video driver.
Did you do an abnormal shutdown which may damage partition. You would then need fsck or e2fsck on all ext4 partitions.

Post link to the Summary report that Boot Repair gives.

---

### Post by anael03100 on 2022-08-12
> **oldfred said:**
> 
Did you install driver from Ubuntu repository?


I used the software & updates app, when I saw that there was a more recent driver that was marked as tested, I thought it was a good idea to switch to that one, I'll think twice next time :eek:

> **oldfred said:**
> 
Did you do an abnormal shutdown which may damage partition.


Nope, the app prompted me to restart so I just did it normally using the GUI
 
Here's the boot repair summary
[https://paste.ubuntu.com/p/Znq8tcYkJ9/](https://paste.ubuntu.com/p/Znq8tcYkJ9/)

I also managed to start Ubuntu by going in the advanced boot settings for Ubuntu in GRUB and selecting the second version

---

### Post by oldfred on 2022-08-12
Report looks like standard dual boot install in UEFI boot mode.

Did nVidia driver not get correctly installed in the newer -46 kernel?
Or did an UEFI update by either Windows or fwupdate in Ubuntu change UEFI settings to defaults?
And then is a setting in UEFI for which video is used Internal or nVidia? May have to review manual to see settings details. 

With -46 kernel can you boot recovery mode? That adds nomodeset for a default video.
If you can get to terminal you can purge & reinstall nVidia drivers.
Or both kernels may get updated with purge & reinstall with -25 kernel.

If wrong nVidia driver or upgrade, you must purge & install correct driver, you now do not need ppa as Ubuntu repository has correct drivers.
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by TheFu on 2022-08-12
I've seen a few people with nvidia driver caused issues the last few weeks. I haven't seen anything related to storage, however.

So, first, video drivers in Linux aren't like MS-Windows. Only use the approved-by-Canonical versions of the driver. I suspect you are, but something got screwed, somehow.  Prior to 22.04, we could just run
```
sudo ubuntu-drivers autoinstall 
```
and all would be handled.  I read somewhere that now the exact driver version has to be specified in 22.04 for some reason.  I don't know why.  This is an nvidia thing. AMD and Intel GPU drivers are built into the kernel and "just work".  Someday, nvidia will finally make this stuff easy ... er ... like all the other major vendors have for years now.

Update: I see you've run the boot-repair and posted a URL that doesn't allow access (to me).

The install flash drive has a "Try Ubuntu" option. That can always be used for emergency and troubleshooting needs. I've used it to run a system for 5 days after the HDD failed, while I waited for a replacement to arrive.  It is a very handy thing to have.

BTW, dual booting with MS-Windows can cause some issues. MSFT tends to ignore Linux and "fixed" boot stuff whenever they like, without asking first. Expect this to happen about once a year on any dual boot system with MS-Windows.

---

### Post by anael03100 on 2022-08-12
> **oldfred said:**
> 
Did nVidia driver not get correctly installed in the newer -46 kernel?

I think it installed correctly, the app didn't return any error.
> **oldfred said:**
> 
Or did an UEFI update by either Windows or fwupdate in Ubuntu change UEFI settings to defaults?
And then is a setting in UEFI for which video is used Internal or nVidia? May have to review manual to see settings details.

I didn't launch my windows installation since I installed ubuntu so I don't think so, and I don't have any settings to select the integrated or discret GPU in EUFI...
> **oldfred said:**
> 
With -46 kernel can you boot recovery mode? That adds nomodeset for a default video.
If you can get to terminal you can purge & reinstall nVidia drivers.
Or both kernels may get updated with purge & reinstall with -25 kernel.

No, the recovery mode also drops me to initram
> **oldfred said:**
> 
If wrong nVidia driver or upgrade, you must purge & install correct driver, you now do not need ppa as Ubuntu repository has correct drivers.

> **TheFu said:**
> 
Prior to 22.04, we could just run
```
sudo ubuntu-drivers autoinstall 
```
and all would be handled.

I tried doing that in the -25 kernel but it didn't solve the issue, but  again due to my limited understanding of how linux works, I don't  really know if I only purged the -25 kernel drivers or both

> **TheFu said:**
> 
Update: I see you've run the boot-repair and posted a URL that doesn't allow access (to me).

Strange, I think you just need to connect to SSO, is it still unaccessible ?

---

### Post by oldfred on 2022-08-12
If you have not recently gone to the pastebin site, you just have to click log in. 
Then it seems to want you to post something, but come back & click again and it works to open the link.

---

### Post by TheFu on 2022-08-13
> **anael03100 said:**
> Strange, I think you just need to connect to SSO, is it still unaccessible ?
Perhaps. 

I have hundreds of online accounts and don't need another.  I'm stubborn that way. Nothing you did wrong.  Different people have different lines they won't cross and others they will.  I feel that "looking" at stuff should be open to the world, unless there's good reason for that not to be the situation.  There's nothing left in any of these system information tools that are worth being private over.  The new system-info tool (google ubuntuforums system info to find it on github), by default, also posts to a login-mandated pastebin. But it can post to other pastebin locations too.  Of course, we've all written our own sys-info tools for our needs, but the one in github has lots of experts here contributing and should work for not just ubuntu (and 3 versions of it), but debian, mint, the RPM flavors and Arch too, well enough to be useful.

Sorry for this bit of a rant.  Oldfred knows much more about dual boot issues than I - 1000x more.  I haven't dual booted in over a decade.  I much prefer running MS-Windows under a virtual machine, as needed.  I hear people still using Windows complain that there was a Windows update that broke booting Linux. With virtual machines, that cannot happen.

---

### Post by ActionParsnip on 2022-08-13
The UUID is a disk identifier. Nothing to do with Nvidia drivers. If you boot to Ubuntu live CD / USB then you can run:
```

sudo blkid

```
You can see the ID of the file systems. You can then mount the internal drive and edit the fstab file and make sure that the ID of the root file system or whichever it is, is correct. You can then reboot and the OS should boot.

---

### Post by yancek on 2022-08-13
Also, booting the Ubuntu live USB you can check the grub.cfg file on the installed Ubuntu and compare the UUID on the Ubuntu menuentry to the one you see with the error.  If they are different, you have found your problem.

---

### Post by tea for one on 2022-08-13
> **anael03100 said:**
>  I'm very new to linux :).
As you are new to Linux and/or Ubuntu, how did you end up with 3 Linux partitions?

[COLOR="#0000FF"]Line 143[/COLOR] - nvme0n1p6 1588248576 1754263551  166014976  79.2G Linux filesystem
[COLOR="#0000FF"]Line 144[/COLOR] - nvme0n1p7 1754263552 1969106943  214843392 102.4G Linux filesystem
[COLOR="#0000FF"]Line 145[/COLOR] - nvme0n1p8 1969106944 1997848575   28741632  13.7G Linux swap

Particularly, the swap partition, where the default is a swap file?
Did you follow an internet guide or some other advice?

---

### Post by anael03100 on 2022-08-14
> **ActionParsnip said:**
> The UUID is a disk identifier. Nothing to do with Nvidia drivers. If you boot to Ubuntu live CD / USB then you can run:
```

sudo blkid

```
You can see the ID of the file systems. You can then mount the internal drive and edit the fstab file and make sure that the ID of the root file system or whichever it is, is correct. You can then reboot and the OS should boot.

So, I just did that, here's what the blkid command returned :
```

anael@Portable-Anael:~$ sudo blkid
[sudo] password for anael:
/dev/nvme0n1p8: UUID="6f4e1c1d-6a1e-435e-8717-6c8c9545e008" TYPE="swap" PARTUUID="08fbf99f-95ed-483c-bfb4-07792baa3b62"
/dev/nvme0n1p6: UUID="1ed98b7b-b11f-423b-928e-3522aefd4f87" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="9db27efc-c718-4c60-8727-1d42a4cc659e"
/dev/loop1: TYPE="squashfs"
/dev/nvme0n1p7: UUID="d0afda96-8482-4119-892e-fa32413b1560" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="65aca89c-e9a5-4d2e-80ae-1d976ff2f9f7"
/dev/nvme0n1p5: LABEL="MYASUS" UUID="165E-E47B" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="2811661e-ff12-4111-bb28-007ba0825db2"
/dev/nvme0n1p3: LABEL="OS" BLOCK_SIZE="512" UUID="265E9A035E99CBC5" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="3b41a967-16d1-467b-9bba-a8acde18f261"
/dev/nvme0n1p1: LABEL_FATBOOT="SYSTEM" LABEL="SYSTEM" UUID="4098-34CB" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="94d3eaed-624e-4779-bff7-8afd76cefc26"
/dev/nvme0n1p4: LABEL="RECOVERY" BLOCK_SIZE="512" UUID="B872DF2F72DEF15C" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="0a84037a-8c79-42b9-af37-408201aec90b"
/dev/nvme0n1p2: PARTLABEL="Microsoft reserved partition" PARTUUID="a0dcaa3f-59ad-4ab1-b29e-24882cc20786"
/dev/loop8: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
anael@Portable-Anael:~$

```
So then I went to check the fstab file, here it is :
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p6 during installation
UUID=1ed98b7b-b11f-423b-928e-3522aefd4f87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=4098-34CB  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p7 during installation
UUID=d0afda96-8482-4119-892e-fa32413b1560 /home           ext4    defaults        0       2
# swap was on /dev/nvme0n1p8 during installation
UUID=6f4e1c1d-6a1e-435e-8717-6c8c9545e008 none            swap    sw              0       0

```
I also checked the grub config file and the UUID seems to be the right one ( You'll find it here : [https://pastebin.com/RgwDziqE](https://pastebin.com/RgwDziqE) )
So, if I'm correct, everything checks out so UUID shouldn't be a problem :-k
> **yancek said:**
> 
Also, booting the Ubuntu live USB you can check the grub.cfg file on the installed Ubuntu and compare the UUID on the Ubuntu menuentry to the one you see with the error. If they are different, you have found your problem.

I also checked that, the UUID causing problems is 1ed98b7b-b11f-423b-928e-3522aefd4f87, and it's the same one as in the fstab file and blkid, so I don't really understand what's going on
> **tea for one said:**
> 
As you are new to Linux and/or Ubuntu, how did you end up with 3 Linux partitions?

I just followed a tutorial on how to install unbuntu alongside windows

---

### Post by tea for one on 2022-08-14
From post no.3, you mentioned > I also managed to start Ubuntu by going in the advanced boot settings for Ubuntu in GRUB and selecting the second version 
Are you still able to boot OK with this option?
Can you show the output from:-```
ls /boot | grep vmlinuz-
```

---

### Post by anael03100 on 2022-08-14
Yep, that's what i've been using for now, the command returns :
```

anael@Portable-Anael:~$ ls /boot | grep vmlinuz-
vmlinuz-5.15.0-25-generic
vmlinuz-5.15.0-46-generic

```

---

### Post by tea for one on 2022-08-14
Therefore, can we safely assume that:-
vmlinuz-5.15.0-25-generic - boots and works fine with Nvidia?
vmlinuz-5.15.0-46-generic - does not boot at all?

---

### Post by anael03100 on 2022-08-14
Yep, 25 works fine, 46 won't boot

---

### Post by TheFu on 2022-08-14
> **anael03100 said:**
> Yep, 25 works fine, 46 won't boot

After installing a new kernel, please also, reinstall the same nvidia driver, so it can be linked into the newer kernel.  I've had to do this when dkms isn't working correctly.

---

### Post by anael03100 on 2022-08-14
Well I didn't install the 26 kernel it was installed automatically at the same time as the 46 one so I'm not really sure what you want me to do

---

### Post by TheFu on 2022-08-15
> **anael03100 said:**
> Well I didn't install the 26 kernel it was installed automatically at the same time as the 46 one so I'm not really sure what you want me to do

Whenever a new kernel GETS installed, if there are nvidia driver issues, reinstall the drivers.  Whether you install a kernel or it is automatically installed due to dependencies, doesn't matter.

---

### Post by anael03100 on 2022-08-15
I see, well I could try that, how do I do that ?

---

### Post by TheFu on 2022-08-15
> **anael03100 said:**
> I see, well I could try that, how do I do that ?

Find the installed nvidia packages, then ask the package manager to reinstall them.  Someone else will need to explain how to do that with a GUI. I don't know. From a shell, I'd run 
$ dpkg -l 'nvidia*'
pick out the main driver package from the returned list, then 
$ sudo apt install --reinstall {the-name-of-the-nvidia-driver-package}

---

### Post by anael03100 on 2022-08-16
So I did that and reinstalled all the nvidia packages, but the problem is still the same :-k

---

### Post by TheFu on 2022-08-16
> **anael03100 said:**
> So I did that and reinstalled all the nvidia packages, but the problem is still the same :-k

It was just what I'd been using for about 2 yrs when I'd seen similar issues. Always worked here.
Can you show the exact commands, please?  Sometimes things are lost in translation and things I forgot to say will be seen by others.

But this may not be a fix either.  Just something more to try.

---

### Post by anael03100 on 2022-08-17
So since $ didn't work for me, I assumed it meant sudo and used that instead,here's the list :
```

anael@Portable-Anael:~$ sudo dpkg -l 'nvidia*' 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                    Architecture Description
+++-=========================-==========================-============-===============================================
un  nvidia-384                <none>                     <none>       (no description available)
un  nvidia-390                <none>                     <none>       (no description available)
un  nvidia-common             <none>                     <none>       (no description available)
un  nvidia-compute-utils      <none>                     <none>       (no description available)
ii  nvidia-compute-utils-515  515.65.01-0ubuntu0.22.04.1 amd64        NVIDIA compute utilities
un  nvidia-dkms-515           <none>                     <none>       (no description available)
ii  nvidia-driver-515         515.65.01-0ubuntu0.22.04.1 amd64        NVIDIA driver metapackage
un  nvidia-driver-binary      <none>                     <none>       (no description available)
un  nvidia-egl-wayland-common <none>                     <none>       (no description available)
un  nvidia-kernel-common      <none>                     <none>       (no description available)
un  nvidia-kernel-common-510  <none>                     <none>       (no description available)
ii  nvidia-kernel-common-515  515.65.01-0ubuntu0.22.04.1 amd64        Shared files used with the kernel module
un  nvidia-kernel-source      <none>                     <none>       (no description available)
ii  nvidia-kernel-source-515  515.65.01-0ubuntu0.22.04.1 amd64        NVIDIA kernel source package
un  nvidia-libopencl1-dev     <none>                     <none>       (no description available)
un  nvidia-opencl-icd         <none>                     <none>       (no description available)
un  nvidia-persistenced       <none>                     <none>       (no description available)
un  nvidia-prebuilt-kernel    <none>                     <none>       (no description available)
ii  nvidia-prime              0.8.17.1                   all          Tools to enable NVIDIA's Prime
ii  nvidia-settings           510.47.03-0ubuntu1         amd64        Tool for configuring the NVIDIA graphics driver
un  nvidia-settings-binary    <none>                     <none>       (no description available)
un  nvidia-smi                <none>                     <none>       (no description available)
un  nvidia-utils              <none>                     <none>       (no description available)
ii  nvidia-utils-515          515.65.01-0ubuntu0.22.04.1 amd64        NVIDIA driver support binaries
lines 1-29/29 (END)

```
So then I reinstalled all the packages :

```

anael@Portable-Anael:~$ sudo apt install --reinstall nvidia-compute-utils-515
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
   glib-networking:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386  libaa1:i386 libavc1394-0:i386 libcaca0:i386 libcairo-gobject2:i386  libcapi20-3:i386 libdv4:i386 libfaudio0:i386
   libgdk-pixbuf-2.0-0:i386 libgsm1:i386  libgstreamer-plugins-good1.0-0:i386 libgudev-1.0-0:i386  libiec61883-0:i386 libmp3lame0:i386 libmpg123-0:i386 libproxy1v5:i386  libraw1394-11:i386 libshout3:i386
  libslang2:i386 libsoup2.4-1:i386  libspeex1:i386 libstb0:i386 libtag1v5:i386 libtag1v5-vanilla:i386  libtwolame0:i386 libvkd3d1:i386 libvpx7:i386 libwavpack1:i386 libwine  libwine:i386 libxdamage1:i386
  libxslt1.1:i386 libxv1:i386 wine32:i386 wine64
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 239 not upgraded.
Need to get 0 B/114 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 176453 files and directories currently installed.)
Preparing to unpack .../nvidia-compute-utils-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-compute-utils-515 (515.65.01-0ubuntu0.22.04.1) over (515.65.01-0ubuntu0.22.04.1) ...
Setting up nvidia-compute-utils-515 (515.65.01-0ubuntu0.22.04.1) ...
Processing triggers for man-db (2.10.2-1) ...
anael@Portable-Anael:~$ sudo apt install --reinstall nvidia-driver-515
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
   glib-networking:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386  libaa1:i386 libavc1394-0:i386 libcaca0:i386 libcairo-gobject2:i386  libcapi20-3:i386 libdv4:i386 libfaudio0:i386
   libgdk-pixbuf-2.0-0:i386 libgsm1:i386  libgstreamer-plugins-good1.0-0:i386 libgudev-1.0-0:i386  libiec61883-0:i386 libmp3lame0:i386 libmpg123-0:i386 libproxy1v5:i386  libraw1394-11:i386 libshout3:i386
  libslang2:i386 libsoup2.4-1:i386  libspeex1:i386 libstb0:i386 libtag1v5:i386 libtag1v5-vanilla:i386  libtwolame0:i386 libvkd3d1:i386 libvpx7:i386 libwavpack1:i386 libwine  libwine:i386 libxdamage1:i386
  libxslt1.1:i386 libxv1:i386 wine32:i386 wine64
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 239 not upgraded.
Need to get 0 B/467 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 176453 files and directories currently installed.)
Preparing to unpack .../nvidia-driver-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-driver-515 (515.65.01-0ubuntu0.22.04.1) over (515.65.01-0ubuntu0.22.04.1) ...
Setting up nvidia-driver-515 (515.65.01-0ubuntu0.22.04.1) ...
anael@Portable-Anael:~$ sudo apt install --reinstall nvidia-kernel-common-515
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
   glib-networking:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386  libaa1:i386 libavc1394-0:i386 libcaca0:i386 libcairo-gobject2:i386  libcapi20-3:i386 libdv4:i386 libfaudio0:i386
   libgdk-pixbuf-2.0-0:i386 libgsm1:i386  libgstreamer-plugins-good1.0-0:i386 libgudev-1.0-0:i386  libiec61883-0:i386 libmp3lame0:i386 libmpg123-0:i386 libproxy1v5:i386  libraw1394-11:i386 libshout3:i386
  libslang2:i386 libsoup2.4-1:i386  libspeex1:i386 libstb0:i386 libtag1v5:i386 libtag1v5-vanilla:i386  libtwolame0:i386 libvkd3d1:i386 libvpx7:i386 libwavpack1:i386 libwine  libwine:i386 libxdamage1:i386
  libxslt1.1:i386 libxv1:i386 wine32:i386 wine64
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 239 not upgraded.
Need to get 0 B/25,2 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 176453 files and directories currently installed.)
Preparing to unpack .../nvidia-kernel-common-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-kernel-common-515 (515.65.01-0ubuntu0.22.04.1) over (515.65.01-0ubuntu0.22.04.1) ...
Setting up nvidia-kernel-common-515 (515.65.01-0ubuntu0.22.04.1) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-5.15.0-25-generic
I: The initramfs will attempt to resume from /dev/nvme0n1p8
I: (UUID=6f4e1c1d-6a1e-435e-8717-6c8c9545e008)
I: Set the RESUME variable to override this.
Processing triggers for initramfs-tools (0.140ubuntu13) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-46-generic
I: The initramfs will attempt to resume from /dev/nvme0n1p8
I: (UUID=6f4e1c1d-6a1e-435e-8717-6c8c9545e008)
I: Set the RESUME variable to override this.
anael@Portable-Anael:~$ sudo apt install --reinstall nvidia-kernel-source-515
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
   glib-networking:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386  libaa1:i386 libavc1394-0:i386 libcaca0:i386 libcairo-gobject2:i386  libcapi20-3:i386 libdv4:i386 libfaudio0:i386
   libgdk-pixbuf-2.0-0:i386 libgsm1:i386  libgstreamer-plugins-good1.0-0:i386 libgudev-1.0-0:i386  libiec61883-0:i386 libmp3lame0:i386 libmpg123-0:i386 libproxy1v5:i386  libraw1394-11:i386 libshout3:i386
  libslang2:i386 libsoup2.4-1:i386  libspeex1:i386 libstb0:i386 libtag1v5:i386 libtag1v5-vanilla:i386  libtwolame0:i386 libvkd3d1:i386 libvpx7:i386 libwavpack1:i386 libwine  libwine:i386 libxdamage1:i386
  libxslt1.1:i386 libxv1:i386 wine32:i386 wine64
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 239 not upgraded.
Need to get 0 B/31,3 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 176453 files and directories currently installed.)
Preparing to unpack .../nvidia-kernel-source-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-kernel-source-515 (515.65.01-0ubuntu0.22.04.1) over (515.65.01-0ubuntu0.22.04.1) ...
Setting up nvidia-kernel-source-515 (515.65.01-0ubuntu0.22.04.1) ...
anael@Portable-Anael:~$ sudo apt install --reinstall nvidia-settings
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
   glib-networking:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386  libaa1:i386 libavc1394-0:i386 libcaca0:i386 libcairo-gobject2:i386  libcapi20-3:i386 libdv4:i386 libfaudio0:i386
   libgdk-pixbuf-2.0-0:i386 libgsm1:i386  libgstreamer-plugins-good1.0-0:i386 libgudev-1.0-0:i386  libiec61883-0:i386 libmp3lame0:i386 libmpg123-0:i386 libproxy1v5:i386  libraw1394-11:i386 libshout3:i386
  libslang2:i386 libsoup2.4-1:i386  libspeex1:i386 libstb0:i386 libtag1v5:i386 libtag1v5-vanilla:i386  libtwolame0:i386 libvkd3d1:i386 libvpx7:i386 libwavpack1:i386 libwine  libwine:i386 libxdamage1:i386
  libxslt1.1:i386 libxv1:i386 wine32:i386 wine64
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 239 not upgraded.
Need to get 0 B/960 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 176453 files and directories currently installed.)
Preparing to unpack .../nvidia-settings_510.47.03-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (510.47.03-0ubuntu1) over (510.47.03-0ubuntu1) ...
Setting up nvidia-settings (510.47.03-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libc-bin (2.35-0ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
anael@Portable-Anael:~$ sudo apt install --reinstall nvidia-utils-515
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
   glib-networking:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386  libaa1:i386 libavc1394-0:i386 libcaca0:i386 libcairo-gobject2:i386  libcapi20-3:i386 libdv4:i386 libfaudio0:i386
   libgdk-pixbuf-2.0-0:i386 libgsm1:i386  libgstreamer-plugins-good1.0-0:i386 libgudev-1.0-0:i386  libiec61883-0:i386 libmp3lame0:i386 libmpg123-0:i386 libproxy1v5:i386  libraw1394-11:i386 libshout3:i386
  libslang2:i386 libsoup2.4-1:i386  libspeex1:i386 libstb0:i386 libtag1v5:i386 libtag1v5-vanilla:i386  libtwolame0:i386 libvkd3d1:i386 libvpx7:i386 libwavpack1:i386 libwine  libwine:i386 libxdamage1:i386
  libxslt1.1:i386 libxv1:i386 wine32:i386 wine64
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 239 not upgraded.
Need to get 0 B/366 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 176453 files and directories currently installed.)
Preparing to unpack .../nvidia-utils-515_515.65.01-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-utils-515 (515.65.01-0ubuntu0.22.04.1) over (515.65.01-0ubuntu0.22.04.1) ...
Setting up nvidia-utils-515 (515.65.01-0ubuntu0.22.04.1) ...
Processing triggers for man-db (2.10.2-1) ...

```
And that's all

---

### Post by TheFu on 2022-08-17
There are some commonly used "hints" by all Unix people to convey added information, like if a regular userid should be used or the root userid should be used.
```
$
```
means regular user
```
# 
```
means root user.  Basic knowledge, printed in every Unix/Linux book.  Since Ubuntu doesn't really use the root account directly, people posting commands to be typed would use '$' at the beginning of the line.  Lines without that are example output from the command.  Useful, right?

When using apt or apt-get to install or reinstall stuff, multiple packages can be listed concurrently.  The "compute" stuff isn't needed for graphics. It is to run 'compute' calculations specifically designed for a heavy multiple pipelining ... bitcoin is the most used today, but lots of people in science use GPUs to crunch numbers without outputting anything to a monitor. That's "compute" work.

The list I'd reinstall would have *515*, "driver" or "kernel" in the package name.

```
$ sudo apt install --reinstall  nvidia-driver-515 nvidia-kernel-common-515  nvidia-dkms-515
```
You probably got those reinstalled fine. If a reboot didn't fix it, then I'd move on to only be concerned with the UUID stuff and ignore nvidia, but if you like, you could remove --purge all the nvidia stuff and use the nouveau  drivers while troubleshooting that. It would remove that aspect of the problem from being possible, though the nouveau drivers are less capable and slower, they are fine for basic use.


I did manually check the blkid and fstab stuff. Seems fine to me as well, but I don't boot with UEFI most of my systems.  The single laptop that does, isn't powered on, so I can't easily check the /boot area or grub.  Have you tried the UEFI equivalent to doing a grub-install and update-grub?
I'm also assuming that all the Linux file systems have been fsck'd and reported clean?  Normally, if 1 kernel boots, but another doesn't, it is one of these issues:
a) ran out of space for the /boot/ partition - I get hit with this a few times a year on my older systems with 200MB /boot/ partitions.  It is common for installs not to have a separate /boot/, but I'm old school. I don't see a /boot/ in your fstab, so doubtful this is the issue.
b) kernel bug impacted by hardware in the system.  Sometimes a kernel won't like an NVMe storage device.  The attempted fix is to update the BIOS for the motherboard and for the NVMe storage. 5% chance this is the issue.
c) corrupted EFI file system. I've never seen this, but failing storage can fail in selected storage blocks that don't impact many other things.

The other things I can think of would cause problems for all Linux kernels, not just 1.

You could attempt to copy the EFI storage to an external flash drive and use it to boot.  I wouldn't, but it could be possible.  We are at the point of simplify and test, simplify more and test again. Keep doing that until the fault is discovered.

I don't dual boot either.  Haven't since around 2006 when I switched to running alternate OSes inside virtual machines.  Then only 1 OS is controlling the boot process and they don't have conflicts. Not everyone is willing to do this for some reasons. There are good reasons to want to boot an OS directly on hardware, I just don't have any of those anymore.

---

### Post by anael03100 on 2022-08-18
Oooh okay thanks for the info !

So It's not a space problem I just checked, I don't have any NVMe storage drives so it's not that either so maybe it's the last option, I'm not really sure of what to do then, I could try your idea , how do I proceed ?

---

### Post by oldfred on 2022-08-18
Is Boot-Repair report still the  same? It looked normal.
You could try the advanced mode and full reinstall of grub & install of latest kernel, just to reset ever thing.

Screens you see in Boot-Repair's advanced mode. 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Commands you can run if booted.
[https://ubuntuforums.org/showthread.php?t=2478104&p=14108368#post14108368](https://ubuntuforums.org/showthread.php?t=2478104&p=14108368#post14108368)


You may also need:
sudo update-initramfs -u -k

---

### Post by TheFu on 2022-08-18
> **anael03100 said:**
> Oooh okay thanks for the info !

So It's not a space problem I just checked, I don't have any NVMe storage drives so it's not that either so maybe it's the last option, I'm not really sure of what to do then, I could try your idea , how do I proceed ?

It appears from the fstab comments that you DO have at least 1 NVMe SSD drive.  If you didn't replace it, then it is still being used.

SMART data is something that every storage device should have the capability to show.  This is "drive problems" data, as far as the the drive can tell.  HDDs, SSDs should all have it and some USB flash drives too.  The disk controller is important. Some cheap USB controllers don't support it - USB-storage isn't the full commands that SATA, SCSI, IDE PATA support.  

Sometimes the BIOS needs an "Enable SMART" toggle. This is on the motherboard, those BIOS settings.  There are a number of ways to see the SMART data, but they all begin by performing a test, waiting for the test to complete, then asking for a report.  A "short" test usually takes 5seconds to 5 minutes, depending on the type of storage.  A "long" test on HDDs can take hours.  As part of my drive maintenance process, I run weekly "short" tests and monthly "long tests". The results are saved to files, since SMART data is most helpful by comparing the differences over time.  The test results are relatively small, so I keep 12 months worth for every storage device.  smartctl is the tool I use, since it is easy to automate, unlike the GUI stuff and most of my systems don't have GUIs at all.  Search these forums for exact smartctl command examples. For non-standard controllers, a specific device may need to be manually told to the smartctl command, for it to work.  I've only needed this with old Maxell controllers and some external USB storage from WD. Yuck.

What's all this about?  There isn't an easy way to validate data on a FAT file system, so looking at the SMART data is about all we have.

---

### Post by anael03100 on 2022-08-24
Well this didn't work either sadly, at this point since I need to move forward and have nothing to lose I'm just gonna do a clean install of ubuntu, thanks for all the help, this has taught me lot about linux =)

---


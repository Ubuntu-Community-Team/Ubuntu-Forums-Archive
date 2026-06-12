---
title: "How to set up Xen 3.0 from binaries in Ubuntu 6.06"
date: 2006-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by cyberloon on 2006-06-13
This particular way of installing and configuring Xen is just the path of least resistance for me. There are
many other possible ways of configuring the system.

1. Install a clean base server system.
Setup Ubuntu like you normally would. I have created 3 partitions on hda, but you can do it any way you like.
Just keep your differences in mind when you edit the config files.

hda1 is swap
hda2 is 2 GB and mounted as /
hda3 is the rest of the disk and mounted as /xen-images

2. Update the system and install Xen
2.1. Install Xen and configure it
Open a root shell so you don't have to type sudo for every command.
```
sudo -s
```

Update the system and install nessecary packages.
```
apt-get update 
apt-get upgrade
apt-get install iproute python python-twisted bridge-utils debootstrap
```

Download and extract the Xen 3.0 tarball from [http://www.xensource.com/xen/downloads/](http://www.xensource.com/xen/downloads/)
```
tar xvf xen-3.0.1-install-x86_32.tgz
cd xen-3.0.1-install
./install.sh
```

Check for error messages - it should say OK to all.
Next we create modules.dep and map files for the new kernel. (see /lib/modules for the correct kernel version)
```
/sbin/depmod -a 2.6.16-xen
```

Edit /etc/mkinitramfs/modules and append the following line:
```
loop max_loop=64
```

If you run out of loop devices later just increase max_loop and rebuild the initrd.
Create an initrd image. Use the same version number as before.
```
cd /boot
mkinitramfs -o initrd.img-2.6.16-xen 2.6.16-xen
```

Edit /boot/grub/menu.lst placing the following lines **before** the Automagic section
```
title Xen 3.0 / XenLinux 2.6 
kernel /boot/xen-3.gz 
module /boot/vmlinuz-2.6-xen root=/dev/hda2 ro
module /boot/initrd.img-2.6.16-xen
```

Make Xen start up and autostart selected guests when the system starts up. xend must start before,
and must be stopped after xendomains.
```
update-rc.d xend start 30 2 3 4 5 . stop 31 0 1 6 .
update-rc.d xendomains start 31 2 3 4 5 . stop 30 0 1 6 .
```

Disable Thread-Local Storage (remember to check this after every update)
```
mv /lib/tls /lib/tls.disabled
```

2.2. The following workarounds may not be required later, but I had to do them.
Rename xen-backend.rules
```
mv /etc/udev/rules.d/xen-backend.rules /etc/udev/rules.d/92-xen-backend.rules
```

To make sure that /var/run/xenstored and /var/run/xend exist.
Edit /etc/init.d/xend and insert the following lines after the check for /proc/xen/capabilities
```
if [ ! -d /var/run/xend ] ; then
    mkdir -p /var/run/xend
fi

if [ ! -d /var/run/xenstored ] ; then
    mkdir -p /var/run/xenstored
fi
```

Edit /etc/init.d/xendomains and change the LOCKFILE line to read
```
LOCKFILE=/var/lock/xendomains
```

2.3. All done for this part so reboot.
When the system is back up try the following command to verify that everything is ok.
```
xm list
```

You should see something similar to this:
```
Name                              ID Mem(MiB) VCPUs State  Time(s)
Domain-0                           0      463     1 r-----    42.3
```

3. Configuring the guest domains
3.1. Create disk images and bootstrap them
Create a mountpoint for the images.
```
mkdir /xen-images/mnt
```

Create a 1 GB image file and 500 MB swap file, for larger images increase count.
```
dd if=/dev/zero of=/xen-images/guest_base.img bs=1024k count=1000<br/>
dd if=/dev/zero of=/xen-images/guest_base-swap.img bs=1024k count=500
```

Change permissions for the image files. No one should have access to your Domain-0 computer since that
would compromise security for all of the guest domains, but this is a good idea anyway and doesn't affect Xen.
```
chmod 640 /xen-images/guest_base*
```

Format guest_base.img as ext3 and then format guest_base-swap.img as swap.
When it says "/xen-images/guest_base.img is not a block special device." answer yes to proceed anyway.
```
mkfs.ext3 /xen-images/guest_base.img
mkswap /xen-images/guest_base-swap.img
```

Mount the guest image and bootstrap it.
You should replace [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) with a mirror that is closer to you.
```
mount -o loop /xen-images/guest_base.img /xen-images/mnt<br/>
debootstrap --arch i386 dapper /xen-images/mnt http://archive.ubuntu.com/ubuntu/
```

Copy your /etc/apt/sources.list to the new image.
```
cp /etc/apt/sources.list /xen-images/mnt/etc/apt/
```

Copy the kernel modules.
```
cp -dpR /lib/modules/2.6.16-xen /xen-images/mnt/lib/modules/
```

Disable Thread-Local Storage.
```
mv /xen-images/mnt/lib/tls /xen-images/mnt/lib/tls.disabled
```

Configure networking for the guest /xen-images/mnt/etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# Uncomment this and configure after the system has booted for the first time
#auto eth0
#iface eth0 inet static
#        address 192.168.0.101
#        netmask 255.255.255.0
#        broadcast 192.168.0.255
#        gateway 192.168.0.1
#        dns-nameservers 192.168.0.1
```

Create /xen-images/mnt/etc/hosts and make it look like this.
```
127.0.0.1       localhost localhost.localdomain
127.0.0.1       guest

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Create /xen-images/mnt/etc/hostname
```
echo guest > /xen-images/mnt/etc/hostname
```

Edit /xen-images/mnt/etc/fstab so it looks like this.
```
proc            /proc       proc    defaults    0 0
/dev/hda1       /           ext3    defaults,errors=remount-ro    0 1
/dev/hda2       none        swap    sw          0 0
```

Unmount the image.
```
umount /xen-images/mnt
```

If you get this warning "umount: /xen-images/mnt: device is busy" don't worry, it's not important.

3.2. Boot up the base image to finalize the configuration
Create a config file for the guest /etc/xen/baseimage
```
#  -*- mode: python; -*-
kernel = "/boot/vmlinuz-2.6.16-xen"
ramdisk = "/boot/initrd.img-2.6.16-xen"
memory = 128
name = "baseimage"
vif = ['bridge=xenbr0']
disk = ['file:/xen-images/guest_base.img,hda1,w','file:/xen-images/guest_base-swap.img,hda2,w']
ip = "192.168.0.101"
netmask = "255.255.255.0"
gateway = "192.168.0.1"
hostname = "baseimage"
root = "/dev/hda1 ro"
extra = "4"
```

Start the guest.
```
xm create baseimage -c
```

Login as root and set the root password.

Enable shadow passwords.
```
shadowconfig on
```

Create a backup of /etc/network/interfaces
```
cp /etc/network/interfaces /etc/network/interfaces.bak
```

Edit /etc/network/interfaces and put in correct values so you can access the Internet.

Start networking.
```
ifup -a
```

Install packages (add ubuntu-desktop and more if you want).
```
apt-get update
apt-get install ubuntu-base configure-debian openssh-server
```

Disable Thread-Local Storage if it has been updated.
```
mv /lib/tls /lib/tls.disabled
```

Configure the system any way you like, I recommend that you try every menu item.
You should do utils->console-data before utils->console-common.
```
configure-debian
```

Make /etc/sudoers writable.
```
chmod 660 /etc/sudoers
```

Add the new user you created to /etc/sudoers

Fix permissions for /etc/sudoers
```
chmod 440 /etc/sudoers
```

Stop networking.
```
ifdown -a
```

Replace /etc/network/interfaces with the backup copy.
```
mv /etc/network/interfaces.bak /etc/network/interfaces
```

You are now done setting up the base image so shut it down.

4. Creating your first guest domain
Make a copy of the base guest images.
```
cp /xen-images/guest_base.img /xen-images/guestdom1.img
cp /xen-images/guest_base-swap.img /xen-images/guestdom1-swap.img
```

Rename /etc/xen/baseimage
```
mv /etc/xen/baseimage /etc/xen/guestdom1
```

Edit /etc/xen/guestdom1 and change name, disk and hostname to the following values.
```
name = "guestdom1"
disk = ['file:/xen-images/guestdom1.img,hda1,w','file:/xen-images/guestdom1-swap.img,hda2,w']
hostname = "guestdom1"
```

You will want to change the following files for each new guest you create.
[LIST]
[*]/etc/hostname
[*]/etc/hosts
[*]/etc/network/interfaces
[/LIST]

To make the guest start up automatically and make Domain 0 wait for it before shutting down.
```
ln -s /etc/xen/guestdom1 /etc/xen/auto/
```

Or if you want to start and stop the guest manually.
```
xm create guestdom1
```

For further information check the [Xen Documentation]("http://www.cl.cam.ac.uk/Research/SRG/netos/xen/documentation.html")

References:
[http://www.howtoforge.com/perfect_xen_setup_debian_ubuntu](http://www.howtoforge.com/perfect_xen_setup_debian_ubuntu)
[https://wiki.ubuntu.com/XenOnUbuntuBinaryInstall](https://wiki.ubuntu.com/XenOnUbuntuBinaryInstall)
[http://www.ubuntuforums.org/showthread.php?t=178027](http://www.ubuntuforums.org/showthread.php?t=178027)

Other points of interest:
[https://wiki.ubuntu.com/XenVirtualMachine/XenOnUbuntuDapper](https://wiki.ubuntu.com/XenVirtualMachine/XenOnUbuntuDapper)

---

### Post by WetWilly on 2006-06-14
very well explained and comprehensive guide!!

THANKS ALOT :KS

---

### Post by Alethos on 2006-06-17
Well, I tried your how to and at the point where you tell us to reboot, I did and I got the following error...

kernel /boot/xen-3.gz
Error 15: file not found

I'm at a loss. xen-3.gz is in the boot directory.

---

### Post by cyberloon on 2006-06-17
Hmmm. Is /boot on a separate partition?

---

### Post by Alethos on 2006-06-17
Yes I seperated out /boot from / ... habit I guess. Should I rebuild with just 1 partition (for /boot + /). It's no big deal...I don't have any data i need to save or anything.

---

### Post by cyberloon on 2006-06-17
Try to put /boot and / on the same partition. I had this trouble once and that solved it for me.

---

### Post by Alethos on 2006-06-17
Ok, i'll rebuild and give it another shot...thanks.

---

### Post by prflfoawhgu on 2006-06-17
I get to the reboot, but it drops me to a shell. It seems to not support sata drives on the ich7. The only solution I found was to use xen 2.07, which isn't a option for me.

---

### Post by cyberloon on 2006-06-18
You might want to have a look at [https://wiki.ubuntu.com/XenVirtualMachine/XenOnUbuntuDapper](https://wiki.ubuntu.com/XenVirtualMachine/XenOnUbuntuDapper) and compile your own kernel.

---

### Post by Alethos on 2006-06-18
I rebuilt partition scheme, reinstalled and followed your how to. Once again at the reboot point here is what I see:
```

Begin: Running /scripts/local-premount...
Done.
modprobe: FATAL: could not load /lib/modules/2.6.16-xen/modules.dep: no such file or directory

mount: mounting /dev/hda1 on /root failed: no such device
Begin: running /scripts/local-bottom...
Done.
Done.
Begin running /scripts/init-bottom...
mount: mounting /root/dev on /dev/static/dev failed: no such file or directory
Done.
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target filesystem doesn't have /sbin/init

Busybox v1.01..............................

/bin/sh: can't access tty; job control turned off
#
```

That's all the errors i could see on screen...where to go from here?

---

### Post by cyberloon on 2006-06-18
Did you do the /sbin/depmod -a 2.6.16-xen step?
What does /lib/modules contain?

---

### Post by Alethos on 2006-06-18
I believe I did.

/lib/modules contains
2.6.15-23-server

and that's it

---

### Post by cyberloon on 2006-06-19
The xen install script should have placed a 2.6.16-xen directory there. Try to start over.

---

### Post by Alethos on 2006-06-19
I tried it again last night at about midnight. Good news: I did not get the same error messages. Bad news: I still got some error messages. I'm stuck here at work but after I get home i'll copy down the error messages and post them here. Thanks.

[EDIT]
Got it working. To the reboot point at least. I'll try the rest of it tomorrow. What I finally did was partition my drive exactly like yours with the swap first then / on hda2 and x for the rest. Previously I had / on hda1 and swap on some other partition. I wonder why it would keep dorking up? In grub I always changed the root= to whatever my root was. Strange. Anyhow...like I said got it working and I'll try the rest tomorrow as it's late here.

Thanks for yer help and the how-to.

[EDIT]
How do I go about specifying where the xen images are stored? I've read through the steps several times and I'm not seeing it. I have a 200GB hd /dev/hdb1 that I'd like to use for the xen images instead of the rest of /dev/hda.

---

### Post by cyberloon on 2006-06-30
You specify the image files in the config file for the guest.
In my example I set it like this```
disk = ['file:/xen-images/guest_base.img,hda1,w','file:/xen-images/guest_base-swap.img,hda2,w']
```

You can just modify the path to suit your needs

---

### Post by sickdude on 2006-07-03
thnx loads for your great tutorial it worked like a charm for me.

i tryed to install xen on fedora core 5 and that was a lot harder then on ubuntu, with your help that is :)

anyway i created another problem. i want to install asterisk on 1 of my xen domains. but i have to compile asterisk, i had a little help from somebody else wich wasnt wrong. but i have to install kernel headers ($ apt-get install linux-headers-`uname -r`) but when i try this, it says no way dude.

this is when im compiling the zaptel drivers, is it maybe a option to complile the zaptel drivers on my xen server in stead of the xen host?

---

### Post by cyberloon on 2006-07-04
The latest kernel header package I can see for Ubuntu is 2.6.15 and Xen is compiled with 2.6.16

You should take a look at this page
[https://wiki.ubuntu.com/XenVirtualMachine/XenOnUbuntuDapper](https://wiki.ubuntu.com/XenVirtualMachine/XenOnUbuntuDapper)
I'm not sure if you really need to compile your own kernel, but it's probably a good idea.

I haven't done this myself, but it doesn't seem like it's too much trouble.

---

### Post by sal_veya on 2006-07-07
I followed the instructions, however I used the 64 bit version as I'm using Ubuntu AMD64. After booting the new kernel I can use my system, however after about three-four minutes the entire system hangs and reboots. If I use the dom0_memory parameter I believe the issue goes away. Does this parameter set the ammount of reserved memory for only dom0, or does it specify the ammount of total memory to be used for Xen. For example, if I set it to 600 meg out of my 1024 meg of ram, can I use the remaining 400 meg for the guest OS's?

Thanks,

Sal

---

### Post by herbr on 2006-07-09
The problem I bump into is "configure-debian". All goes well until I try to apt-get install configure-debian, then I find this package is not found!
I'm running 2.6.16-xen and it cannot find the package.

Any suggestions?

Regards, Herb

---

### Post by herbr on 2006-07-09
Never mind, I found that when I first installed Dapper Drake this source entry gave me a hard time so I commented it out.
I just uncommented it and noe I can install configure-debian

Regards, Herb

---

### Post by cyberloon on 2006-07-12
@sal_veya

The Xen documentation has the following to say:> mem=xxx
    Set the physical RAM address limit. Any RAM appearing beyond this physical address in the memory map will be ignored. This parameter may be specified with a B, K, M or G suffix, representing bytes, kilobytes, megabytes and gigabytes respectively. The default unit, if no suffix is specified, is kilobytes. 
dom0_mem=xxx
    Set the amount of memory to be allocated to domain0. In Xen 3.x the parameter may be specified with a B, K, M or G suffix, representing bytes, kilobytes, megabytes and gigabytes respectively; if no suffix is specified, the parameter defaults to kilobytes. In previous versions of Xen, suffixes were not supported and the value is always interpreted as kilobytes.

So I think that dom0_mem only sets how much memory is available to domain 0.

---

### Post by sal_veya on 2006-07-17
Regardless, I still had a lot of crashing issues on Xen 3.0, so I switched over to VMware server, and it's running great. Maybe I'll try back with Xen in a bit to see if I can get it working, if not I'll wait until Eft comes out.

---

### Post by shellster on 2006-07-26
How do I add more domains?
Can I use xen tools I keep getting an initrd kernel panic even though the path to the initrd image is right.
Also, although everything works I always get a bunch of device mapper errors when the system starts up.  Has anyone else experienced this?

---

### Post by k1773r37f on 2007-12-12
I have a fuctional Dapper Drake xen guest running.  However,  several times in the instrctions, we are told to 
```
# mv /lib/tls /lib/tls.disable
```

If I do that, the xm commands do not work.
```
root@enterprise:~# xm list
Traceback (most recent call last):
  File "/usr/sbin/xm", line 8, in ?
    from xen.xm import main
  File "/usr/lib/python/xen/xm/main.py", line 51, in ?
    from xen.util import security
  File "/usr/lib/python/xen/util/security.py", line 25, in ?
    from xen.lowlevel import acm
ImportError: libxenctrl.so.3.0: cannot handle TLS data
root@enterprise:~#

```
 What are the ramicifactions of tls libs in a xen environment.  If it is working for me, should I ignore it?

Thanx,
The Killer Elf.

---

### Post by k1773r37f on 2007-12-12
Nevermind. I found that I can leave tls in place on dom0 and disable it on the guests and everyone is happy.

Thanx,
The Killer Elf

---


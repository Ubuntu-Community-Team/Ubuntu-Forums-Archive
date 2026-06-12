---
title: "Help downgrading to Kernel 3.2 in 12.04.2 LTS"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by ryan4 on 2013-08-03
I have a problem that might be solved by downgrading to 3.2. I was following the instructions here:

[http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/](http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/)

but got stuck when running "sudo make menuconfig"

I tried to post all of the code but it was filled with frowning faces, so here is part:

a whole buch of "undefined reference to"s...
...
collect2: ld returned 1 exit status
make[1]: *** [scripts/kconfig/mconf] Error 1
make: *** [menuconfig] Error 2
ryan@ryan-X75A:/usr/src/linux-3.2$

any ideas?

---

### Post by ibjsb4 on 2013-08-03
The 3.2 kernel for 12o4 is in the repositories, no need to compile it.  Install synaptic package manager and choose your kernel.

[ATTACH=CONFIG]245037[/ATTACH]

To install synaptic in terminal:

```
sudo apt-get install synaptic
```

---

### Post by meilin on 2013-08-03
Why not using the Debs to make installation easy???

The kernal ppa contains the .deb packages for Kernel 3.2.xx: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Check your OS type first, 32-bit or 64-bit. Then download 3 packages: "linux-headers-*-generic.deb" "linux-headers-*all.deb" and "linux-image-*.deb"

Then use below command to install them:

<pre>cd ~/Downloads/</pre>
<pre>sudo dpkg -i PACKAGE_NAME1.deb PACKAGE_NAME2.deb PACKAGE_NAME3.deb</pre>

---

### Post by VMC on 2013-08-03
Using the debs is the way I went. From mainline, I downloaded the kernel and headers and *"sudo dpkg -i *deb*" from the folder it was in. It errored, stating something about missing wifi, so "*sudo apt-get install -*f" installed the needed files, and it was fixed.

---

### Post by ryan4 on 2013-08-03
> **VMC said:**
> Using the debs is the way I went. From mainline, I downloaded the kernel and headers and *"sudo dpkg -i *deb*" from the folder it was in. It errored, stating something about missing wifi, so "*sudo apt-get install -*f" installed the needed files, and it was fixed.

Here are my results:

ryan@ryan-X75A:~$ uname -r
3.5.0-38-generic
ryan@ryan-X75A:~$ cd Downloads
ryan@ryan-X75A:~/Downloads$ sudo dpkg -i *.deb
[sudo] password for ryan: 
Selecting previously unselected package linux-headers-3.2.50-030250-generic.
(Reading database ... 174254 files and directories currently installed.)
Unpacking linux-headers-3.2.50-030250-generic (from linux-headers-3.2.50-030250-generic_3.2.50-030250.201308021735_amd64.deb) ...
Preparing to replace linux-image-3.2.50-030250-generic 3.2.50-030250.201308021735 (using linux-image-3.2.50-030250-generic_3.2.50-030250.201308021735_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.2.50-030250-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.50-030250-generic /boot/vmlinuz-3.2.50-030250-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.50-030250-generic /boot/vmlinuz-3.2.50-030250-generic
dpkg: dependency problems prevent configuration of linux-headers-3.2.50-030250-generic:
 linux-headers-3.2.50-030250-generic depends on linux-headers-3.2.50-030250; however:
  Package linux-headers-3.2.50-030250 is not installed.
dpkg: error processing linux-headers-3.2.50-030250-generic (--install):
 dependency problems - leaving unconfigured
Setting up linux-image-3.2.50-030250-generic (3.2.50-030250.201308021735) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.50-030250.201308021735 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.50-030250.201308021735 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.50-030250-generic /boot/vmlinuz-3.2.50-030250-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.50-030250-generic /boot/vmlinuz-3.2.50-030250-generic
update-initramfs: Generating /boot/initrd.img-3.2.50-030250-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.50-030250-generic /boot/vmlinuz-3.2.50-030250-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.50-030250-generic /boot/vmlinuz-3.2.50-030250-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.50-030250-generic /boot/vmlinuz-3.2.50-030250-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-38-generic
Found initrd image: /boot/initrd.img-3.5.0-38-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found linux image: /boot/vmlinuz-3.2.50-030250-generic
Found initrd image: /boot/initrd.img-3.2.50-030250-generic
Found memtest86+ image: /boot/memtest86+.bin
Adding boot menu entry for EFI firmware configuration
done
Errors were encountered while processing:
 linux-headers-3.2.50-030250-generic
ryan@ryan-X75A:~/Downloads$

---

### Post by ryan4 on 2013-08-03
I am not sure if it was successful.

---

### Post by ryan4 on 2013-08-03
Is it possible to install 12.04 with the 3.2 kernel?

---

### Post by ryan4 on 2013-08-03
I tried installing synaptic, got:

ryan@ryan-X75A:~$ sudo apt-get install synaptic
[sudo] password for ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate
ryan@ryan-X75A:~$ 


This is a fresh install.

---

### Post by Vladlenin5000 on 2013-08-03
Are you sure you have all the required repos active? You may want to check that and ```
sudo apt-get update
``` before trying again.
You can also try installing it from the software center.

---

### Post by ryan4 on 2013-08-03
I tried installing synaptic, following the instructions here:

[http://askubuntu.com/questions/131979/how-to-install-synaptic-package-manager](http://askubuntu.com/questions/131979/how-to-install-synaptic-package-manager)

First two steps, no problem. Third step:

ryan@ryan-X75A:~$ sudo apt-get install synaptic
[sudo] password for ryan: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ryan@ryan-X75A:~$ 

??

---

### Post by ryan4 on 2013-08-03
Nevermind, it was some system update running that I was unaware of.

---

### Post by ryan4 on 2013-08-03
synaptic is installed but I cannot find the 3.2 kernel. I entered "linux kernel image" in the Quick filter, and the results are all 3.5 versions

---

### Post by ryan4 on 2013-08-03
I found them. There are a LOT of versions. Which one do I need??? Generic, virtual, pae?

---

### Post by ryan4 on 2013-08-03
I decided to go with the last generic version. Do I need to get rid of 3.5?

---

### Post by ryan4 on 2013-08-03
I rebooted and it is still running 3.5. What's the next step?

---

### Post by Vladlenin5000 on 2013-08-03
If you reported the problems that you think you're having due to the 3.5 kernel then *maybe* someone would already suggested some solution that would have avoided the trouble of downgrading and all the issues that should be expected. Your hardware benefits from a newer, not older, kernel.

---

### Post by ryan4 on 2013-08-03
I need to downgrade in order to get the wireless working, see here:
[http://ubuntuforums.org/showthread.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690)

I did manage to downgrade successfully and loaded 3.2 in grub, but now I have no wired connection, so I cannot set up wireless. I followed this to get wired working in 3.5:
[http://askubuntu.com/questions/237004/atheros-ar8161-ethernet-card-not-working-on-12-10-on-an-asus-n56vm](http://askubuntu.com/questions/237004/atheros-ar8161-ethernet-card-not-working-on-12-10-on-an-asus-n56vm)

And it worked perfectly with 3.5 (not no wireless, hence the downgrade)... but in 3.2 I run into problems when I execute "make", specifically I get:
.../lib/modules/3.2.0-51-generic/build:No such file or directory...
followed by Error 2...

So there is at least one more step to getting this all working. Any ideas?

---

### Post by ryan4 on 2013-08-04
Anyone?

---

### Post by kurt18947 on 2013-08-04
How big a hassle would it be to reinstall 12.04 original then lock the kernel?  My desktop didn't seem happy with 12.10/kernel 3.5.  It likes 12.04/3.2 and seems quite pleased with 13.04 & 13.10.  Have you tried live CD/liveUSB of 13.04 or 13.10?  I  have a generic RT5370 USB wifi adapter.  The speed & signal strength were pretty sorry in 12.10 & 13.04.  It seems much better in 13.10.

---

### Post by ryan4 on 2013-08-04
I solved the issue, [see my post here]("http://ubuntuforums.org/showthread.php?t=2165295").

Speed & signal strength seem fine to me. The only issue I am noticing is that the mouse pauses from time to time.

---


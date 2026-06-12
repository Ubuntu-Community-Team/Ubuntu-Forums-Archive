---
title: "New to Unbuntu, Can't install new software"
date: 2016-10-15
forum: New to Ubuntu
---

### Post by apol1 on 2016-10-15
Hi, I am very new to Ubuntu and I have lost my ability to install, and update anything on my computer. I would be eternally grateful for any help I can get and will follow your instructions without question. 

Heres a few errors from my terminal on what happens when I attempt to install new software...

Removing linux-image-extra-4.4.0-24-generic (4.4.0-24.43) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-24-generic: No such file or directory

Error! Your kernel headers for kernel 4.4.0-24-generic cannot be found.

Please install the linux-headers-4.4.0-24-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-24-generic cannot be found.

update-initramfs: Generating /boot/initrd.img-4.4.0-24-generic
WARNING: missing /lib/modules/4.4.0-24-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-24-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory

the errors repeat like this over and over, and please let me know if Im being unpleasant in anyway by mistake

your help is greatly appreciated

---

### Post by hmw2 on 2016-10-15
it appears as though you somehow deleted part of your kernel (the heart of the operating system)
i would backup all your important stuff and just reinstall ubuntu. then once you relog in run 'sudo apt-get update && sudo apt-get upgrade' and install all the new updates as well as the updated kernel. you shouldnt have issues after that. just make sure you dont delete stuff if you dont know what its for.

---

### Post by howefield on 2016-10-15
> **apol1 said:**
> Heres a few errors from my terminal on what happens when I attempt to install new software...

Please post the full output of the terminal, not just a few selected errors. It may help others to better help you.

---

### Post by RobGoss on 2016-10-15
What distribution of Ubuntu do you currently have installed? 

And is this a new installation if it is it might be a good idea to just do a fresh installation save you some time

You might be able to just install your kernels version I found this post with a few details that might help you: [http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

---

### Post by apol1 on 2016-10-16
I think your right I might just do a reinstall, Im having some trouble attempting this, I have an Ubuntu LTS 16.04 disk and a downloaded version of it (I think) 

I have my stuff backed up and ready to go, how should I proceed in a reinstall?

---

### Post by RobGoss on 2016-10-16
Before you do a reinstallation try choosing a diffefent kernel I have seen a lot of post with this same issue. Try holding down the **shift key** while your machine is booting this will also display the** Grub menu**, you should be able to choose a older kernel version, if you don't see a list of older kernel versions click on **advanced options **there should be a list for you to choose from

If all else fails them we can proceed to reinstall Ubuntu if needed

---

### Post by apol1 on 2016-10-17
Im afraid even the Grub Menu has bid farewell cruel world :/

I say we go for the re-install, this machine has several other concerning problems I simply don't have time to learn to fix at the moment.

Thx

Awaiting instructions

---

### Post by Bucky Ball on 2016-10-17
> **apol1 said:**
> I say we go for the re-install ...

Welcome. I agree. If this drive has been used for other things, boot to 'Try Ubuntu' from the install media, open Gparted, right click on and delete all partitions> go to Device> Create partition table. Once that's done, leave the disk blank, free, unallocated space and click the 'Install' icon on the desktop.

During the install don't tick 'Install third-party proprietary drivers' or 'Update during install'. Those can be dealt with later and can be problematic during install. You also don't need to be online to install and that might be a good idea too.

Do you need more info than that? Couple of things. From the kernel you're having issues with I am presuming you are using 16.04? Are you attempting to dual-boot with Windows? If so, that is a slightly different path with different pitfalls.

---

### Post by howefield on 2016-10-17
Hello apol1, I have removed you post with the failed image, try using the paperclip icon to attach your inage to the post rather than dragging it into the posting window.

---

### Post by apol1 on 2016-10-17
I did'nt Even Get that far, I got an error when I popped in the disk

Here is the error itself

                        An Error occurred  

 
 
 Error attaching disk image:
 CDBus.Error org.freedesktop.UDisks2.Error.Failed: Error Setting  
 up loop device /dev/loop0: Invailid argument (udisks-error-quark. 0)

---

### Post by RobGoss on 2016-10-17
I think the best thing you need to do is explain how you created your installation USB or DVD and how are you installing the live media. The information you provide the better we can help you

Also give us the spec details about your machine this is very important while trying to trouble shoot any machine 

Video card
RAM
Mother board

Computer brand

Thanks

---

### Post by apol1 on 2016-10-21
[FONT=Verdana ]Video Card: 4GB EVGA NVIDIA GeForce GTX970 GDDR5 video card
Ram: [/FONT]
**[FONT=Verdana ]DDR4 Memory[/FONT]**[FONT=Verdana ][/FONT]
   [FONT=Verdana ]32GB Crucial Ballistix DDR4-2400MHz (4 x 8GB), CAS 16 latency, low voltage

[/FONT]**[FONT=Verdana ]Motherboard[/FONT]**[FONT=Verdana ][/FONT]

   [FONT=Verdana ]Asus X99-A/USB 3.1 Intel X99 based chipset, ATX Motherboard :)[/FONT]

---

### Post by Bucky Ball on 2016-10-21
... and importantly, release and flavour of Ubuntu, please. If you include the release and flavour of Ubuntu you are using (along with other relevant hardware details) in your first post it will speed things up (i.e. how long it takes you to get support ;)).

Open a terminal and

```
sudo apt update
sudo apt full-upgrade
```

Please post any error messages you receive from either command between ```
 tags, please (see the green link in my signature at the bottom of this post). Also the output of this.

[code]lsb_release -a
```

---

### Post by apol1 on 2016-10-21
fantastic, :D I got two prompts outside of terminal to report problems, here they are


                        Sorry, a problem occurred while installing software.

 
 
 Package: grub-efi-amamd64 2.02~beta2-36ubuntu3.2

 
 
 Sorry, a problem occurred while installing software.

 
 
 Package: Linux-image-4.4.0-45-generic 4.4.0-45.66

TERMINAL OUTPUT

                        

 **```
** Errors were encountered while processing:

  grub-efi-amd64
  grub-efi-amd64-signed
  linux-image-4.4.0-45-generic
  linux-image-extra-4.4.0-45-generic
  linux-image-generic
  linux-generic
  linux-signed-image-4.4.0-45-generic
  linux-signed-image-generic
  linux-signed-generic
  linux-image-4.4.0-24-generic
  linux-image-4.4.0-28-generic
  linux-image-4.4.0-34-generic
  linux-image-extra-4.4.0-24-generic
  linux-image-extra-4.4.0-28-generic
  linux-image-extra-4.4.0-34-generic
  linux-signed-image-4.4.0-34-generic
 E: Sub-process /usr/bin/dpkg returned an error code (1)
 
 
 lsb_release -a
 No LSB modules are available.
 Distributor ID:    Ubuntu
 Description:    Ubuntu 16.04.1 LTS
 Release:    16.04
 Codename:    xenial**
```**
  
Im not sure what a flavor is, but I'll edit my main post once I find out, I'll also crack down on using code tags as well for clarity :)

---

### Post by Bucky Ball on 2016-10-21
[code] tags please, as requested.

---

### Post by apol1 on 2016-10-21
sure no problem :)

---

### Post by Bucky Ball on 2016-10-21
The problem in your first post seems to be with the old kernel, 4.4.0-24-generic which is well obsolete. Please give more details about this install. An older one that has gotten into problems or a newer one that's had a bunch of kernels old and new thrown at it to get it to work or a fresh install?

Try this:

```
sudo apt autoremove
```

What do you get, please? Copy the output and whack between code tags.

---

### Post by apol1 on 2016-10-21
Im not sure what you mean by 'this install' do you mean apt-get update? Heres the output from auto remove. Thx for being patient with me, I feel like a chimp fixing a car


 **```
 **sudo apt autoremove
[sudo] password for apollo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-24-generic linux-image-4.4.0-28-generic
  linux-image-extra-4.4.0-24-generic linux-image-extra-4.4.0-28-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
16 not fully installed or removed.
After this operation, 435 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 266447 files and directories currently installed.)
Removing linux-image-extra-4.4.0-24-generic (4.4.0-24.43) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-24-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
Error! Your kernel headers for kernel 4.4.0-24-generic cannot be found.
Please install the linux-headers-4.4.0-24-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-24-generic cannot be found.
Please install the linux-headers-4.4.0-24-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-24-generic cannot be found.
Please install the linux-headers-4.4.0-24-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-24-generic
WARNING: missing /lib/modules/4.4.0-24-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-24-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_7M6A6U/lib/modules/4.4.0-24-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_7M6A6U/lib/modules/4.4.0-24-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: quiet splash acpi_backlight=vendor acpi_osi='!Windows 2013' acpi_osi='!Windows 2012': not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-24-generic (4.4.0-24.43) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-24-generic /boot/vmlinuz-4.4.0-24-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: quiet splash acpi_backlight=vendor acpi_osi='!Windows 2013' acpi_osi='!Windows 2012': not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-24-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-28-generic (4.4.0-28.47) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-28-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
Error! Your kernel headers for kernel 4.4.0-28-generic cannot be found.
Please install the linux-headers-4.4.0-28-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-28-generic cannot be found.
Please install the linux-headers-4.4.0-28-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-28-generic cannot be found.
Please install the linux-headers-4.4.0-28-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-28-generic
WARNING: missing /lib/modules/4.4.0-28-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-28-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_whNNRe/lib/modules/4.4.0-28-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_whNNRe/lib/modules/4.4.0-28-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: quiet splash acpi_backlight=vendor acpi_osi='!Windows 2013' acpi_osi='!Windows 2012': not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-28-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-28-generic (4.4.0-28.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: quiet splash acpi_backlight=vendor acpi_osi='!Windows 2013' acpi_osi='!Windows 2012': not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-28-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-28-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-24-generic
 linux-image-4.4.0-24-generic
 linux-image-extra-4.4.0-28-generic
 linux-image-4.4.0-28-generic
E: Sub-process /usr/bin/dpkg returned an error code (1) **
```**

---

### Post by Bucky Ball on 2016-10-21
Ok, perhaps this will get us somewhere. Run this and it will tell you the exact kernel you are booting from at the moment. What does it say?

```
uname -a
```

Does it end in .45 or .2* (as in .24 or .2 something else)? Keep a note of that because you DON'T want to remove it. We'll try removing the rest because you have some very old kernels lurking in there that may be causing this problem. You are running straight Ubuntu? I take it you don't have Synaptic Package Manager installed?

If you are running the .45 kernel, then do this. Type "sudo apt-get remove linux-" and pressed the TAB key twice to see a list of possible completions. Do you see yours there and a bunch of others? We want to remove the bunch of others, and to do so, if you are not using Synaptic, use a terminal and this command, replacing the kernel numbers with the ones you want to remove or add more if there is more:

```
sudo apt remove linux-image-4.4.0-28-generic linux-image-extra-4.4.0-28-generic linux-image-4.4.0-24-generic linux-image-extra-4.4.0-24-generic
```

Thanks to [Redoubts]("http://askubuntu.com/questions/31667/what-does-no-apport-report-written-because-maxreports-is-reached-already-mean") for the code. There may be a better way than this (I use Synaptic and simply remove all linux-images I don't want then update and 'sudo update-grub' does it) but I don't know it. 

Just to reiterate: DO NOT remove ALL kernels, particularly the kernel that the command 'uname -a' spits out or there will be chaos! (If you remove all kernels there will be none to boot from, obviously. :))

This suggestion was inspired by having a quick search for one of the errors your machine is throwing up:

```
No apport report written because MaxReports is reached already
```

---

### Post by apol1 on 2016-10-22
Im not sure how to do any of that, Heres the output. I may need to rely on your instructions **```
** uname -a
Linux Neptune 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux**
```**

---

### Post by Bucky Ball on 2016-10-22
That kernel is old. Please give the result of this:

```
lsb_release -a
```

---

### Post by apol1 on 2016-10-23
[B]
```
[/B]lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial**
```**
Here ya go :)

---

### Post by RobGoss on 2016-10-23
If you need to update to the latest kernel this might help get you there [http://www.ubuntuupdates.org/package/core/xenial/main/security/linux-image-extra-4.4.0-42-generic](http://www.ubuntuupdates.org/package/core/xenial/main/security/linux-image-extra-4.4.0-42-generic) if you're using a **32-bit, **machine choose the **32-bit,** deb package something for the [B]64-bit

[/B]I also run Ubuntu **16.04.1 LTS** and this is the kernel **4.4.0-42-generic,** that is currently installed on my machine

Hope this helps

---

### Post by apol1 on 2016-10-23
Thank you RobGoss but unfortunately Im unable to install any new software, I gave it a shot anyway just incase but to no avail

---

### Post by RobGoss on 2016-10-27
I would do a clean installation if you're not getting anywhere with one

---


---
title: "Cannot update!"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by pijiu on 2008-05-23
I get this error when trying to update

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

Then when I run:

```
sudo dpkg --configure -a
```

I get:

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
```

Any help please?

---

### Post by alzie on 2008-05-23
Have you already checked you software sources to make sure they're all enabled?

---

### Post by pijiu on 2008-05-23
How would I do that through terminal? My version doesn't seem to have some of the features in the GUI menu. It is 8.04 desktop but i'm accessing it via NX client so perhaps the techie's who install changed things around?

Edit: I don't seem to have synaptic or software sources so I tried this:

```
sudo gedit /etc/apt/sources.list
```

Then I added the following:

```
## MAIN REPOSITORIES
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

## BACKPORTS REPOSITORY
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## PROPOSED REPOSITORY
deb http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse
```

Ran:

```
sudo apt-get update
```

Then ended up with the same result:

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
```

I then checked 'Update Manager' and it said I now had 61 updates available instead of 4 but when I go to install updates I end up with the in my first post:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by ubuntu-freak on 2008-05-23
Try running this command:
 
**sudo apt-get --reinstall install linux-image-2.6.24-16-generic** 

Nathan

---

### Post by pijiu on 2008-05-23
> **reassuringlyoffensive said:**
> Try running this command:
 
**sudo apt-get --reinstall install linux-image-2.6.24-16-generic** 

Nathan

I got this again:

```
******@******:~$ sudo apt-get --reinstall install linux-image-2.6.24-16-generic
[sudo] password for admin: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

I'm at a loss :confused:

---

### Post by Bubba64 on 2008-05-23
I would go to software sources in system-administration software sources and see if what you want is ticked on, and if you did a CD install that it is off, close and let it reload if some things were not on then run the dpkg again. The terminal is great if your real familiar with it but there are other ways of getting the same results while having a better look at what is going on.

---

### Post by rmtatum on 2008-05-24
Someone else had the same problem and found a solution.

[http://ubuntuforums.org/showthread.php?t=616523&page=2](http://ubuntuforums.org/showthread.php?t=616523&page=2)

---

### Post by pijiu on 2008-05-24
> **Bubba64 said:**
> I would go to software sources in system-administration software sources and see if what you want is ticked on, and if you did a CD install that it is off, close and let it reload if some things were not on then run the dpkg again. The terminal is great if your real familiar with it but there are other ways of getting the same results while having a better look at what is going on.

I did say I can't get access to Software Sources and that I'm accessing via Nx Client and have have no way to re-install without asking tech support.

> **rmtatum said:**
> Someone else had the same problem and found a solution.

[http://ubuntuforums.org/showthread.php?t=616523&page=2](http://ubuntuforums.org/showthread.php?t=616523&page=2)

The file they deleted was different from mine. I changed it to the relevant file but when I run the command I get:

```
******@*******:~$ sudo update-initramfs -k 2.6.24-16-generic -d
[sudo] password for admin: 
Cannot delete /boot/initrd.img-2.6.24-16-generic, doesn't exist.

```

Maybe i've not done it right?

---

### Post by Bubba64 on 2008-05-24
1

---

### Post by pijiu on 2008-05-25
Still having no luck guys :/

---

### Post by robertchahine on 2008-05-25
maybe this help?

```

sudo dpkg -l linux-image-2.6*

```

---

### Post by pijiu on 2008-05-25
Unfortunatley it didn't help.

I had a look in the directory where it was reporting the errors and all I could see was:

```
******@******:~$ cd /boot/
admin@ks36538:/boot$ ls
boot.0800                          debianlilo.bmp
boot.0801                          map
bzImage-2.6.24.5-xxxx-std-ipv4-32  sarge.bmp
coffee.bmp                         sid.bmp
debian.bmp                         System.map-2.6.24.5-xxxx-std-ipv4-32

```

and there's nothing in /lib/modules/ either.

---

### Post by pijiu on 2008-05-27
Sorry to bump this but I'm still having no luck even after searching the forums.

---

### Post by robertchahine on 2008-05-27
i don't know if you should reinstall ubuntu or not.
And i suggest this (personnally i don't know even if it will work).
boot up from a live cd , and copy the /lib/modules/2.6.24-16-generic folder to a usb the reboot and paste this folder in your system !

---

### Post by walkman79 on 2008-06-11
I have exactly the same problem and I don't have physical access to the server either, I also use NX client to access the server or putty. So, I can't use the Live CD on it  :( , I could boot up a live cd from  my PC but I would have to download it first, and then upload the folder to the server, and my speeds at home are very low.

I would greatly appreciate if anyone could please share that folder via ftp or any file hosting.

```
$ ls -la /lib/modules/
total 16
drwxr-xr-x  4 root root 4096 2008-06-05 17:58 .
drwxr-xr-x 15 root root 4096 2008-06-11 05:31 ..
drwxr-xr-x  2 root root 4096 2008-06-02 05:39 2.6.24-17-generic
drwxr-xr-x  2 root root 4096 2008-06-05 17:58 2.6.24-18-generic
```

---

### Post by elord on 2008-06-11
i have same problem here with all you guys. is there any possible solutions for this problems? can we reinstall Ubuntu.. if yes!! How? please help..

---

### Post by iaculallad on 2008-06-11
What about giving this command on your terminal:

```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by elord on 2008-06-11
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Setting up update-manager-core (1:0.81.3) ...

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up volumeid (113-0ubuntu17) ...
update-initramfs: deferring update (trigger activated)

Setting up libbind9-30 (1:9.4.1-P1-3ubuntu1) ...

Setting up libavahi-core5 (0.6.20-2ubuntu3.3) ...

Setting up linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.38) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

Setting up openssh-client (1:4.6p1-5ubuntu0.5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: error processing libpng12-0 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up udev (113-0ubuntu17) ...
update-initramfs: deferring update (trigger activated)

Setting up update-manager (1:0.81.3) ...

Setting up avahi-daemon (0.6.20-2ubuntu3.3) ...
 * Reloading system message bus config...                                [ OK ] 
Fixing up startup script priorities...
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 

Setting up bind9-host (1:9.4.1-P1-3ubuntu1) ...
Setting up dnsutils (1:9.4.1-P1-3ubuntu1) ...

Setting up language-pack-en (1:7.10+20080229) ...
Setting up perl-modules (5.8.8-7ubuntu3.1) ...
Setting up language-pack-en-base (1:7.10+20080205) ...
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]

Setting up perl (5.8.8-7ubuntu3.1) ...

Setting up language-pack-gnome-en (1:7.10+20080229) ...
Setting up language-pack-gnome-en-base (1:7.10+20080205) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Errors were encountered while processing:
 libpng12-0


this is what happen.. after i type the command at terminal

---

### Post by iaculallad on 2008-06-11
> **elord said:**
> Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Setting up update-manager-core (1:0.81.3) ...

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up volumeid (113-0ubuntu17) ...
update-initramfs: deferring update (trigger activated)

Setting up libbind9-30 (1:9.4.1-P1-3ubuntu1) ...

Setting up libavahi-core5 (0.6.20-2ubuntu3.3) ...

Setting up linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.38) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

Setting up openssh-client (1:4.6p1-5ubuntu0.5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: error processing libpng12-0 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up udev (113-0ubuntu17) ...
update-initramfs: deferring update (trigger activated)

Setting up update-manager (1:0.81.3) ...

Setting up avahi-daemon (0.6.20-2ubuntu3.3) ...
 * Reloading system message bus config...                                [ OK ] 
Fixing up startup script priorities...
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 

Setting up bind9-host (1:9.4.1-P1-3ubuntu1) ...
Setting up dnsutils (1:9.4.1-P1-3ubuntu1) ...

Setting up language-pack-en (1:7.10+20080229) ...
Setting up perl-modules (5.8.8-7ubuntu3.1) ...
Setting up language-pack-en-base (1:7.10+20080205) ...
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]

Setting up perl (5.8.8-7ubuntu3.1) ...

Setting up language-pack-gnome-en (1:7.10+20080229) ...
Setting up language-pack-gnome-en-base (1:7.10+20080205) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Errors were encountered while processing:
 libpng12-0


this is what happen.. after i type the command at terminal

In your terminal:

```
sudo apt-get install util-linux
sudo dpkg --configure -a && sudo apt-get -f install

```

---

### Post by elord on 2008-06-11
Tnxs a lot dude.. its been done..

---

### Post by sontex on 2008-10-29
sorry if I bring up old topic
I got the same problem and couldn't find any solution.
I would greatly appreciate if anyone could help me how to fix this problem

---

### Post by walkman79 on 2008-10-29
> **sontex said:**
> sorry if I bring up old topic
I got the same problem and couldn't find any solution.
I would greatly appreciate if anyone could help me how to fix this problem

No mate, I had to reinstall the server :(. After you have reinstalled your server, you have to type this command to update your system properly:
> sudo aptitude update && sudo aptitude safe-upgrade -y
Then, you will be able to use the update manager without any problems.

---


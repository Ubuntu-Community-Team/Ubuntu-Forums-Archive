---
title: "broken package need help"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by dynamethod on 2008-06-08
```
xen@darksun:/boot/grub$ sudo apt-get install splashy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdirectfb-extra libsplashy1
Suggested packages:
  splashy-themes
The following packages will be REMOVED:
  usplash
The following NEW packages will be installed:
  libdirectfb-extra libsplashy1 splashy
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/1227kB of archives.
After this operation, 1819kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 179469 files and directories currently installed.)
Removing usplash ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Selecting previously deselected package libdirectfb-extra.
(Reading database ... 179457 files and directories currently installed.)
Unpacking libdirectfb-extra (from .../libdirectfb-extra_1.0.1-7ubuntu3_i386.deb) ...
Selecting previously deselected package libsplashy1.
Unpacking libsplashy1 (from .../libsplashy1_0.3.8-1_i386.deb) ...
Selecting previously deselected package splashy.
Unpacking splashy (from .../splashy_0.3.8-1_i386.deb) ...
Setting up libdirectfb-extra (1.0.1-7ubuntu3) ...
Setting up libsplashy1 (0.3.8-1) ...

Setting up splashy (0.3.8-1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Splashy ERROR: Cannot read XML File <</etc/splashy/config.xml>>. Exiting...
Splashy ERROR: Error occured while starting Splashy
Make sure that you can read Splashy's configuration file

Splashy ERROR: Cannot read XML File <</etc/splashy/config.xml>>. Exiting...
Splashy ERROR: Error occured while starting Splashy
Make sure that you can read Splashy's configuration file

cp: cannot stat `/etc/splashy/config.xml': No such file or directory
dpkg: subprocess post-installation script killed by signal (Interrupt)
E: Sub-process /usr/bin/dpkg returned an error code (2)
xen@darksun:/boot/grub$ sudo apt-get --purge remove splashy
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
xen@darksun:/boot/grub$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
xen@darksun:/boot/grub$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Splashy ERROR: Cannot read XML File <</etc/splashy/config.xml>>. Exiting...
Splashy ERROR: Error occured while starting Splashy
Make sure that you can read Splashy's configuration file

Splashy ERROR: Cannot read XML File <</etc/splashy/config.xml>>. Exiting...
Splashy ERROR: Error occured while starting Splashy
Make sure that you can read Splashy's configuration file

cp: cannot stat `/etc/splashy/config.xml': No such file or directory
dpkg: subprocess post-installation script killed by signal (Interrupt)
xen@darksun:/boot/grub$ sudo apt-get --purge remove splashy
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
xen@darksun:/boot/grub$ 

```


Sigh... how do i fix this damn thing?

---

### Post by Bachstelze on 2008-06-08
Apparently, this Splashy program you installed expects a config file at /etc/splashy/config.xml, which is not there. Read the program's documentation to find out what to do.

---

### Post by quinnten83 on 2008-06-08
Have you already tried running 

```
sudo dpkg --configure -a
```

in the terminal?

you can also open synaptic and remove all files associated with Splashy!

---

### Post by dynamethod on 2008-06-08
Hey look im no programmer but in man splashy-config.xml, its all cryptic to me, all i wanted was to check out a cool picture at boot, now this has happend, im no wizz kid at bash or cli in general, and have absolutly no idea what to do here (im an end-user not a software engineer)

---

### Post by dynamethod on 2008-06-08
i got this when trying to open synaptic package manager:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

---

### Post by bumanie on 2008-06-08
Put the code as described by quinnten83 in terminal and push enter. The error message is saying that the download was interrupted > sudo dpkg --configure -a will start the download at the point it was interrupted. Once it has finished the package should install.

---

### Post by dynamethod on 2008-06-08
I've already actually pasted this in the first post, but here it is again:

```
sudo dpkg --configure -a

```

which gives:

```
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Splashy ERROR: Cannot read XML File <</etc/splashy/config.xml>>. Exiting...
Splashy ERROR: Error occured while starting Splashy
Make sure that you can read Splashy's configuration file

Splashy ERROR: Cannot read XML File <</etc/splashy/config.xml>>. Exiting...
Splashy ERROR: Error occured while starting Splashy
Make sure that you can read Splashy's configuration file

cp: cannot stat `/etc/splashy/config.xml': No such file or directory

```

---

### Post by dynamethod on 2008-06-08
it hangs at:

cp: cannot stat `/etc/splashy/config.xml': No such file or directory


but just spat out:

cp: cannot stat `/home/xen/.gvfs': Permission denied

after like 5 mins of it hanging there

---

### Post by quinnten83 on 2008-06-08
okay, 
I really need to be sitting behind the computer to try stuff.
but lets try this

```
sudo apt-get purge splashy
```

It will deinstall splashy and the configuration files.
We can try reinstalling it again if this works.

---

### Post by dynamethod on 2008-06-08
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


the package manager is broken, i cant use apt-get or anthing related to apt untill apt is fixed

---

### Post by philinux on 2008-06-08
Does this file exist can you browse to it.

/etc/splashy/config.xml

Or create a blank file or get one from the splashy website?

Here's what the config file contents should look like.

You can create this file yourself. Something must have gone wrong to not create it.
[http://splashy.alioth.debian.org/wiki/themes](http://splashy.alioth.debian.org/wiki/themes)
Found this from google.

---

### Post by dynamethod on 2008-06-08
lol splashy is the last thing on my mind right at this moment seeing as my package manager is now broken, attempting another re-install, sigh

---

### Post by jherievans on 2009-04-24
Ok, I know this is an old thread, but I am having the exact same issue. I'll try not to be as abrasive as the fellow above. I have navigated to the  /etc/splashy/ folder and have figured out that the config.xml has had .old added to the end of it. The problem, though, is that I cannot rename it. It will not let me. Can anyone help me?

** EDIT :: I should have done more research before reopening this thread. Sorry about that. I've fixed the problem, entirely through the help of Philinux. I wish the other fellow had given his suggestions a shot.**

---


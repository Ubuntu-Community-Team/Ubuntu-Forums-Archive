---
title: "VMware Player 1.0.1 package + Usage Guidelines"
date: 2006-01-28
forum: Outdated Tutorials &amp; Tips
---

### Post by NeTo on 2006-01-28
I have built a checkinstall package for [VMware Player](http://www.vmware.com/products/player/). It has postinst and prerm scripts, to ensure everything gets correctly installed and setup. The scripts support is a new feature in [Checkinstall 1.6.0](http://asic-linux.com.mx/~izto/checkinstall/)

**Contents**
1. Installation
2. Usage
3. Package Compilation (Not Required)

**1. Installation**
Open a terminal window and type:```
sudo apt-get install build-essential gcc-3.4 g++-3.4 linux-headers-`uname -r`
``` to install the package dependencies. Run:```
wget http://netosoft.no-ip.org/Ubuntu/breezy/vmware/vmwareplayer_1.0.1-1~neto1_i386.deb
```This will download a .deb file in your current directory. To install this package type:```
sudo dpkg -i vmwareplayer_1.0.1-1~neto1_i386.deb
```After installation you'll need to answer a few configuration questions (the default answers are fine for Ubuntu). After that you'll be ready to use VMware Players

**2. Usage**
To use the player, you need to already have a virtual machine (blank or with an OS installed). They consist of various files, the most important are:
[LIST]
[*]A file with a vmx extension has the Virtual Machine (VM) options. You can double click this file on Nautilus or Konqueror to start the VM. You can also edit this file in any text editor.
[*]Files with a vmdk extension represent a virtual hard-disks.  These can be of several kinds: growable, of fixed size, that link a physical hard disk, ide/scsi, etc.
[/LIST]
To install Windows 2000/XP you can follow the instructions in [thread=84275]this how-to[/thread], from which I also took the dependency list. Just read from the Qemu part for the steps you need to take.

Alternatively, you can search the [VMware Virtual Machibe Center](http://www.vmware.com/vmtn/vm/) for virtual machines with preinstalled OSs. For example, there is a [Browser Appliance](http://www.vmware.com/vmtn/vm/browserapp.html) VM which has Ubuntu 5.10 + Firefox 1.5.

I have also attached a file which has blank virtual disks taken from several places over the web. Download the *hd-pack.tar.gz* file from this post for a set of scsi drives (500MB, 10GB, 20GB, 20GB splitted 9 files of 2.3GB/each, 20GB splitted 8 files of 2.5GB/each) and a ide drive (100GB).

**3. Package Compilation (Not Required)**
If you want to compile the package yourself you can download the *vmwareplayer-1.0.1-checkinstall.tar.gz* file from this post. It has all of the checkinstall files I used, including the postinst and prerm scripts. 

You need to download and install checkinstall 1.6.0 first (the 1.5.3 version in the Breezy repos won't work). I made deb packages for it, and hopefully I will post them in a separate thread soon.

You also need to have the [vmware player tarball](http://download3.vmware.com/software/vmplayer/VMware-player-1.0.1-19317.tar.gz). Extract it, and copy the contents of *vmwareplayer-1.0.1-checkinstall.tar.gz* to the *vmware-player-distrib* folder.

Run ```
export CC=/usr/bin/gcc-3.4 && checkinstall -si vmware-install.pl
``` to make the package. You will need to answer some questions (you can use the defaults if you're unsure).

---

### Post by sbaker33 on 2006-01-31
Has anyone been able to download the .deb file?  I have been trying for two days now and heve never been able to get connected...
-sbaker

---

### Post by NeTo on 2006-01-31
It's most likely because I wrote the link incorrectly (I forgot the port number). Now the link should be fixed in the first post.

---

### Post by bartbes on 2006-02-02
still not working (for me)

---

### Post by spook on 2006-02-03
I can't connect either :(

---

### Post by NeTo on 2006-02-03
[QUOTE=spook]I can't connect either :([/QUOTE]

Sorry guys, my PC has been down for a few days because I'm doing a major hardware upgrade (which sadly hasn't turn out very well). The download will be down at least until tomorrow. Again, sorry for any inconvenients :cry:

---

### Post by NeTo on 2006-02-07
Since I'll be offline for the time being, I have uploaded the file in rapidshare. Here's the link: [http://rapidshare.de/files/12773787/vmwareplayer_1.0.1-1_neto1_i386.deb.html](http://rapidshare.de/files/12773787/vmwareplayer_1.0.1-1_neto1_i386.deb.html)

---

### Post by NeTo on 2006-03-21
It seems that no-ip.com doesn't redirect addresses that look like *membername.no-ip.com* anymore for non-premium members. I didn't realized the issue until now, so the links for the sources were down all of this time.

I have now registered a different address, so I have updated the (now hopefully) working link in the first post. Sorry for any inconvenience.

The vmware player link in the first post should be working atm.

---

### Post by kspades on 2006-03-22
thanks, this works perfectly for me, save me the trouble of installing the full VMware when I've already got my machine files.

---

### Post by DragonOrta on 2006-03-31
I keep on getting these error messages at the "sudo dpkg -i vmwareplayer_1.0.1-1~neto1_i386.deb dpkg-deb:" step.


`vmwareplayer_1.0.1-1~neto1_i386.deb' is not a debian format archive
dpkg: error processing vmwareplayer_1.0.1-1~neto1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 vmwareplayer_1.0.1-1~neto1_i386.deb

---

### Post by NeTo on 2006-04-01
[QUOTE=DragonOrta]I keep on getting these error messages at the "sudo dpkg -i vmwareplayer_1.0.1-1~neto1_i386.deb dpkg-deb:" step.
[/QUOTE]

The package may have corrupted during the download process. Run ```
md5sum vmwareplayer_1.0.1-1~neto1_i386.deb
```The md5sum of this package should be: *5d522ace8bfd22f9c7a4ab283a7ebcf8*. If you get a different value, try re-downloading the package.

---

### Post by stengah on 2006-04-16
[QUOTE=NeTo]
**1. Installation**
Open a terminal window and type:```
sudo apt-get build-essential gcc-3.4 g++-3.4 linux-headers-`uname -r`
``` to install the package [/QUOTE]

when trying to tun this command I get an error like this:

"E: Invalid action build-essential"

I'm new in ubuntu business - d'you have any idea what's going wrong???:confused:

---

### Post by NeTo on 2006-04-19
[QUOTE=stengah]when trying to tun this command I get an error like this:

"E: Invalid action build-essential"

I'm new in ubuntu business - d'you have any idea what's going wrong???:confused:[/QUOTE]


Oops, typo :p. The command should be: ```
sudo apt-get install build-essential gcc-3.4 g++-3.4 linux-headers-`uname -r`
```

---

### Post by stengah on 2006-04-19
#13: Thanks a lot - I think it got me up and running!

---


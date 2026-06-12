---
title: "help installing Scribus_1.2.1"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by dgloe on 2012-04-14
I am trying to install Scribus_1.2.1 software with no success. I have recently installed Ubuntu on two older computers, so I can learn Ubuntu. One is an 8.04 server, I use to test and program Html,MySql,Php and Samba. The other computer is a 5.04 gnome desktop, I use for Open Office and Desktop Publishing (ie Scribus). I have tried to install Scribus from the index of: [http://old-releases.ubuntu.com/ubuntu/pool/main/s/scribus](http://old-releases.ubuntu.com/ubuntu/pool/main/s/scribus) /scribus_1.2.1-ubuntu2_i386.deb. I tried putting this path in the sources.list file, then used Synaptic with no success. I also burned the .deb file to a cd and mounted it to the 5.04 file system with no success. What about cp the scribus_1.2.1-unbuntu2_i386.deb in either directores: /var/lib/apt/list or /var/cache/apt/archives on the 5.04 computer? Shuould I use another of the file formats: .dsc,.diff.gz,-powerpc.deb or even tar.gz? If you suggest tar.gz. What directories should I create (mkdir) to copy,unpack,install,build and compile. Any help or suggestions would be much appreciated.

---

### Post by MG&amp;TL on 2012-04-14
I'm not sure the required dependencies will be provided for on such an old release. Consider upgrading, particularly as you 'recently' installed them.

If you insist on your configuration, I would recommend a source tarball -.tar.gz. Obtain one, then uncompress it and show us a screenshot or similiar of what is inside to help you install it.

---

### Post by dgloe on 2012-04-14
I tried to install 8.04 desktop on this 5.04, but it wouldn't install. The install process came up with some boot command window (I think something like  ramfs (I can't remember the first two letters)). It was waiting for me to enter a command. I then tried 6.10 desktop and it hung up. 5.04 installed. At this point, I think I'll go with your suggestion to use the tarball. Thank you for your help!!!!!!! Who needs MS when we have all you great people out there that are willing to help!!!!!!!!!!!!!! I used tarballs when the server was Fedora. I'll re-post if I get hung up.

---

### Post by MG&amp;TL on 2012-04-14
Possibly initramfs.

What are the specs of the 5.04 one, it's possible the installer is running out of memory.

No problem. :)

---

### Post by dgloe on 2012-04-14
Mg&TL, The specs on the 5.04 computer are memory 98mb, Release 4.1 Award BIOS by eSupppport.com, AMD-K6-2/350cpu, WD153aa 15GbHDD. Probably no enough mem for 8.04. dgloe

---

### Post by sandyd on 2012-04-14
> **dgloe said:**
> I am trying to install Scribus_1.2.1 software with no success. I have recently installed Ubuntu on two older computers, so I can learn Ubuntu. One is an 8.04 server, I use to test and program Html,MySql,Php and Samba. The other computer is a 5.04 gnome desktop, I use for Open Office and Desktop Publishing (ie Scribus). I have tried to install Scribus from the index of: [http://old-releases.ubuntu.com/ubuntu/pool/main/s/scribus](http://old-releases.ubuntu.com/ubuntu/pool/main/s/scribus) /scribus_1.2.1-ubuntu2_i386.deb. I tried putting this path in the sources.list file, then used Synaptic with no success. I also burned the .deb file to a cd and mounted it to the 5.04 file system with no success. What about cp the scribus_1.2.1-unbuntu2_i386.deb in either directores: /var/lib/apt/list or /var/cache/apt/archives on the 5.04 computer? Shuould I use another of the file formats: .dsc,.diff.gz,-powerpc.deb or even tar.gz? If you suggest tar.gz. What directories should I create (mkdir) to copy,unpack,install,build and compile. Any help or suggestions would be much appreciated.
Wow.
5.04 is really old.

If you had a newer version, you could have used the ppa.
[https://launchpad.net/~scribus/+archive/ppa](https://launchpad.net/~scribus/+archive/ppa)

---

### Post by MG&amp;TL on 2012-04-15
Lubuntu uses 128Mb-Puppy Linux may be a good distribution, depending on whether you want a new system or not. :)

---

### Post by mastablasta on 2012-04-15
also Slitaz will work on that.

---

### Post by dgloe on 2012-04-17
MG&TL, Thank You for your continued help! I have downloaded lupu-528.005.iso and I am about to download the 528 with libre office suite. I use Open Office, so Libre will be great. I am going to install the puppy with libre first.  If it crashes, I'll try puppy without libre. Should work great!!!! Will re-post a reply.

---

### Post by dgloe on 2012-04-23
Sandy, thank you again for helping me with my oooold computer that I am using to write the rough draft for a book on "How To Build Your Own Home. I tried to install SliTaz, but it hung up on the install with a initramfs error. Just not enough memory. I also tried install Puppy-linux, which it did install but the word processor AbiWorld kept locking up. Probably low ram again. So I finally just re-installed Ubuntu Hoary Hedgehog 5.04. It installed and works find and uses Open Office. Thank You for your willingness to help. I am going to look for a couple 128mb memory sticks locally.

---

### Post by dgloe on 2012-04-23
Mg&TL, thank you again for helping me with my oooold computer that I am  using to write the rough draft for a book on "How To Build Your Own  Home. I tried to install SliTaz, but it hung up on the install with a  initramfs error. Just not enough memory. I also tried install  Puppy-linux, which it did install but the word processor AbiWorld kept  locking up. Probably low ram again. So I finally just re-installed  Ubuntu Hoary Hedgehog 5.04. It installed and works find and uses Open  Office. Thank You for your willingness to help. I am going to look for a  couple of 128mb memory sticks locally.

---


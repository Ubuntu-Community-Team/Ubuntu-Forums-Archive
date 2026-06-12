---
title: "Build Thin client"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by sjude on 2008-05-29
I am having a problem in building thin client.  I followed the procedure in [http://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](http://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall) (Installing on top of an already running desktop system) to install ltsp-server-standalone and then ltsp-build-client

At the end of the download I get an error.  

I have posted this before but my post cannot be seen in this forum so I am posting again.

Everytime I start again the retriving of files starts from the beginnig and at the end I get an error "W: Failure trying to run: chroot /opt/ltsp/i386 dpkg --force-depends --install var/cache/apt/archives/base-files_4.0.1ubuntu5_i386.deb
var/cache/apt/archives/base-passwd_3.5.16_i386.deb
error: LTSP client installation ended abnormally"

The download is almost 49MB each time I build the client.  is there any other way to build a thin client enviroment.  Following this procedure I was successful to build and thin client enviroment on my Dell Laptop and also on a Desktop.  This is the third machine I am tying to do the same and failed everytime (about 15 times).

Could be a hardware problem ?  I am not sure.

I also used APTONCD to archive the downloaded .deb files and restore it back on this machine so that the Internet retriving of files does not take place.  But, it always connects to 
I: Checking component main on [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)...
and downloads files.

I have attached the CLI output.  There seems to be no error in any downloaded files then why the error.

---

### Post by quelx on 2008-05-29
Have you tried downloading the files (base-files_4.0.1ubuntu5_i386.deb and base-passwd_3.5.16_i386.deb) from here:

[http://packages.ubuntu.com/hardy/i386/base-files/download](http://packages.ubuntu.com/hardy/i386/base-files/download)

then moving them into **/var/cache/apt/archives/** then running the install?

---

### Post by sjude on 2008-06-01
> **quelx said:**
> Have you tried downloading the files (base-files_4.0.1ubuntu5_i386.deb and base-passwd_3.5.16_i386.deb) from here:

[http://packages.ubuntu.com/hardy/i386/base-files/download](http://packages.ubuntu.com/hardy/i386/base-files/download)

then moving them into **/var/cache/apt/archives/** then running the install?

These packages were already installed but I downloaded it again and reinstalled.

I have to delete the /opt/ltsp/i386 directory to run sudo "ltsp-build-client".  This starts the Retrieving and Validating the packages.  All the downloading again - 47 MB.  Is there anyway to take the files from the /apt/cache/archives

I again get the same error 
I: Installing core packages...
W: Failure trying to run: chroot /opt/ltsp/i386 dpkg --force-depends --install var/cache/apt/archives/libc6_2.7-10ubuntu3_i386.deb
error: LTSP client installation ended abnormally

This time there was error in Retrieving 2 packages which are already installed.
I: Retrieving readline-common
W: Couldn't download package readline-common
I: Retrieving sed
W: Couldn't download package sed

I am  not getting this done.  Why is it downloading packages that already exist.

---

### Post by AnRa on 2008-06-01
I recommend downloading the alternate desktop CD, as it has all the components needed to install an LTSP server (if you press F4 on the first screen you can select LTSP mode).

---

### Post by sjude on 2008-06-02
> **AnRa said:**
> I recommend downloading the alternate desktop CD, as it has all the components needed to install an LTSP server (if you press F4 on the first screen you can select LTSP mode).

I tried booting with Alternate CD but the menu to press F4 did not come up.  The only option was to press ENTER on the boot.  Anyway, I solved the problem with an option as below.

sudo ltsp-build-client --copy-packages-cache

This copied all the *.deb files from /var/cache/archive and started the process without downloading.  Later it downloaded the missing image files (about 20MB) and completed successfully.

---


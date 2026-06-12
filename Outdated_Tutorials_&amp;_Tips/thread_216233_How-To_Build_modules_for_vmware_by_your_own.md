---
title: "How-To: Build modules for vmware by your own"
date: 2006-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Chrissss on 2006-07-15
Hi There!

The last kernel upgrade is over a week ago, and still there's no new vmware-player-kernel-modules-2.6.15-26 package, so that people can user vmware player with this new kernel. But why wait, when you can build those modules by your own. 

Those two packages have to be installed
[B]* build-essential
* linux-headers-386 (or whatever architecture you use)[/B]

Then open a editor
```
gedit ~/build_vmwaremodules
``` and paste this code
```
#!/bin/bash

VMPLAYER_URL=http://download3.vmware.com/software/vmplayer/VMware-player-1.0.1-19317.tar.gz
KERNEL=`uname -r`

cd /tmp
wget $VMPLAYER_URL
mkdir /lib/modules/$KERNEL/misc/
tar -xzf VMware-player-1.0.1-19317.tar.gz
cd vmware-player-distrib/lib/modules/source/
tar -xf vmmon.tar
cd vmmon-only
make
cp vmmon.ko /lib/modules/$KERNEL/misc/
cd ..
tar -xf vmnet.tar
cd vmnet-only
make
cp vmnet.ko /lib/modules/$KERNEL/misc/
depmod -a
modprobe vmmon
modprobe vmnet
rm -rf /tmp/vmware-player-distrib
``` This script will download vmware_player  (30mb!!), extract the kernel modules source, compile and install them
```
chmod 755 ~/build_vmwaremodules
``` and finally execute it
```
sudo ./build_vmwaremodules
``` Now you should be able to use vmplayer again :)

CU
 Christoph

PS: @Mods I just submitted a howto without proper titel. Please delete the first one and publish just this own. And while you're at it. Please delete this "PS" Text ;) Thanks

*EDIT (by matthew): Since I deleted the other thread it's probably a good idea to leave this "PS" here for a week or so in case anyone wonders what happened to the other thread. I put a link to this thread in the "reason" line that shows the other thread was deleted.*

---

### Post by AlbertVeli on 2006-07-17
I tried your method and it works. But it kind of bothers me to mix debianized files with custom files (vmmon.ko and vmnet.ko). The proper Debian-way to do it would be to download vmware-player-kernel-source:
```
 sudo apt-get install vmware-player-kernel-source
```

and then compile a custom vmware-player-kernel-modules-2.6.15-26-686 deb file. This requires a couple of commands but it is not so complicated.
First install the kernel sources
```
 sudo apt-get install linux-source
```

Then unpack both the linux source and the vmware module source:
```
 cd /usr/src
 sudo tar jxvf linux-source-2.6.15.tar.bz2
 sudo tar jxvf vmware-player-kernel-source.tar.bz2
```

Now copy the current configuration from /boot and build the vmware kernel module:
```
 cd linux-source-2.6.15
 sudo cp /boot/config-2.6.15-26-686 .
 sudo make-kpkg clean
 sudo make-kpkg --revision=26 --append-to-version="-26-686" modules_image
```

Note: Before building with make-kpkg you might have to comment out (or remove) the EXTRAVERSION row in the file Makefile:

#EXTRAVERSION = .7-ubuntu1

After make-kpkg finishes you can install the created deb-file:

 sudo dpkg -i vmware-player-kernel-modules-2.6.15-26-686_2.6.15.10-7+26_i386.deb

But it really is easier if someone could do this and upload the 2.6.15-26 deb(s) into the official repositories...

---

### Post by OrganicPanda on 2006-07-17
snip...

> Now copy the current configuration from /boot and build the vmware kernel module:
```
 cd linux-source-2.6.15
 sudo cp /boot/config-2.6.15-26-686 .
 sudo make-kpkg clean
 sudo make-kpkg --revision=26 --append-to-version="-26-686" modules_image
```
... snip

i have a problem with the line 
```

 sudo cp /boot/config-2.6.15-26-686 .

```
this file doesn't exist, i do however have a 386 in my computer and a config-2.6.15-26-386 file, so when i change it that works ok

now the showstopper is make-kpkg isnt recognised, is this something i dont have or a typo?

edit ok i see it's meant to be something like make dpkg-clean but the linux source directory has no config so it wont make, what do i do?

---

### Post by OrganicPanda on 2006-07-17
right, i came into this thread and thought the 2nd post was better but, as i posted above ^^, that didnt work so i tried the original method and, i think, it worked but none of my vmx files are associated with vmware player and i dont know how to launch the application by itself, help

edit: i used to call something like sudo vmplayer /files/virtual/virtual_windowsxp/virtual_windowsxp.vmx but now vmplayer isnt recognised, i'm starting to think this isn't going to work, stupid kernal update

---

### Post by Chrissss on 2006-07-17
> **AlbertVeli said:**
> I tried your method and it works. But it kind of bothers me to mix debianized files with custom files (vmmon.ko and vmnet.ko). The proper Debian-way to do it would be to download vmware-player-kernel-source...
Yep you are right, but I don't see a big problem there, cause when the "real" vmware-player-kernel-modules-2.6.15-26 appear inside the repositories, the self built modules will be overwritten. Or in the case apt complains that those two files are allready there, you can easily delete them.

But nevertheless, buidling a decent .deb package is the better way to do it :)

---

### Post by OrganicPanda on 2006-07-17
well i couldn't get any of this to work but vmware server looks all good, infact better [http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server]("http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server")

---

### Post by AlbertVeli on 2006-07-18
Hi!

> **OrganicPanda said:**
> i have a problem with the line 
 sudo cp /boot/config-2.6.15-26-686 .
this file doesn't exist, i do however have a 386 in my computer and a config-2.6.15-26-386 file, so when i change it that works ok


Then you probably have the default i386 kernel. You can check with the command:

 uname -r

copy the config-file that ends with the same numbers as 'uname -r' tells you.

> **OrganicPanda said:**
> now the showstopper is make-kpkg isnt recognised, is this something i dont have or a typo?


It is part of kernel-package:

 sudo apt-get install kernel-package

And when you run make-kpkg, replace 686 with 386 on the command line since you are running the 386 kernel.

Good Luck!


/Albert


PS The method in the first post is probably easier if you don't get this to work... DS

---

### Post by OrganicPanda on 2006-07-18
kool cheers, but ive given upo, vmware server is alot better anyway so i will just use that from now on, thanks anyway, sorry for hijacking this thread for no real reason :p

---

### Post by sharperguy on 2006-07-18
> **AlbertVeli said:**
> 
But it really is easier if someone could do this and upload the 2.6.15-26 deb(s) into the official repositories...

Should we file a bug report about this?

---

### Post by AlbertVeli on 2006-07-18
> **sharperguy said:**
> Should we file a bug report about this?

Yes. I don't know how to file a bug report the "Ubuntu way". But please do fill in a bug report.

The packages available in the current dapper repositories are:

[LIST]
[*]vmware-player-kernel-modules-2.6.15-23
[*]vmware-player-kernel-modules-2.6.15-25
[/LIST]

But the current kernel version is 2.6.15-26. So the vmware-player-kernel-modules prebuilt module package should also be updated. Actually all module packages should be updated each time the kernel is updated. But, like the first post said, until this package is updated the vmware-player package is broken.

---

### Post by sharperguy on 2006-07-18
Ok, i baisically just copy/pasted the relevent stuff you said there into a bug report.

edit: Nice response :) , theyve done it already

---

### Post by HJB on 2006-07-20
Thank you so much. 
Great post:p

---

### Post by finite9 on 2006-08-23
I feel like i've messed up my installation a bit..cant get vmware player to work.

I understand that 2.6.15-23 kernel works fine with the vmware packages in the main repository, and I have tested this at work on an i386 Ubuntu 60.6.

However, at home on an amd64 Ubuntu 6.06 with kernel 2.6.15-25, I cannot see the correct kernel module for vmware player in teh repos.  If I start firefox and go to archive.ubuntu, I can see that there is a deb for amd64 2.6.15-25, but my synaptic cannot see it!

What gives?

Maybe it has something to do with the fact that I have 2.6.15-23, -25 and -26 installed on my system??  I tried to remove -23 but now vmware player wont even install with apt-get!  I get loads of errors in Synaptic.

---

### Post by ssmaxss on 2006-08-28
I also have amd64 an -25 kernel. And no module in apt. So I downloaded deb from archive.ubuntu.com and install it via sudo dpkg -i <deb>

---

### Post by marceluda on 2006-09-27
I have the nex error while executing:
# make-kpkg --revision=26 --append-to-version="-26-386" modules_image


```
make[1]: se ingresa al directorio `/usr/src/modules/vmware-player-kernel'
/usr/bin/make -w -f debian/rules kdist_clean kdist_config binary-modules
make[2]: se ingresa al directorio `/usr/src/modules/vmware-player-kernel'
echo '# NOTE: THIS FILE IS AUTO-GENERATED FROM control.modules.in.in' > \
          debian/control.modules.in
sed -e 's/@@KVERSION@@/2.6.15/g' \
            -e 's/@@ABIVER@@/2.6.15-23/g' \
           debian/control.modules.in.in >> debian/control.modules.in
if [ "" ]; then \
                echo '# NOTE: THIS FILE IS AUTO-GENERATED FROM control.in' > \
                  debian/control; \
                sed -e 's/@@KVERSION@@/2.6.15/g' \
                    -e 's/@@ABIVER@@/2.6.15-23/g' \
                   debian/control.in >> debian/control ; \
        fi
dh_testdir
dh_testdir: cannot read debian/control: No existe el fichero ó directorio

make[2]: *** [clean] Error 1
make[2]: se sale del directorio `/usr/src/modules/vmware-player-kernel'
make[1]: *** [kdist_build] Error 2
make[1]: se sale del directorio `/usr/src/modules/vmware-player-kernel'
Module /usr/src/modules/vmware-player-kernel failed.
Hit return to Continue
```

---


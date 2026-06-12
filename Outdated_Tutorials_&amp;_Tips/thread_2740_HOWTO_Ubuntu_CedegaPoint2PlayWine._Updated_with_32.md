---
title: "HOWTO: Ubuntu Cedega/Point2Play/Wine. Updated with 32bit chroot installation."
date: 2004-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by dmatrix on 2004-10-31
Sorry to crosspost. I just thought this would get more use in this forum than the amd64 forum.

I have just updated the Ubuntu Cedega/Point2Play/Wine Howto on the Unofficial TransGaming wiki. Detailed instructions on building a clean 32bit chroot with debbootstrap. These instructions are also useful for AMD64 users wanting a 32bit Firefox with 32bit plugins (ie. Firefox + Flash + mplayer-mozilla + w32codecs).

Looking for some help in the ATI section and the 32bit chroot issues section.

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

---

### Post by xpt on 2005-01-24
[QUOTE=dmatrix]
[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)[/QUOTE]

Very insightful article!

I just tried it and it works perfectly. 

Some considerations:

,-----
| Then mount (mkdir) each folder. Then type:
| 
|  dchroot -d
| 
| This should start a shell in the chroot. 
`-----

It maybe better to clearly state how to mount them. 

More over, in the chroot environment, the /etc/fstab is empty:

$ cat /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM

shouldn't it be populated with something? Should I use bind mount?...

Further more, refering back to the Debian  AMD64 HOW-TO
[https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html](https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html)

I noticed that there is a step to setup 32bit libraries, Shouldn't that be included in?

I quote them here:

- - - - >8 - - - -
To use the 32bit libraries in your 64bit system you have to add the library path of your chroot into your /etc/ld.so.conf:

/usr/X11R6/lib
# chroot i386 system libs
/var/chroot/sid-ia32/lib
/var/chroot/sid-ia32/usr/lib
/var/chroot/sid-ia32/usr/X11R6/lib
/var/chroot/sid-ia32/usr/local/lib

You also need a link to your 32bit linker in the /lib path. Change in to directory /lib and create a link to the 32bit linker library of your chroot: (The name of the 64bit linker is ld-linux-x86-64.so.2)

cd /lib
ln -s /var/chroot/sid-ia32/lib/ld-2.3.2.so ld-linux.so.2

Now run ldconfig to update your linker's cache.

Now you should be able to run ia32 binaries with the libs from your chroot within your 64bit system. Having the libs in a separate chroot makes it easy for you to update or install the 32bit libraries with apt-get.
- - - - >8 - - - -

---

### Post by xpt on 2005-01-24
Another thing, here is what I did with the "Transparent 32bit chroot"

sudo su -

cat <<'EOF' > /usr/local/bin/do_dchroot
#!/bin/sh

exec dchroot -d "`echo $0 | sed 's|^.*/||'` $*"
EOF

Then do:

 chmod 755 /usr/local/bin/do_dchroot

It is better and safer this way.

---

### Post by gmc on 2005-02-19
Hello dmatrix,

On your webpage [http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Enabling_Nvidia_3D_driver](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Enabling_Nvidia_3D_driver) under the "Optimizing Nvidia 3D driver" section. You suggest editing the /etc/init.d/bootmisc.sh file. A better way to add those NVreg_* switches is to edit the /etc/modutils/nvidia-kernel-nkc and add the following line:

*options nvidia NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1NVreg_ReqAGPRate=8 *

Then run update-modules and reboot (or unload/reload the nvidia driver).

---


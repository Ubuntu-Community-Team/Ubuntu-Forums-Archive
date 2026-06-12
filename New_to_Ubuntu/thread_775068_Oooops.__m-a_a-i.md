---
title: "Oooops.  m-a a-i"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by shadowpool on 2008-04-29
I accidentally ran "sudo m-a -t a-i" without any other arguments and it installed a whole bunch of things I'm not sure I wanted to install.  I restarted and everything seems to work, but I'm still not sure what I did by running this.  Does anyone know?  Did I corrupt my pristine Hardy install already?  

Thanks!

---

### Post by Monicker on 2008-04-29
What module were you trying to build with module assistant?  I doubt that any harm was done.  At most you probably took up some extra space by building modules you may not really need.

---

### Post by shadowpool on 2008-04-29
I was trying to build tp-smapi.  Looking through term.log, I found where module assistant started to install things, copied that part of the log to another file and did:

cat filea | grep 'deselected package' > fileb

And did some editing on gedit to get a list of packages installed:
debconf-utils html2text gettext intltool-debian po-debconf debhelper alsa-source bcm5700-source kernel-package cdfs-src comedi-source cpad-kernel-source device3dfx-source dpatch drbd0.7-module-source em8300-source m4 autoconf autotools-dev automake1.7 fdupes intltool cdbs exmap-modules-source fglrx-kernel-source fuse-source quilt gpib-modules-source ivtv-source gcc-4.1-base cpp-4.1 gcc-4.1 kqemu-source linux-wlan-ng-source dkms lirc-modules-source mga-vid-source nozomi-source nvidia-kernel-source flex bison openafs-modules-source openswan-modules-source ov511-source ppscsi-source qc-usb-source realtime-lsm-source rt2400-source rt2500-source rt2570-source rtai-source sl-modem-source zlib1g-dev lzma-dev squashfs-source sysprof-module-source unicorn-source unionfs-source zaptel-source gawk zd1211-source

I'm guessing it's safe to remove these?  Also, is there a way to delete the built modules that I don't need?

---

### Post by Monicker on 2008-04-29
m-a should take you to an ncurses menue where you can remove things.  I recognize some of them, but not all.

linux-wlan-ng-source - for madwifi drivers
rt2400-source - wireless driver
rt2500-source - wireless driver
rt2570-source - wireless driver 
squashfs-source - compress fs used a lot for live cds
unionfs-source - compress fs used a lot for live cds
lirc-modules-source - remote control driver
ivtv-source - tv capture card driver
nvidia-kernel-source - do you have an nvidia card?
openswan-modules-source - ipsec vpn


Maybe that will help some in determining what you can remove.

---


---
title: "integrated graphics issues, alienware w/ AMD Radeon HD 6900M"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by ofclouds on 2013-02-21
my Windows system crashed about a week ago after a simple update, so I've turned to Linux and am extremely new at this.  

Currently running **12.10 64bit **with **Intel® Core™ i7-2720QM CPU @ 2.20GHz × 8  **and it *says* the graphics card is **Intel® Sandybridge Mobile**,but i'm guessing that's the weaker built-in gfx card my computer has. I've tried just about everything I could find. The Additional Drivers section classifies my gaming card as a **ATI:Blackcomb Radeon HD 6900M**, so why it says it's sandybridge in the "Details" section, I don't know. 


[LIST]
[*]the fglrx command doesn't work.
[*]proprietary options leave me with just the desktop screen and no ui/sidebar
[*]i've tried this [http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/](http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/)  (won't let me run/isntall the older drive)
[*]won't let me use switcharoo  -- i type in "echo ON > /sys/kernel/debug/vgaswitcheroo/switch" and similar commands; it says I don't have permission. I believe the ABILITY is there? -- But I don't know how to get past the permission denial. I've tried a few different commands: sudo, sudo -i, nautilus... (IDK what they mean, I just saw them suggested in other threads/websites)
[/LIST]
There are a few other things, but, honestly I can't remember them anymore. i've spent like 3 days trying whatever I can find. I don't know many terminal commands. 

 My objective is to be able to play Path of Exile without the lag/freezes/disconnects which are caused by--I believe, anyway--the use of whatever sandybridge is, as opposed to my gaming card. Everything else is working fine. Just can't play games properly...

  If you tell me what extra info you need, (and how to go about it if necessary), i'll be glad to.  
[LEFT]
Thanks. 
[/LEFT]

---

### Post by Muty-bg on 2013-02-21
Hmm I'm not sure if this applies for the alienwares too but I can force my dell notebook to use the faster videocard in bios, but if you say that you get the desktop without the ui when you install fglrx from the ubuntu repository I guess it means that it is using the ati card and not the cpu built in one.


I have a radeon 7970 HD in my home pc and I had the same issue with the missing ui when I installed the drivers from the official repository and the only reasonable way I was able to get it working was by generating the deb packages using the installer that you can download directly from the AMD site. 

You can download it from here:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

After that just extract the script and run it. It will give you an option to generate packets for your system instead of installing it directly. Do that and you'll end up with 2 deb packages in the folder where you ran the installer from. Install them, restart and you should be good to go. Let me know if you need further help with that.

As for Path of Exile. I play it on my notebook on ubuntu from time to time without any issues. My advice is to use PlayOnLinux rather than directly installing wine and then POE with it as it will set up several dependencies that you'll have to otherwise deal with by hand.
You can install playonlinux from the ubuntu software center.

---

### Post by ofclouds on 2013-02-21
hey, and thanks for your help.

i got this message:  

"Supported adapter detected.
Check if system has the tools required for installation.

fglrx installation requires that the system have kernel headers.  /**lib/modules/3.5.0-24-generic/build/include/linux/version.h** cannot be found on this system."


do i need to figure out how to get that, or do the --force thing it also suggests?

package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:9.012-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html> dpkg-source --before-build fglrx.SU8gLS
dpkg-buildpackage: host architecture amd64
debian/rules build
#Create important strings
for i in 10fglrx \ dkms.conf \ fglrx.install \ fglrx-dev.install \ fglrx-dev.links \ fglrx-amdcccle.install \ fglrx.grub-gfxpayload \ fglrx.dirs \ fglrx.links \ fglrx.postinst \ fglrx.postrm \ fglrx.preinst \ fglrx.prerm \ overrides/fglrx; do \ sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \ -e "s|#LIBDIR#|usr/lib|g" \ -e "s|#LIBDIR32#|usr/lib32|g" \ -e "s|#BINDIR#|usr/bin|g" \ -e "s|#SYSCONFDIR#|etc|g" \ -e "s|#MANDIR#|usr/share/man/man1|g" \ -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \ -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \ -e "s|#ALTPRIORITY#|1000|g" \ -e "s|#PXALTPRIORITY#|900|g" \ -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \ -e "s|#DATADIR#|usr/share|g" \ -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \ -e "s|#PKGDATADIR#|usr/share/fglrx|g" \ -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \ -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \ -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \ -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \ -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \ -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \ -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \ -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \ -e "s|#DRIVERNAME#|fglrx|g" \ -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \ -e "s|#DRIVERSRCNAME#||g" \ -e "s|#INCLUDEDIR#|usr/include|g" \ -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \ -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \ -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \ -e "s|#PXDIR#|usr/lib/pxpress|g" \ -e "s|#PXDIR32#|usr/lib32/pxpress|g" \ -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \ -e "s|#PXDIRNAME#|pxpress|g" \ -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \ -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \ -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \ -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \ -e "s|#CVERSION#|9.012|g" \ -e "s|#SRCXARCH#|xpic_64a|g" \ -e "s|#SRCARCH#|x86_64|g" \ -e "s|#SRCOTHERARCH#|x86|g" \ -e "s|#SRCLIBDIR#|lib64|g" \ -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \ -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \ debian/$i.in > debian/$i; \ done # remove exec bit on everything find arch \ etc \ lib \ module \ usr \ xpic_64a -type f | xargs chmod -x find: `module': No such file or directory # set executable on user apps find arch/x86_64/usr/sbin \ arch/x86_64/usr/X11R6/bin \ usr/sbin/ -type f | xargs chmod a+x # set exec bit on scripts find lib etc debian -name "*.sh" -type f | xargs chmod +x # set the permissions on the pxpress scripts chmod 744 debian/pxpress/switch* dh build dh_testdir dh_auto_configure dh_auto_build dh_auto_test dh build debian/rules binary # refresh copyright file cat debian/copyright_stub_0 > debian/copyright cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright cat debian/copyright_stub_1 >> debian/copyright #Steps that we can't easily represent in debhelper files or .in files yet # Remove any libraries that may be caught by shell expansion find . -name libGLE* | xargs rm -f find . -name libEGL* | xargs rm -f dh_install -pfglrx "arch/x86/usr/X11R6/lib/libAMD*.so*" "usr/lib32/fglrx" dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.*" "usr/lib32/fglrx" dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*" "usr/lib32/fglrx" dh_installdirs -pfglrx "usr/lib32/fglrx" dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri" "usr/lib32/fglrx" dh_install -pfglrx "arch/x86/usr/lib/*.so*" "usr/lib32/fglrx" # Install the QT libraries dh_install -pfglrx "arch/x86_64/usr/share/ati/lib64" "usr/share/ati" for i in \ debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \ debian/fglrx/usr/lib32/fglrx/*libGL.so.* \ ; do execstack -q $i; execstack -c $i; done /bin/sh: 4: execstack: not found /bin/sh: 4: execstack: not found /bin/sh: 4: execstack: not found /bin/sh: 4: execstack: not found make: *** [binary-arch] Error 127 dpkg-buildpackage: error: debian/rules binary gave error exit status 2 ./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found dpkg-buildpackage: source package fglrx-installer dpkg-buildpackage: source version 2:9.012-0ubuntu1 dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html> dpkg-source --before-build fglrx.AEKQ17 dpkg-buildpackage: host architecture amd64 debian/rules build #Create important strings for i in 10fglrx \ dkms.conf \ fglrx.install \ fglrx-dev.install \ fglrx-dev.links \ fglrx-amdcccle.install \ fglrx.grub-gfxpayload \ fglrx.dirs \ fglrx.links \ fglrx.postinst \ fglrx.postrm \ fglrx.preinst \ fglrx.prerm \ overrides/fglrx; do \ sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \ -e "s|#LIBDIR#|usr/lib|g" \ -e "s|#LIBDIR32#|usr/lib32|g" \ -e "s|#BINDIR#|usr/bin|g" \ -e "s|#SYSCONFDIR#|etc|g" \ -e "s|#MANDIR#|usr/share/man/man1|g" \ -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \ -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \ -e "s|#ALTPRIORITY#|1000|g" \ -e "s|#PXALTPRIORITY#|900|g" \ -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \ -e "s|#DATADIR#|usr/share|g" \ -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \ -e "s|#PKGDATADIR#|usr/share/fglrx|g" \ -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \ -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \ -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \ -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \ -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \ -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \ -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \ -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \ -e "s|#DRIVERNAME#|fglrx|g" \ -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \ -e "s|#DRIVERSRCNAME#||g" \ -e "s|#INCLUDEDIR#|usr/include|g" \ -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \ -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \ -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \ -e "s|#PXDIR#|usr/lib/pxpress|g" \ -e "s|#PXDIR32#|usr/lib32/pxpress|g" \ -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \ -e "s|#PXDIRNAME#|pxpress|g" \ -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \ -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \ -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \ -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \ -e "s|#CVERSION#|9.012|g" \ -e "s|#SRCXARCH#|xpic_64a|g" \ -e "s|#SRCARCH#|x86_64|g" \ -e "s|#SRCOTHERARCH#|x86|g" \ -e "s|#SRCLIBDIR#|lib64|g" \ -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \ -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \ debian/$i.in > debian/$i; \ done # remove exec bit on everything find arch \ etc \ lib \ module \ usr \ xpic_64a -type f | xargs chmod -x find: `module': No such file or directory # set executable on user apps find arch/x86_64/usr/sbin \ arch/x86_64/usr/X11R6/bin \ usr/sbin/ -type f | xargs chmod a+x # set exec bit on scripts find lib etc debian -name "*.sh" -type f | xargs chmod +x # set the permissions on the pxpress scripts chmod 744 debian/pxpress/switch* dh build dh_testdir dh_auto_configure dh_auto_build dh_auto_test dh build debian/rules binary # refresh copyright file cat debian/copyright_stub_0 > debian/copyright cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright cat debian/copyright_stub_1 >> debian/copyright #Steps that we can't easily represent in debhelper files or .in files yet # Remove any libraries that may be caught by shell expansion find . -name libGLE* | xargs rm -f find . -name libEGL* | xargs rm -f dh_install -pfglrx "arch/x86/usr/X11R6/lib/libAMD*.so*" "usr/lib32/fglrx" dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.*" "usr/lib32/fglrx" dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*" "usr/lib32/fglrx" dh_installdirs -pfglrx "usr/lib32/fglrx" dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri" "usr/lib32/fglrx" dh_install -pfglrx "arch/x86/usr/lib/*.so*" "usr/lib32/fglrx" # Install the QT libraries dh_install -pfglrx "arch/x86_64/usr/share/ati/lib64" "usr/share/ati" for i in \ debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \ debian/fglrx/usr/lib32/fglrx/*libGL.so.* \ ; do execstack -q $i; execstack -c $i; done /bin/sh: 4: execstack: not found /bin/sh: 4: execstack: not found /bin/sh: 4: execstack: not found /bin/sh: 4: execstack: not found make: *** [binary-arch] Error 127 dpkg-buildpackage: error: debian/rules binary gave error exit status 2 [Error] Generate Package - error generating package : Ubuntu/quantal

---

### Post by Muty-bg on 2013-02-21
Sorry my bad. You'll have to install some dependencies first:

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install ia32-libs
```

and if you are running a 64 bit system also:
```
sudo apt-get install ia32-libs-multiarch i386 lib32gcc1 libc6-i386
```

source: 
[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx)

That should do it.

---

### Post by QIII on 2013-02-21
I'm afraid it won't be as easy as that with Intel/ATI hybrid graphics.  On my cell right now and can't insert links, but I'll get back to this.  Don't do anything just yet.

---

### Post by ofclouds on 2013-02-21
i got it to  install the devs after those dependencies, but yeah... it was the same effect the Ubuntu Additional Software isntalls' had: no ui, game wouldn't even run.  thanks for trying, though.

@QIII, okay, cool. no rush.  Thanks in advance for the help.

---

### Post by QIII on 2013-02-21
OK.

Have a look at [this thread](http://ubuntuforums.org/showthread.php?t=1930450).

Remember that anything you do based on this is [I]at your own  risk!

[/I]I would back up anything you don't want to lose before you launch into this.

Best of luck!

---

### Post by JiuJitsu500 on 2013-02-21
Just so you know, Sandy Bridge was the architecture name they used before the newer chips released mid-2012 called Ivy Bridge... still amd64-based and all that, but the newer chips are more effiecient, faster, all that jazz. All of them have integrated graphics.

Sandy just means you have a Gen 2 Core i chip, Ivy is Gen 3 :)

I'm also drunk and didn't read all of those posts, but read the OP saying "i don't know why it says sandy bridge."

:guitar:

Try adding the x-swat PPA and udating your drivers. ATI drivers suck in linux compared to NVidia, which is unfortunate because I like Radeon better - but still, the x-swat dudes keep that up pretty damn well.

I'm done talking now before I get into trouble :)

---


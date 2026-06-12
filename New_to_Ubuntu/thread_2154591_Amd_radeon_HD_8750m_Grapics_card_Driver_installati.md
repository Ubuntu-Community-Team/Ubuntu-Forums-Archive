---
title: "Amd radeon ?HD 8750m? Grapics card Driver installation fail + NETGEAR WNA3100"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by knagieknagger on 2013-06-15
Hello,

I installed Ubuntu studio 2 days ago because i wanted to record videos for minecraft.
So i installed minecraft with some trouble but it works now :).

I got 2 problems at the moment:

**Problem 1. **

for:

lspci | grep VGA 

I get:

VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV670 [Radeon HD 3870] 

  All the mobs are missing some parts of their body and with shaders mod the screen goes completley black with only the inventory and sometimes weird colored blocks and tools and stuff so i thought it was my grapics card who wasnt correctly installed.

So i tryed to install the latest drivers from amd for linux 




Then i get this error message when i try to install my drivers for my graphics card:

```
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:12.104-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.UOWcLC
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-dev.links \
             fglrx-amdcccle.install \
             fglrx.grub-gfxpayload \
             fglrx.dirs \
             fglrx.links \
             fglrx.postinst \
             fglrx.postrm \
             fglrx.preinst \
             fglrx.prerm \
             overrides/fglrx; do \
        sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#LIBDIR#|usr/lib|g" \
            -e "s|#LIBDIR32#|usr/lib32|g" \
            -e "s|#BINDIR#|usr/bin|g" \
            -e "s|#SYSCONFDIR#|etc|g" \
            -e "s|#MANDIR#|usr/share/man/man1|g" \
            -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
            -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
            -e "s|#ALTPRIORITY#|1000|g" \
            -e "s|#PXALTPRIORITY#|900|g" \
            -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
            -e "s|#DATADIR#|usr/share|g" \
            -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
            -e "s|#PKGDATADIR#|usr/share/fglrx|g" \
            -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
            -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
            -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \
            -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
            -e "s|#DRIVERNAME#|fglrx|g" \
            -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
            -e "s|#DRIVERSRCNAME#||g" \
            -e "s|#INCLUDEDIR#|usr/include|g" \
            -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
            -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
            -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#PXDIR#|usr/lib/pxpress|g" \
            -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
            -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
            -e "s|#PXDIRNAME#|pxpress|g" \
            -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
            -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
            -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
            -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
            -e "s|#CVERSION#|12.104|g" \
            -e "s|#SRCXARCH#|xpic_64a|g" \
            -e "s|#SRCARCH#|x86_64|g" \
            -e "s|#SRCOTHERARCH#|x86|g" \
            -e "s|#SRCLIBDIR#|lib64|g" \
            -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
            -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
dh build
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib64" "usr/share/ati"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/*libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
[Error] Generate Package - error generating package : Ubuntu/raring
```

The package i tryed to install is:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx ]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

and then this version not the beta!

**AMD Catalyst&#8482; 13.4 Proprietary Linux x86 Display Driver**

I got:

Ubuntu studio 13.04 on one 320GB HDD and Windows on my 500GB HDD
i will try to get a list of all the parts i got in my PC but this will take some time!!!

i will put the list also here (or if asked in another post)

**Problem 2.**

i cant get my NETGEAR WNA3100 to work with ubuntu studio

(i am currently connected with a network cable running through the complete house to my router)

i searched on the forums and tryed several different solutions but none of them worked :(

maybe someone can give me a fresh start! 

i ran this command:

lspci | grep Wireless

and got this:



"Nothing"

Niels

---

### Post by Mark Phelps on 2013-06-15
I know you are new, but you would do better to keep each thread to a single problem.  You will get better responses that way.

As to the video problem, the lspci shows it being a 3870 -- and AMD dropped restricted driver support for that card last summer.  So, unless you're running Ubuntu 11.10, or the original version of 12.04, you can't install any drivers from AMD.  The only drivers that will work now are the open-source, and they are installed by default.

As to the netgear problem, you would do better to post a new thread in the Networking section.

---

### Post by knagieknagger on 2013-06-15
ok thanks for the respons i will get to the network problems section with my problem about netgear and its pitty they arent supported anymore so then i will wait for my new graphics card :)

thanks again

EDIT:
how can i set this topic to solved or something like that?

---


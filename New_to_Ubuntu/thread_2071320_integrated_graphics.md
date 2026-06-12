---
title: "integrated graphics"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by TooFreppaT on 2012-10-15
I have two computers, one is intel and the other is amd

both have integrated graphics

intel already had ubuntu installed and the amd computer is new

all I did was take the hdd from the intel and put it into the amd

now I cannot use unity and my monitor is unkown (low resolutions)


...I thought I was upgrading the graphics

---

### Post by TooFreppaT on 2012-10-15
I already tried this [http://grenage.com/xorg.html](http://grenage.com/xorg.html) (from [http://linux.bigresource.com/Ubuntu-11-04-display-resolution-Detected-Unknown-Monitor--fEZNsp4qj.html](http://linux.bigresource.com/Ubuntu-11-04-display-resolution-Detected-Unknown-Monitor--fEZNsp4qj.html))

but I get to:
grenage@ublt:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.old
and I find out there's no xorg.conf file in there ...but there is /etc/X11/

---

### Post by TooFreppaT on 2012-10-15
went to Additional Drivers

clicked on Activate button

...."Downloading and installing driver..."

...need to restart computer, ibb

okay...that worked! :)
and it looks way better than before!

...even managed to fix my sound problem before creating another thread (jack wasn't in all the way in properly)

---

### Post by Cheesemill on 2012-10-15
Have you tried installing the Restricted Drivers for your new GPU?

---

### Post by TooFreppaT on 2012-10-15
> **Cheesemill said:**
> Have you tried installing the Restricted Drivers for your new GPU?

...how do I do that?

also, I now have this annoying transparent picture in the bottom left corner:
AMD[COLOR=SeaGreen]^
Unsupported
hardware

[COLOR=Black]it's in a black box... and the AMD part is in white
the [/COLOR][/COLOR][COLOR=SeaGreen][COLOR=Black][COLOR=SeaGreen]^[/COLOR] is a green AMD logo

I'm doing a googlesearch ...an auto (one of "those" things) came up with "... watermark" - that's exactly what it's like

...when I lockscreen, only the green-coloured part is shown (everything else just simply dissappears into nothingness)

JUST CHECKED - NOW I HAVE XORG.CONF!?! :D :D :D :D :D

AND UNITY IS WORKING...wtf, I didn't even log in with...oh wait a sec, I forgot to log into Gnome manually [/COLOR][/COLOR]](*,)

---

### Post by Cheesemill on 2012-10-15
> **TooFreppaT said:**
> ...how do I do that
You've just done it. Restricted Drivers and Additional Drivers are the same thing.

---

### Post by TooFreppaT on 2012-10-15
but what do I do with a .run file?

I downloaded "[**AMD Catalyst&#8482; 12.8 Proprietary Linux x86 Display Driver**]("http://www2.ati.com/drivers/linux/amd-driver-installer-12-8-x86.x86_64.zip")" from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

(got there via [http://askubuntu.com/questions/25519/how-to-remove-amd-unsupported-hardware-without-reinstalling-the-driver](http://askubuntu.com/questions/25519/how-to-remove-amd-unsupported-hardware-without-reinstalling-the-driver) - I think third answer down)

...trying to get rid of the watermark

*from [http://ubuntuforums.org/showthread.php?t=2046540](http://ubuntuforums.org/showthread.php?t=2046540) I learned that "The watermark is just to tell you that the version of the driver you have installed is too old to support your card."

and I don't wanna do like these guys here @ [http://www.ubunturoot.com/2012/07/remove-amdati-drivers-testing-only.html](http://www.ubunturoot.com/2012/07/remove-amdati-drivers-testing-only.html)
I don't wanna just get rid of it like that - I want to actually solve it (the key principle problem here)

---

### Post by audiomick on 2012-10-15
> **TooFreppaT said:**
> but what do I do with a .run file?

Try this

[https://help.ubuntu.com/community/InstallingRunPackage]("https://help.ubuntu.com/community/InstallingRunPackage")

Basically, downloads get stored as a normal file, and you have to mark them as being an executable if you want them to run as such.

---

### Post by TooFreppaT on 2012-10-15
> **audiomick said:**
> Try this

[https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

Basically, downloads get stored as a normal file, and you have to mark them as being an executable if you want them to run as such.

thanks! that worked :)
but now I have another problem...
when I run it, it give two options"[INDENT]Install Driver 8.982 on X.Org 6.9 or later 64-bit
Generate Distribution Specifice Driver Package
[/INDENT]when I click the "Install Driver" one, I get this message:> A previous install of the fglrx driver has
been detected. Please uninstall the older
version before installing this version.
Optionally, run the installer with --force
option to overwrite the existing driver.
Forcing install is not recommended.
See /usr/share/ati/fglrx-install.log for
more details.when I click the "Generate Distro" one, I get...
it says something about "aticonfig" but cannot find it in the specified directory
and it says there was errors
this is from /usr/share/ati/fglrx-install.log (there was no generated file there, that wasn't already there before):```
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 399: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.982-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.ler4Ds
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
            -e "s|#XORGEXTRA#|usr/lib/xorg/extra-modules|g" \
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
            -e "s|#CVERSION#|8.982|g" \
            -e "s|#SRCXARCH#|xpic_64a|g" \
            -e "s|#SRCARCH#|x86_64|g" \
            -e "s|#SRCLIBDIR#|lib64|g" \
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
make: dh: Command not found
make: *** [build] Error 127
dpkg-buildpackage: error: debian/rules build gave error exit status 2
[Error] Generate Package - error generating package : Ubuntu/natty
```I'm only guessing that the first one would be easiest...how do I uninstall the older version?

[http://debianhelp](http://debianhelp) .wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/
[http://ubuntuforums.org/showthread.php?t=1758755](http://ubuntuforums.org/showthread.php?t=1758755)
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Switching_drivers_on_system_with_hybrid_graphics]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Switching_drivers_on_system_with_hybrid_graphics")
[http://ubuntuforums.org/showthread.php?t=1959059](http://ubuntuforums.org/showthread.php?t=1959059)

I can't play any videos - only get sound with black screen

---

### Post by TooFreppaT on 2012-10-16
I AM SOOO PISSED OFF!!!!!

how many times do I have to read all these instrutions over and over again (for every problem - including this thread)

oh, it's fine that the instructions will successfully accomplish what they are intended, sure

<snip>
who, in their right mind, would give instructions without telling you when to restart your pc?

I've been scouring the internet to fix my problem and every instructions I come across is basically the same old thing (but just a little different, so that you think that it might work)

I've been doing the same thing over and over again for so many hours

until I finally go to turnoff my pc and there it is - it saidsomething about restarting for updates

so then I turn back on and see I'm back to where I started (no driverless)

and then I run the AMD driver (the .run file) and it actually says to restart the pc when finished (see, AMD is professional and gives proper instructions)

NOW! all my problems are finally solve

---


---
title: "Problem Installing Google Earth"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by bigtel on 2011-11-27
I am trying to install Google Earth (among other things) in 11.10 and I keep getting the following error message. I have downloaded the deb file and I am installing it with the software center.

here is the output....

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 177203 files and directories currently installed.)

Unpacking google-earth-stable (from .../google-earth-stable_current_i386.deb) ...

xz: (stdin): Compressed data is corrupt

dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe

dpkg-deb: error: subprocess <decompress> returned error exit status 1

dpkg: error processing /home/terry/Downloads/google-earth-stable_current_i386.deb (--install):

 short read on buffer copy for backend dpkg-deb during `./opt/google/earth/free/libQtGui.so.4'

Errors were encountered while processing:

 /home/terry/Downloads/google-earth-stable_current_i386.deb



Has anyone any idea why I am getting this message and what I can do about it?

---

### Post by BC59 on 2011-11-27
Did you install first the package?

```
sudo apt-get install lsb-core
```

---

### Post by beew on 2011-11-27
I think you need to install the package lsb-core first,--at least for Natty,-- and then to install the .deb, open a terminal and type
```
 sudo dpkg -i google-earth-stable_current_i386.deb
```I am assuming you have the .deb file in your home directory, otherwise cd into wherever it is first, so if it is on the desktop, run the following first (note the capital D)
```
cd Deskop
```The Software Center and gdebi used to give that kind of errors when I installed GE on 11.10. But gdebi seems to work fine now,don't know about the SC, maybe it still doesn't work. It is a waste of space anyway. Synaptic is a much better package manager and for installing .debs you can either use the command line or use gdebi for one click install
```

sudo apt-get install synaptic gdebi
```

---

### Post by BC59 on 2011-11-27
Another method could be 

First install lsb-core

```
sudo apt-get install lsb-core
```

Then install the googleearth package

```
sudo apt-get install googleearth-package
```

You will see errors but ignore them and after run to download the package:

```
sudo make-googleearth-package --force
```

Afterwords install the package downloaded

```
sudo dpkg -i [COLOR="Blue"]the name of the package or write google and hit tab to autocomplete[/COLOR]
```

If you have problems with the fonts:

```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by bigtel on 2011-11-27
I don;t think it's my day..! I am now getting - 

terry@terry-A7N8X-E:~/Downloads$ sudo dpkg -i google-earth-stable_current_i386.deb
(Reading database ... 177226 files and directories currently installed.)
Unpacking google-earth-stable (from google-earth-stable_current_i386.deb) ...
xz: (stdin): Compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 1
dpkg: error processing google-earth-stable_current_i386.deb (--install):
 short read on buffer copy for backend dpkg-deb during `./opt/google/earth/free/libQtWebKit.so.4'
Errors were encountered while processing:
 google-earth-stable_current_i386.deb
terry@terry-A7N8X-E:~/Downloads$ 


I have tried deleting and then re-downloading the package but I get the same message. Is it me, or are things just that more complicated today..??

---

### Post by BC59 on 2011-11-27
Ok write now

```
sudo dpkg --configure -a
```

and then

```
sudo apt-get -f install
```

---

### Post by bigtel on 2011-11-27
OK completed that.

```
terry@terry-A7N8X-E:~$ sudo dpkg --configure -a
[sudo] password for terry: 
terry@terry-A7N8X-E:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
terry@terry-A7N8X-E:~$ 

```

---

### Post by BC59 on 2011-11-27
Well everything looks ok.

Just try to start again according to my post #4 above.

---

### Post by bigtel on 2011-11-27
Right - first of all thanks for your help so far - 

I have now found Google earth in my 'Dash Home' launcher, but when I click on it nothing happens..!! 


Here is the code from the last install attempt

```
terry@terry-A7N8X-E:~$ sudo apt-get install lsb-core
[sudo] password for terry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lsb-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
terry@terry-A7N8X-E:~$ sudo apt-get install googleearth-package
Reading package lists... Done
Building dependency tree       
Reading state information... Done
googleearth-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
terry@terry-A7N8X-E:~$ sudo make-googleearth-package --force
cat: /etc/mailname: No such file or directory
--2011-11-27 18:55:11--  http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
Resolving dl.google.com... 209.85.147.136, 209.85.147.190, 209.85.147.93, ...
Connecting to dl.google.com|209.85.147.136|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33688483 (32M) [application/octet-stream]
Saving to: `GoogleEarthLinux.bin'

100%[======================================>] 33,688,483  1.15M/s   in 29s     

2011-11-27 18:55:39 (1.12 MB/s) - `GoogleEarthLinux.bin' saved [33688483/33688483]

Google Earth for GNU/Linux 6.0.3.2197
Supported Google Earth version: 6.0.3.2197
./
./googleearth.xpm
./desktop_icons/
./desktop_icons/pro/
./desktop_icons/pro/product_logo_128.png
./desktop_icons/pro/product_logo_22.png
./desktop_icons/pro/product_logo_64.png
./desktop_icons/pro/product_logo_16.png
./desktop_icons/pro/product_logo_256.png
./desktop_icons/pro/product_logo_32.xpm
./desktop_icons/pro/product_logo_24.png
./desktop_icons/pro/product_logo_48.png
./desktop_icons/pro/product_logo_32.png
./desktop_icons/ec/
./desktop_icons/ec/product_logo_128.png
./desktop_icons/ec/product_logo_22.png
./desktop_icons/ec/product_logo_64.png
./desktop_icons/ec/product_logo_16.png
./desktop_icons/ec/product_logo_256.png
./desktop_icons/ec/product_logo_32.xpm
./desktop_icons/ec/product_logo_24.png
./desktop_icons/ec/product_logo_48.png
./desktop_icons/ec/product_logo_32.png
./desktop_icons/consumer/
./desktop_icons/consumer/product_logo_128.png
./desktop_icons/consumer/product_logo_22.png
./desktop_icons/consumer/product_logo_64.png
./desktop_icons/consumer/product_logo_16.png
./desktop_icons/consumer/product_logo_256.png
./desktop_icons/consumer/product_logo_32.xpm
./desktop_icons/consumer/product_logo_24.png
./desktop_icons/consumer/product_logo_48.png
./desktop_icons/consumer/product_logo_32.png
./setup.sh
./googleearth-linux-x86.tar

bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
tar: Unexpected EOF in archive
tar: rmtlseek not stopped at a record boundary
tar: Error is not recoverable: exiting now
tar: /home/terry/googleearth-tmp/googleearth-data.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
cp: cannot stat `/home/terry/googleearth-tmp/README*': No such file or directory
objdump: ../usr/lib/googleearth/libevll.so: File truncated
Checking shlib deps: libIGUtils.so
Checking shlib deps: libbase.so
dpkg-shlibdeps: warning: couldn't find library libport.so needed by ../usr/lib/googleearth/libbase.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
Checking shlib deps: libalchemyext.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGAttrs.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'
Checking shlib deps: libcurl.so.4
Checking shlib deps: libcollada.so
dpkg-shlibdeps: warning: couldn't find library libmath.so needed by ../usr/lib/googleearth/libcollada.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libge_net.so needed by ../usr/lib/googleearth/libcollada.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libport.so needed by ../usr/lib/googleearth/libcollada.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGExportCommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGOpt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGAttrs.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libalchemyext.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGSg.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'
Checking shlib deps: libcommon_gui.so
dpkg-shlibdeps: warning: couldn't find library libmath.so needed by ../usr/lib/googleearth/libcommon_gui.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libGLU.so.1
Checking shlib deps: libQtGui.so.4
Checking shlib deps: libIGExportCommon.so
Checking shlib deps: libIGOpt.so
Checking shlib deps: libQtCore.so.4
Checking shlib deps: libcommon_platform.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libevll.so
objdump: ../usr/lib/googleearth/libevll.so: File truncated
Checking shlib deps: libIGMath.so
Checking shlib deps: libcommon_webbrowser.so
dpkg-shlibdeps: warning: couldn't find library libge_net.so needed by ../usr/lib/googleearth/libcommon_webbrowser.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libgeobase.so needed by ../usr/lib/googleearth/libcommon_webbrowser.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libgeobaseutils.so needed by ../usr/lib/googleearth/libcommon_webbrowser.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libport.so needed by ../usr/lib/googleearth/libcommon_webbrowser.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library librender.so needed by ../usr/lib/googleearth/libcommon_webbrowser.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
Checking shlib deps: libQtNetwork.so.4
Checking shlib deps: libcomponentframework.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libIGAttrs.so
Checking shlib deps: libIGCore.so
Checking shlib deps: libbasicingest.so
dpkg-shlibdeps: warning: couldn't find library libfusioncommon.so needed by ../usr/lib/googleearth/libbasicingest.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libge_net.so needed by ../usr/lib/googleearth/libbasicingest.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libgeobase.so needed by ../usr/lib/googleearth/libbasicingest.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libgeobaseutils.so needed by ../usr/lib/googleearth/libbasicingest.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libmath.so needed by ../usr/lib/googleearth/libbasicingest.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libmoduleframework.so needed by ../usr/lib/googleearth/libbasicingest.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libport.so needed by ../usr/lib/googleearth/libbasicingest.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
Checking shlib deps: libcommon.so
dpkg-shlibdeps: warning: couldn't find library libfusioncommon.so needed by ../usr/lib/googleearth/libcommon.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libge_net.so needed by ../usr/lib/googleearth/libcommon.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libgeobase.so needed by ../usr/lib/googleearth/libcommon.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libgeobaseutils.so needed by ../usr/lib/googleearth/libcommon.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libmath.so needed by ../usr/lib/googleearth/libcommon.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libmoduleframework.so needed by ../usr/lib/googleearth/libcommon.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libport.so needed by ../usr/lib/googleearth/libcommon.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_platform.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
Checking shlib deps: libapiloader.so
dpkg-shlibdeps: warning: couldn't find library libport.so needed by ../usr/lib/googleearth/libapiloader.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
Checking shlib deps: libIGSg.so
Checking shlib deps: libauth.so
dpkg-shlibdeps: warning: couldn't find library libge_net.so needed by ../usr/lib/googleearth/libauth.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libgeobase.so needed by ../usr/lib/googleearth/libauth.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libmath.so needed by ../usr/lib/googleearth/libauth.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libmoduleframework.so needed by ../usr/lib/googleearth/libauth.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libreporting.so needed by ../usr/lib/googleearth/libauth.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libport.so needed by ../usr/lib/googleearth/libauth.so (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_webbrowser.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
Checking shlib deps: libIGGfx.so
Checking shlib deps: libQtWebKit.so.4
Package: googleearth
Version: 6.0.3.2197+0.6.0-1
Section: non-free/science
Priority: optional
Maintainer:  <root@terry-A7N8X-E>
Architecture: i386
Depends: ttf-dejavu | ttf-bitstream-vera | msttcorefonts, lsb-core, libqtcore4, libgl1-mesa-glx, libc6 (>= 2.1.3), libc6 (>= 2.3), libc6 (>= 2.3.2), libc6 (>= 2.3.6-6~), libc6 (>= 2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libice6 (>= 1:1.0.0), libsm6, libstdc++6 (>= 4.1.1), libx11-6, libxext6, libxrender1, zlib1g (>= 1:1.1.4) 
Suggests: 
Description: Google Earth, a 3D map/planet viewer
 Package built with googleearth-package.
chmod: cannot access `usr/lib/googleearth/googleearth-bin': No such file or directory
dpkg-deb: building package `googleearth' in `./googleearth_6.0.3.2197+0.6.0-1_i386.deb'.
Success!
You can now install the package with e.g. sudo dpkg -i <package>.deb
terry@terry-A7N8X-E:~$ sudo dpkg -i googleearth_6.0.3.2197+0.6.0-1_i386.deb 
(Reading database ... 177312 files and directories currently installed.)
Preparing to replace googleearth 6.0.3.2197+0.6.0-1 (using googleearth_6.0.3.2197+0.6.0-1_i386.deb) ...
Unpacking replacement googleearth ...
Setting up googleearth (6.0.3.2197+0.6.0-1) ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
terry@terry-A7N8X-E:~$ 

```

---

### Post by BC59 on 2011-11-27
Well as I assume you have a 64bit Ubuntu and in that case you have to execute:

```
sudo apt-get install googleearth-package ia32-libs
cd && make-googleearth-package --force
```

and then

```
sudo dpkg -i the name of the package or write google and hit tab to autocomplete
```

---

### Post by bigtel on 2011-11-28
I have a 32 bit system. Is there a corresponding install code for that?

---

### Post by beew on 2011-11-28
Not sure why it doesn't work for you. I just installed the 32 bit .deb downloaded from GE on 11.10 and it went through without a hitch (using gdebi, but dpkg -i would have worked too, of course) Again you need to install lsb-core first.

You don't really need to make your own ge .deb (that is what you do with the make-googleearth-package). I think may be the .deb that you created this way have some problems, that's why it installed but didn't show anything other than a launcher. Just completely uninstall it and try to download a fresh .deb from ge and install it. Do a reboot too, just in case.

---

### Post by I2k4 on 2011-11-30
My "for dummies" (that's me) newbie experience:  I used Firefox to go the Google Earth site and Firefox has a dialog box that handles the .deb package.  Just don't close any windows until it's done. For whatever reason, only Firefox seems to have the slick dialog handling of .deb packages, Chrome will only download it and let you go nuts by yourself.

---

### Post by okos on 2012-05-06
> **BC59 said:**
> Another method could be 

First install lsb-core

```
sudo apt-get install lsb-core
```

Then install the googleearth package

```
sudo apt-get install googleearth-package
```

You will see errors but ignore them and after run to download the package:

```
sudo make-googleearth-package --force
```

Afterwords install the package downloaded

```
sudo dpkg -i [COLOR="Blue"]the name of the package or write google and hit tab to autocomplete[/COLOR]
```

If you have problems with the fonts:

```
sudo apt-get install ttf-mscorefonts-installer
```

Hello, I am still using Lucid 10.04 LTS. BC59's suggestion worked for me. I just want to add the following because it solved my dependency errors:
> sudo apt-get -f install

---


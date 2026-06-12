---
title: "HOWTO: Compile wine in amd64"
date: 2006-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by psychosushi on 2006-04-29
This howto will tell you how to compile wine in an Ubuntu AMD64 Dapper Drake system. It worked for me. Let me know if it doesn't for you. It might work in Breezy too, but I'm not sure.

First add the universe repository to your /etc/apt/sources.list file, if you have not already.

```

sudo gedit /etc/apt/sources.list

```

use kate instead of gedit if you use kde. Add the following line to the end of the script.

```

deb http://au.archive.ubuntu.com/ubuntu dapper universe

```

Obviously change the country if necessary.

Then type into a terminal:

```

sudo apt-get build-dep wine
sudo apt-get install build-essential gcc-3.4 libc6-i386 libc6-dev-i386 ia32-libs

```

now make sure that your libraries will be found (thanks to jontxo for this tip)
If there are any problems with the location of any library the best thing to do to solve it is to edit, or to create if it doesn't already exist, the file /etc/ld.so.conf. 

```

sudo gedit /etc/ld.so.conf

```

Use kate if you use Kubuntu. There you can tell ubuntu the directories where it can search for libraries. This is my file:
 
 /usr/X11R6/lib32
 /usr/lib32
 /lib32/
 
after editing this file you only have to use the comand sudo ldconfig.

now get the wine source package:

```

mkdir ~/tmp
cd ~/tmp
wget -c http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.21~winehq0~ubuntu~6.06.orig.tar.gz
tar xvzf wine_0.9.21~winehq0~ubuntu~6.06.orig.tar.gz

```

Now you have to install the 32-bit dependencies of wine.

```

wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34-dev_3.4.1a-1ubuntu1_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34_3.4.1a-1ubuntu1_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf2_1.4pre.20030402-1.1ubuntu1_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf-dev_1.4pre.20030402-1.1ubuntu1_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libx11/libx11-dev_6.2.1+cvs.20050722-8_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext6_1.0.0-0ubuntu4_i386.deb; wget -c http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext-dev_1.0.0-0ubuntu4_i386.deb
for i in *.deb; do dpkg -x "$i" `basename "$i" .deb`; done
rm -Rf *.deb
sudo -i
cd /home/<username>/tmp                 # replace <username> with your username, obviously ;)
cp -r libicu34_*/usr/lib/*.so.34.1 /usr/lib32
for i in /usr/lib32/libicu*.so.34.1; do ln -fs "$i" /usr/lib32/`basename "$i" .1`; done
for i in /usr/lib32/libicu*.so.34.1; do ln -fs "$i" /usr/lib32/`basename "$i" .34.1`; done
cp -r libicu34-*/usr/lib/*.a /usr/lib32
cp -r libicu34-*/usr/lib/icu /usr/lib32
cp -r libttf2_*/usr/lib/*.so.2.4.0 /usr/lib32
ln -fs /usr/lib32/libttf.so.2.4.0 libttf.so.2
ln -fs /usr/lib32/libttf.so.2.4.0 libttf.so
cp -r libttf-dev_*/usr/lib/*.[al]* /usr/lib32
cp -r libx11-dev*/usr/lib/libX11.a /usr/lib32; cp -r libx11-dev*/usr/lib/pkgconfig/* /usr/lib32/pkgconfig
ln -fs /usr/lib32/libX11.so.6.2.0 /usr/lib32/libX11.so
cp -r libxext6_*/usr/lib/libXext.so.6.4.0 /usr/lib32
ln -fs /usr/lib32/libXext.so.6.4.0 /usr/lib32/libXext.so.6
ln -fs /usr/lib32/libXext.so.6.4.0 /usr/lib32/libXext.so
cp -r libxext-dev*/usr/lib/*.a /usr/lib32
cp -r libxext-dev*/usr/lib/pkgconfig/* /usr/lib32/pkgconfig/
ldconfig
exit

```

Now we actually have to compile wine. It took about half an hour on my AMD Athlon64 3000+, so it will take a while.

```

cd wine_0.9.21~winehq0~ubuntu~6.06.orig
CC="gcc-3.4 -m32" ./configure
make depend && make
sudo make install

```

Now you have the latest wine installed in your amd64 system. Use the guide at [http://ubuntuforums.org/showthread.php?t=29996&highlight=winecvs](http://ubuntuforums.org/showthread.php?t=29996&highlight=winecvs) from step four to configure wine properly.

Hope this guide helps somebody.

* I added libc6-i386 to the install list, thanks to jontxo
* I forgot to write install in the apt-get install line, fixed
* updated the version of libxext6 and libxext-dev available (from 1.0.0-0ubuntu3 to 1.0.0-0ubuntu4) and changed cd wine_0.9.12~winehq1.orig.tar.gz to cd wine-0.9.12~winehq1.orig (thanks zakusage)

---

### Post by jontxo on 2006-05-05
Hi psychosushi
I've tried your howto and it althougt i have done all the steps i cannot compile. I can do the configure comand : CC="gcc-3.4 -m32" ./configure 
and the make depend command, but when i try the make command i get the following error

/usr/bin/ld: warning: libdl.so.2, needed by ../port/libwine_port.so, not found (try using -rpath or -rpath-link)
../port/libwine_port.so: referencia a `dlclose@GLIBC_2.0' not defined
../port/libwine_port.so: referencia a `dlerror@GLIBC_2.0' not defined
../port/libwine_port.so: referencia a `dlopen@GLIBC_2.1' not defined
../port/libwine_port.so: referencia a `dlsym@GLIBC_2.0' not defined
collect2: ld returned output state 1
make[1]: *** [wineserver] Error 1
make[1]:leaves directory
`/media/hda2/Programas_Linux/winex/winex/server'make: *** [server/wineserver] Error 2

---

### Post by Jason_25 on 2006-05-05
Does this allow for running 32-bit windows programs?

---

### Post by psychosushi on 2006-05-05
[QUOTE=jontxo]Hi psychosushi
when i try the make command i get the following error

/usr/bin/ld: warning: libdl.so.2, needed by ../port/libwine_port.so, not found (try using -rpath or -rpath-link)
../port/libwine_port.so: referencia a `dlclose@GLIBC_2.0' not defined
../port/libwine_port.so: referencia a `dlerror@GLIBC_2.0' not defined
../port/libwine_port.so: referencia a `dlopen@GLIBC_2.1' not defined
../port/libwine_port.so: referencia a `dlsym@GLIBC_2.0' not defined
collect2: ld returned output state 1
make[1]: *** [wineserver] Error 1
make[1]:leaves directory
`/media/hda2/Programas_Linux/winex/winex/server'make: *** [server/wineserver] Error 2[/QUOTE]
my mistake, you need install the libc6-i386 package as well. I forgot to write it down

---

### Post by psychosushi on 2006-05-05
[QUOTE=Jason_25]Does this allow for running 32-bit windows programs?[/QUOTE]
yes

---

### Post by zakusage on 2006-05-05
Good guide, but a few problems. 

The following line containing the deb downloads needs to be altered to the sub-following.
> wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34-dev_3.4.1a-1ubuntu1_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34-dev_3.4.1a-1ubuntu1_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34_3.4.1a-1ubuntu1_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34_3.4.1a-1ubuntu1_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf2_1.4pre.20030402-1.1ubuntu1_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf2_1.4pre.20030402-1.1ubuntu1_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf-dev_1.4pre.20030402-1.1ubuntu1_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf-dev_1.4pre.20030402-1.1ubuntu1_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libx11/libx11-dev_6.2.1+cvs.20050722-8_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libx11/libx11-dev_6.2.1+cvs.20050722-8_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext6_1.0.0-0ubuntu3_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext6_1.0.0-0ubuntu3_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext-dev_1.0.0-0ubuntu3_i386.deb](http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext-dev_1.0.0-0ubuntu3_i386.deb)
> wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34-dev_3.4.1a-1ubuntu1_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34-dev_3.4.1a-1ubuntu1_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34_3.4.1a-1ubuntu1_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/i/icu/libicu34_3.4.1a-1ubuntu1_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf2_1.4pre.20030402-1.1ubuntu1_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf2_1.4pre.20030402-1.1ubuntu1_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf-dev_1.4pre.20030402-1.1ubuntu1_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/f/freetype1/libttf-dev_1.4pre.20030402-1.1ubuntu1_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libx11/libx11-dev_6.2.1+cvs.20050722-8_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libx11/libx11-dev_6.2.1+cvs.20050722-8_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext6_1.0.0-0ubuntu4_i386.deb;](http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext6_1.0.0-0ubuntu4_i386.deb;) wget -c [http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext-dev_1.0.0-0ubuntu4_i386.deb](http://mirrors.uwa.edu.au/ubuntu/pool/main/libx/libxext/libxext-dev_1.0.0-0ubuntu4_i386.deb)

Also, you post to CD into a tar.gz file, when it should be extracted first. :P

---

### Post by Jason_25 on 2006-05-06
[QUOTE=jontxo]
/usr/bin/ld: warning: libdl.so.2, needed by ../port/libwine_port.so, not found (try using -rpath or -rpath-link)
../port/libwine_port.so: referencia a `dlclose@GLIBC_2.0' not defined
../port/libwine_port.so: referencia a `dlerror@GLIBC_2.0' not defined
../port/libwine_port.so: referencia a `dlopen@GLIBC_2.1' not defined
../port/libwine_port.so: referencia a `dlsym@GLIBC_2.0' not defined
collect2: ld returned output state 1
make[1]: *** [wineserver] Error 1
make[1]:leaves directory
`/media/hda2/Programas_Linux/winex/winex/server'make: *** [server/wineserver] Error 2[/QUOTE]
I am getting these errors compiling too.  That is with libc6-i386 package installed.  Also, libdl.so.2 is in /usr/lib and /usr/lib32.

---

### Post by psychosushi on 2006-05-06
[QUOTE=Jason_25]I am getting these errors compiling too.  That is with libc6-i386 package installed.  Also, libdl.so.2 is in /usr/lib and /usr/lib32.[/QUOTE]
are you trying to install wine or winex? in the passage you quoted it was winex, but this is not a guide for winex

---

### Post by psychosushi on 2006-05-06
[QUOTE=Jason_25]I am getting these errors compiling too.  That is with libc6-i386 package installed.  Also, libdl.so.2 is in /usr/lib and /usr/lib32.[/QUOTE]
for me libdl.so.2 is in /lib32 so it probably is for you as well, so try instead of CC="gcc-3.4 -m32" ./configure type CC="gcc-3.4 -m32" LDFLAGS=-L/lib32/ ./configure

---

### Post by jontxo on 2006-05-06
i've managed to compile wine but after the CC="gcc-3.4 -m32" ./configure command i get the following message:

*** Warning: Freetype or Fontforge is missing.
*** Fonts will not be built. Dialog text may be invisible or unaligned.

Configure finished.  Do 'make depend && make' to compile Wine.

After that i can run make depend && make and the program compiles but when i try to use it with gta san andreas it complains about directx 9 in a message box. The output of the terminal is:
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
epoll_ctl: Operation not permitted

---

### Post by psychosushi on 2006-05-06
[QUOTE=jontxo]i've managed to compile wine but after the CC="gcc-3.4 -m32" ./configure command i get the following message:

*** Warning: Freetype or Fontforge is missing.
*** Fonts will not be built. Dialog text may be invisible or unaligned.

Configure finished.  Do 'make depend && make' to compile Wine.

After that i can run make depend && make and the program compiles but when i try to use it with gta san andreas it complains about directx 9 in a message box. The output of the terminal is:
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
epoll_ctl: Operation not permitted[/QUOTE]
This is normal (the fonts thing). I have been trying to get rid of it for a while with no success.

As for the game, it's probably nothing to do with fonts. Try go to the wine site ([www.winehq.org](www.winehq.org)) and browse to the applications database. It should say there if it works at all.

Sasha

---

### Post by Jason_25 on 2006-05-06
[QUOTE=psychosushi]for me libdl.so.2 is in /lib32 so it probably is for you as well, so try instead of CC="gcc-3.4 -m32" ./configure type CC="gcc-3.4 -m32" LDFLAGS=-L/lib32/ ./configure[/QUOTE]
My error was slightly different because I'm installing wine.  It's the same using even the new command you posted.
```
/usr/bin/ld: warning: libdl.so.2, needed by ../libs/wine/libwine.so, not found (try using -rpath or -rpath-link)
../libs/wine/libwine.so: undefined reference to `dlclose@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dlerror@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dlopen@GLIBC_2.1'
../libs/wine/libwine.so: undefined reference to `dlsym@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dladdr@GLIBC_2.0'
collect2: ld returned 1 exit status
make[1]: *** [wine-glibc] Error 1
make[1]: Leaving directory `/home/jason/Desktop/winetest/wine-0.9.12~winehq1.orig/loader'
make: *** [loader] Error 2

```

---

### Post by psychosushi on 2006-05-06
[QUOTE=Jason_25]My error was slightly different because I'm installing wine.  It's the same using even the new command you posted.
are you using breezy or dapper? IF you are using breezy, then I can't promise this guide will work at all, or unchanged, as I haven't tried it.

---

### Post by turbojugend_gr on 2006-05-06
I have problem when configuring with "CC="gcc-3.4 -m32" ./configure". i get the following error: 
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc-3.4 -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Note that I haven't added the new libc6-i386 package and also the altrernate command CC="gcc-3.4 -m32" ./configure type CC="gcc-3.4 -m32" LDFLAGS=-L/lib32/ ./configure returns me the same error. Please give me a hint. Thanx in advance!

---

### Post by psychosushi on 2006-05-06
[QUOTE=turbojugend_gr]I have problem when configuring with "CC="gcc-3.4 -m32" ./configure". i get the following error: 
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc-3.4 -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Note that I haven't added the new libc6-i386 package and also the altrernate command CC="gcc-3.4 -m32" ./configure type CC="gcc-3.4 -m32" LDFLAGS=-L/lib32/ ./configure returns me the same error. Please give me a hint. Thanx in advance![/QUOTE]
try typing in a terminal: sudo apt-get install libc6-i386 libc6-dev-i386

---

### Post by Davidosky on 2006-05-07
Hi all, i'm a noob in trouble with this howto..
When i type > sudo -i and than > cp -r libicu34_*/usr/lib/*.so.34.1 /usr/lib32 i am getting these error > cp: cannot stat `libicu34_*/usr/lib/*.so.34.1': No such file or directory.

It's the same things with all the "cp" strings...

---

### Post by psychosushi on 2006-05-07
[QUOTE=Davidosky]Hi all, i'm a noob in trouble with this howto..
When i type  and than  i am getting these error .

It's the same things with all the "cp" strings...[/QUOTE]
did you do the for i in *.deb; do dpkg -x "$i" `basename "$i" .deb`; done command and then rm -Rf *.deb?

---

### Post by Rizado on 2006-05-07
Why use an old version of wine? Get the newest one from winehq and the script for dapper that downloads all recommended packages.

---

### Post by psychosushi on 2006-05-07
[QUOTE=Rizado]Why use an old version of wine? Get the newest one from winehq and the script for dapper that downloads all recommended packages.[/QUOTE]
wine 0.9.12 is the newest one. The only newer you can get is.

---

### Post by fluffington on 2006-05-07
I'm getting the same error as [Jason_25](http://ubuntuforums.org/showpost.php?p=989826&postcount=12). I'm running an up-to-date Kubuntu Dapper.

```
gcc-3.4 -m32 -o wine-glibc glibc.o -Wl,--rpath,\$ORIGIN/`../tools/relpath /usr/local/bin /usr/local/lib` -L../libs/wine -lwine -L../libs/port -lwine_port -lpthread
/usr/bin/ld: warning: libdl.so.2, needed by ../libs/wine/libwine.so, not found (try using -rpath or -rpath-link)
../libs/wine/libwine.so: undefined reference to `dlclose@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dlerror@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dlopen@GLIBC_2.1'
../libs/wine/libwine.so: undefined reference to `dlsym@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dladdr@GLIBC_2.0'
collect2: ld returned 1 exit status
make[1]: *** [wine-glibc] Error 1
make[1]: Leaving directory `/home/noah/tmp/wine-0.9.12~winehq1.orig/loader'
make: *** [loader] Error 2

```

---

### Post by Jason_25 on 2006-05-08
Thanks for the confirmation on that.  I'm totally stumped, as I have the library it's referring to.

---

### Post by Rizado on 2006-05-08
[QUOTE=psychosushi]wine 0.9.12 is the newest one. The only newer you can get is.[/QUOTE]Ahaaa, I never read through the post properly and thought you used the source package from the repositories.

---

### Post by jontxo on 2006-05-08
If there are any problem with the localitation of any library the best thing to solve it is to edit, or to create new, the file /etc/ld.so.conf. There you can tell ubuntu the directories where it can search for libraries. This is my file:

/etc/ld.soconf
/usr/lib32
/lib32/

after editing this file you only have to use the comand sudo ldconfig. To see if the system finds now the library you can use: sudo ldconfig -p |grep name_of_the_library

---

### Post by psychosushi on 2006-05-08
[QUOTE=jontxo]If there are any problem with the localitation of any library the best thing to solve it is to edit, or to create new, the file /etc/ld.so.conf. There you can tell ubuntu the directories where it can search for libraries. This is my file:

/etc/ld.soconf
/usr/lib32
/lib32/

after editing this file you only have to use the comand sudo ldconfig. To see if the system finds now the library you can use: sudo ldconfig -p |grep name_of_the_library[/QUOTE]
thanks, I didn't think of that. I'll add it to my original post.

---

### Post by jontxo on 2006-05-08
to compile correctly wine there a lot of libraries that have to be copied to the /usr/lib32 directory. To find them you have to edit the file config.log that is created when you run the comand: CC="gcc-3.4 -m32 ./configure. Here there are a lot of messages saying that the program cannot find libraries. To solve this  you only have to find out what is the 32 bits package that has the library that is needed and extract the library from the package. To know what is the package that has a library you can use the comand: sudo dpkg -S name_of_the_library, with this you will get the name of the 64 bits version that probably will be the same as the 32 bits.

---

### Post by AlvaroBF on 2006-05-09
```
alvaro@alvaro-desktop:~$ sudo apt-get build-dep wine
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
El paquete libicu28-dev no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente
Sin embargo, los siguientes paquetes lo reemplazan:
  libicu34-dev
Nota, seleccionando libfontconfig1-dev en lugar de libfontconfig-dev
Se instalarán los siguientes paquetes NUEVOS:
  bison debconf-utils debhelper docbook docbook-dsssl docbook-to-man
  docbook-utils docbook-xsl flex fontforge html2text jadetex libarts1-dev
  libartsc0-dev libaudio-dev libcapi20-3 libcapi20-dev libcupsys2-dev
  libexpat1-dev libfontconfig1-dev libgcrypt11-dev libgl1-mesa-dev
  libglib1.2-dev libglib2.0-dev libglu1-mesa-dev libgnutls-dev
  libgpg-error-dev libicu34 libicu34-dev libieee1284-3-dev libjack0.100.0-0
  libjack0.100.0-dev liblcms1-dev libldap2-dev libmng-dev libncurses5-dev
  libopencdk8-dev libosp5 libostyle1c2 libpopt-dev libqt3-headers
  libqt3-mt-dev libsane-dev libsgmls-perl libsp1c2 libssl-dev libt1-5
  libtasn1-2-dev libungif4-dev libusb-dev libxcursor-dev libxfixes-dev
  libxft-dev libxinerama-dev libxslt1-dev libxxf86dga-dev libxxf86vm-dev
  mesa-common-dev openjade prelink qt3-dev-tools sgmlspl sp tetex-base
  tetex-bin tetex-extra tex-common x11proto-fixes-dev
0 actualizados, 68 se instalarán, 0 para eliminar y 0 no actualizados.
E: El paquete libicu28-dev no tiene candidato para su instalación
E: No se pudieron procesar las dependencias de construcción
alvaro@alvaro-desktop:~$
```


Why do I get this error?

---

### Post by Jason_25 on 2006-05-09
'The package libicu28-dev has no installation candidate'.  It means a dependency it needs is not available in the ubuntu repositories.  I searched for the debian version and grabbed that one.

---

### Post by e1ektrob0y on 2006-05-10
1

---

### Post by marcemi on 2006-05-10
I've the same problem, ./ configure ends with this warning:
*** Warning: Freetype or Fontforge is missing.
*** Fonts will not be built. Dialog text may be invisible or unaligned.

Is there anyone who can tell what can I do?

---

### Post by Jason_25 on 2006-05-10
If you look above, it should still work despite those problems.  That is, if you can get it to compile.

---

### Post by YokoZar on 2006-05-11
[QUOTE=Jason_25]'The package libicu28-dev has no installation candidate'.  It means a dependency it needs is not available in the ubuntu repositories.  I searched for the debian version and grabbed that one.[/QUOTE]
Don't do this.  You need libicu34-dev.

[QUOTE=AlvaroBF]
Why do I get this error?[/QUOTE]
Both of you are using the wrong apt repository to build-dep wine from:

Read this thread: [http://ubuntuforums.org/showthread.php?p=999374](http://ubuntuforums.org/showthread.php?p=999374)

---

### Post by flapane on 2006-05-26
i get
.
[.....]
:/home/flapane/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1059: undefined reference to `gluDeleteTess'
:/home/flapane/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1016: undefined reference to `gluTessVertex'
:/home/flapane/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1045: undefined reference to `gluTessEndContour'
collect2: ld returned 1 exit status
winegcc: gcc-3.4 failed.
make[2]: *** [opengl32.dll.so] Error 2
make[2]: Leaving directory `/home/flapane/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32'
make[1]: *** [opengl32] Error 2
make[1]: Leaving directory `/home/flapane/tmp/wine-0.9.12~winehq1.orig/dlls'
make: *** [dlls] Error 2

i found this in configure.log

configure:8306: gcc-3.4 -m32 -o conftest -g -O2    conftest.c -lXrende$
$/3.4.6/../../../libXrender.so when searching for -lXrender
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/3.4.6$
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXrender.so when $
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXrender.a when s$
/usr/bin/ld: skipping incompatible /usr/lib/libXrender.so when searchi$
/usr/bin/ld: skipping incompatible /usr/lib/libXrender.a when searchin$
/usr/bin/ld: cannot find -lXrender
collect2: ld returned 1 exit status

Iused this link [http://bugs.winehq.org/show_bug.cgi?id=5124](http://bugs.winehq.org/show_bug.cgi?id=5124) but without lucky

---

### Post by psychosushi on 2006-05-30
[QUOTE=flapane]i get
.
[.....]
:/home/flapane/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1059: undefined reference to `gluDeleteTess'
:/home/flapane/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1016: undefined reference to `gluTessVertex'
:/home/flapane/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1045: undefined reference to `gluTessEndContour'
collect2: ld returned 1 exit status
winegcc: gcc-3.4 failed.
make[2]: *** [opengl32.dll.so] Error 2
make[2]: Leaving directory `/home/flapane/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32'
make[1]: *** [opengl32] Error 2
make[1]: Leaving directory `/home/flapane/tmp/wine-0.9.12~winehq1.orig/dlls'
make: *** [dlls] Error 2

i found this in configure.log

configure:8306: gcc-3.4 -m32 -o conftest -g -O2    conftest.c -lXrende$
$/3.4.6/../../../libXrender.so when searching for -lXrender
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/3.4.6$
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXrender.so when $
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXrender.a when s$
/usr/bin/ld: skipping incompatible /usr/lib/libXrender.so when searchi$
/usr/bin/ld: skipping incompatible /usr/lib/libXrender.a when searchin$
/usr/bin/ld: cannot find -lXrender
collect2: ld returned 1 exit status

Iused this link [http://bugs.winehq.org/show_bug.cgi?id=5124](http://bugs.winehq.org/show_bug.cgi?id=5124) but without lucky[/QUOTE]

Install libXrender (the 32-bit version) the same way as the other 32-bit libraries were installed. And please post what happens, because this is a little bit peculiar.

---

### Post by Evil on 2006-05-30
I receive the following error during compilation:

make[2]: Entering directory `/arcane/wine/libs/wpp'
gcc -m32 -c -I. -I. -I../../include -I../../include    -Wall -pipe -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o preproc.o preproc.c
gcc -m32 -c -I. -I. -I../../include -I../../include    -Wall -pipe -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o wpp.o wpp.c
bison -ppp -d -t ./ppy.y -o ppy.tab.c
./ppy.y:138 parser name defined to default :"parse"
bison -ppp -d -t ./ppy.y -o ppy.tab.c
./ppy.y:138 parser name defined to default :"parse"
gcc -m32 -c -I. -I. -I../../include -I../../include    -Wall -pipe -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o ppy.tab.o ppy.tab.c
flex -olex.yy.c ./ppl.l
gcc -m32 -c -I. -I. -I../../include -I../../include    -Wall -pipe -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o lex.yy.o lex.yy.c
./ppl.l:167:21: error: ppy.tab.h: No such file or directory
./ppl.l:234: error: syntax error before ‘YYSTYPE’
./ppl.l: In function ‘pplex’:
./ppl.l:316: error: ‘tINCLUDE’ undeclared (first use in this function)
./ppl.l:316: error: (Each undeclared identifier is reported only once
./ppl.l:316: error: for each function it appears in.)
./ppl.l:318: error: ‘tERROR’ undeclared (first use in this function)
./ppl.l:319: error: ‘tWARNING’ undeclared (first use in this function)
./ppl.l:320: error: ‘tPRAGMA’ undeclared (first use in this function)
./ppl.l:321: error: ‘tPPIDENT’ undeclared (first use in this function)
./ppl.l:322: error: ‘tUNDEF’ undeclared (first use in this function)
./ppl.l:323: error: ‘tIFDEF’ undeclared (first use in this function)
./ppl.l:324: error: ‘tIFNDEF’ undeclared (first use in this function)
./ppl.l:325: error: ‘tIF’ undeclared (first use in this function)
./ppl.l:326: error: ‘tELIF’ undeclared (first use in this function)
./ppl.l:327: error: ‘tELSE’ undeclared (first use in this function)
./ppl.l:328: error: ‘tENDIF’ undeclared (first use in this function)
./ppl.l:329: error: ‘tLINE’ undeclared (first use in this function)
./ppl.l:330: error: ‘tGCCLINE’ undeclared (first use in this function)
./ppl.l:332: error: ‘tNL’ undeclared (first use in this function)
./ppl.l:340: error: ‘pplval’ undeclared (first use in this function)
./ppl.l:368: error: ‘tDEFINED’ undeclared (first use in this function)
./ppl.l:369: error: ‘tLSHIFT’ undeclared (first use in this function)
./ppl.l:370: error: ‘tRSHIFT’ undeclared (first use in this function)
./ppl.l:371: error: ‘tLOGAND’ undeclared (first use in this function)
./ppl.l:372: error: ‘tLOGOR’ undeclared (first use in this function)
./ppl.l:373: error: ‘tEQ’ undeclared (first use in this function)
./ppl.l:374: error: ‘tNE’ undeclared (first use in this function)
./ppl.l:375: error: ‘tLTE’ undeclared (first use in this function)
./ppl.l:376: error: ‘tGTE’ undeclared (first use in this function)
./ppl.l:389: error: ‘tIDENT’ undeclared (first use in this function)
./ppl.l:420: error: ‘tLITERAL’ undeclared (first use in this function)
./ppl.l:429: error: ‘tMACRO’ undeclared (first use in this function)
./ppl.l:430: error: ‘tDEFINE’ undeclared (first use in this function)
./ppl.l:449: error: ‘tMACROEND’ undeclared (first use in this function)
./ppl.l:453: error: ‘tELIPSIS’ undeclared (first use in this function)
./ppl.l:462: error: ‘tCONCAT’ undeclared (first use in this function)
./ppl.l:463: error: ‘tSTRINGIZE’ undeclared (first use in this function)
./ppl.l:559: error: ‘tDQSTRING’ undeclared (first use in this function)
./ppl.l:579: error: ‘tSQSTRING’ undeclared (first use in this function)
./ppl.l:589: error: ‘tIQSTRING’ undeclared (first use in this function)
./ppl.l:641: error: ‘tRCINCLUDE’ undeclared (first use in this function)
./ppl.l:685: error: ‘tRCINCLUDEPATH’ undeclared (first use in this function)

This is building against today's CVS.  The code compiles fine if I build it in a 32-bit chroot, so I don't think it's an error specific to CVS.  Does anyone know why I might be running into this?

---

### Post by Evil on 2006-05-30
BTW, there is a problem with the script that does all the 'cp's:  When you execute sudo -i, your current directory is going to change - causing the following cp commands to fail.  At least that's what happened on my "pretty standard" Kubuntu 6.06 setup.

---

### Post by beeldings on 2006-06-02
[QUOTE=psychosushi]
Now you have the latest wine installed in your amd64 system. Use the guide at [http://ubuntuforums.org/showthread.php?t=29996&highlight=winecvs](http://ubuntuforums.org/showthread.php?t=29996&highlight=winecvs) from step four to configure wine properly.
[/QUOTE]

One problem, the link to the winetools package is down. Can I still use Wine without the winetools package?

---

### Post by psychosushi on 2006-06-03
[QUOTE=beeldings]One problem, the link to the winetools package is down. Can I still use Wine without the winetools package?[/QUOTE]

Absolutely, it just makes wine a bit easier to set up, because it does all the hocus pocus for you. Otherwise you have to actually figure everything out, which is a bit difficult.

Anyway, here is a link which works to download winetools: [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz)

---

### Post by thelost on 2006-06-03
I am having similar problems to others in the thread.

This is the message I get on make: 
> 
make[2]: Entering directory `/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./opengl32.spec    opengl_ext.o opengl_norm.o wgl.o wgl_ext.o  version.res   -Wl,--rpath,\$ORIGIN/`../../tools/relpath /usr/local/lib/wine /usr/local/lib` -o opengl32.dll.so -L../../dlls -luser32 -lgdi32 -ladvapi32 -lkernel32 -lntdll  -L../../libs -lwine -L/usr/X11R6/lib  -lXext -lX11  -lGL -L../../libs/port -lwine_port
wgl.o: In function `wglUseFontOutlines_common':/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:930: undefined reference to `gluNewTess'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:933: undefined reference to `gluTessCallback'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:934: undefined reference to `gluTessCallback'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:935: undefined reference to `gluTessCallback'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:992: undefined reference to `gluTessBeginPolygon'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:999: undefined reference to `gluTessBeginContour'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1002: undefined reference to `gluTessVertex'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1029: undefined reference to `gluTessVertex'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1032: undefined reference to `gluTessVertex'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1038: undefined reference to `gluTessEndContour'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1050: undefined reference to `gluTessEndPolygon'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1059: undefined reference to `gluDeleteTess'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1016: undefined reference to `gluTessVertex'
:/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32/wgl.c:1045: undefined reference to `gluTessEndContour'
collect2: ld returned 1 exit status
winegcc: gcc-3.4 failed.
make[2]: *** [opengl32.dll.so] Error 2
make[2]: Leaving directory `/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls/opengl32'
make[1]: *** [opengl32] Error 2
make[1]: Leaving directory `/home/nemof/tmp/wine-0.9.12~winehq1.orig/dlls'
make: *** [dlls] Error 2



Am I missing dependencies? I've no idea what to do I am a total ubuntu-newb, so help would be greatfully recieved!

---

### Post by thelost on 2006-06-03
never mind, I used these instructions [http://ubuntuforums.org/showthread.php?t=185557](http://ubuntuforums.org/showthread.php?t=185557) and now wine is working just fine with dapper drake!

---

### Post by nbayiha on 2006-06-03
hello i managed ,somehow , to install wine but when i want to run it i have this problem
[HTML]wine: could not load L"c:\\windows\\system32\\PROGRAM.exe": Module not found[/HTML]
what should i do ??? i was fighting for more than two hours to install it now i don't know what i to do...
thank

---

### Post by eran- on 2006-06-05
Okay... let's see. I've done everything I've been ordered to, but when doing command "make depend && make", I'll get the following error:
```
make[1]: Entering directory `/home/user/tmp/wine-0.9.12~winehq1.orig/loader'
gcc-3.4 -m32 -o wine-glibc glibc.o -Wl,--rpath,\$ORIGIN/`../tools/relpath /usr/l                                                                                                   ocal/bin /usr/local/lib` -L../libs/wine -lwine -L../libs/port -lwine_port -lpthr                                                                                                   ead
/usr/bin/ld: warning: libdl.so.2, needed by ../libs/wine/libwine.so, not found (                                                                                                   try using -rpath or -rpath-link)
../libs/wine/libwine.so: undefined reference to `dlclose@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dlerror@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dlopen@GLIBC_2.1'
../libs/wine/libwine.so: undefined reference to `dlsym@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dladdr@GLIBC_2.0'
collect2: ld returned 1 exit status
make[1]: *** [wine-glibc] Error 1
make[1]: Leaving directory `/home/user/tmp/wine-0.9.12~winehq1.orig/loader'
make: *** [loader] Error 2

```

I've tried to use the other command mentioned *CC="gcc-3.4 -m32" LDFLAGS=-L/lib32/ ./configure*, but it didn't help at all.

Dpkg -S libdl*  also tells me the following:
```
$ dpkg -S libdl*
libc6-dev-i386: /usr/lib32/libdl.so
libc6-dev-i386: /usr/lib32/libdl.a
libc6: /lib/libdl.so.2
libc6-dev: /usr/lib/libdl.a
libc6-i386: /lib32/libdl-2.3.6.so
libc6-dev: /usr/lib/libdl.so
libc6: /lib/libdl-2.3.6.so
libc6-i386: /lib32/libdl.so.2

```

So, here I am a little bit stuck. I've tried to do the whole process again from the beginning, but the outcome won't change.

Is there a solution for this?

---

### Post by psychosushi on 2006-06-05
[QUOTE=eran-]Okay... let's see. I've done everything I've been ordered to, but when doing command "make depend && make", I'll get the following error:
```
make[1]: Entering directory `/home/user/tmp/wine-0.9.12~winehq1.orig/loader'
gcc-3.4 -m32 -o wine-glibc glibc.o -Wl,--rpath,\$ORIGIN/`../tools/relpath /usr/l                                                                                                   ocal/bin /usr/local/lib` -L../libs/wine -lwine -L../libs/port -lwine_port -lpthr                                                                                                   ead
/usr/bin/ld: warning: libdl.so.2, needed by ../libs/wine/libwine.so, not found (                                                                                                   try using -rpath or -rpath-link)
../libs/wine/libwine.so: undefined reference to `dlclose@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dlerror@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dlopen@GLIBC_2.1'
../libs/wine/libwine.so: undefined reference to `dlsym@GLIBC_2.0'
../libs/wine/libwine.so: undefined reference to `dladdr@GLIBC_2.0'
collect2: ld returned 1 exit status
make[1]: *** [wine-glibc] Error 1
make[1]: Leaving directory `/home/user/tmp/wine-0.9.12~winehq1.orig/loader'
make: *** [loader] Error 2

```

I've tried to use the other command mentioned *CC="gcc-3.4 -m32" LDFLAGS=-L/lib32/ ./configure*, but it didn't help at all.

Dpkg -S libdl*  also tells me the following:
```
$ dpkg -S libdl*
libc6-dev-i386: /usr/lib32/libdl.so
libc6-dev-i386: /usr/lib32/libdl.a
libc6: /lib/libdl.so.2
libc6-dev: /usr/lib/libdl.a
libc6-i386: /lib32/libdl-2.3.6.so
libc6-dev: /usr/lib/libdl.so
libc6: /lib/libdl-2.3.6.so
libc6-i386: /lib32/libdl.so.2

```

So, here I am a little bit stuck. I've tried to do the whole process again from the beginning, but the outcome won't change.

Is there a solution for this?[/QUOTE]

Try sudo ln -s /lib32/libdl.so.2 /lib32/libdl.so && sudo ldconfig

I had a similar problem with a different compile, and this solved it.

---

### Post by eran- on 2006-06-05
Okay, it worked out. Thank you. :)

---

### Post by papaver on 2006-06-05
hi.. I get the following error when I try to make the wine package :

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/3.4.6/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/3.4.6/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc-3.4 failed.
make[2]: *** [ddraw.dll.so] Error 2


dpkg -S libXext :

ia32-libs: /usr/lib32/libXext.so.6.4.0
libxext-dev: /usr/lib/libXext.so
libxext6: /usr/lib/libXext.so.6.4.0
libxext6: /usr/lib/libXext.so.6
ia32-libs: /usr/lib32/libXext.so.6
libxext-dev: /usr/lib/libXext.a


any help would be appreciated... thanks!

---

### Post by psychosushi on 2006-06-06
[QUOTE=papaver]hi.. I get the following error when I try to make the wine package :

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/3.4.6/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/3.4.6/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc-3.4 failed.
make[2]: *** [ddraw.dll.so] Error 2


dpkg -S libXext :

ia32-libs: /usr/lib32/libXext.so.6.4.0
libxext-dev: /usr/lib/libXext.so
libxext6: /usr/lib/libXext.so.6.4.0
libxext6: /usr/lib/libXext.so.6
ia32-libs: /usr/lib32/libXext.so.6
libxext-dev: /usr/lib/libXext.a


any help would be appreciated... thanks![/QUOTE]

try sudo ln -s /usr/lib32/libXext.so.4.0 /usr/lib32/libXext.so && sudo ldconfig.

By the way, if you are using breezy, then this guide probably doesn't work.

---

### Post by carney1979 on 2006-06-06
> Install libXrender (the 32-bit version) the same way as the other 32-bit libraries were installed. 
I got the same exact error.

I'm unsure what you mean above. Would you please be more specific? Such as in an actual example?

Thanks!

David

---

### Post by psychosushi on 2006-06-06
[QUOTE=carney1979]I got the same exact error.

I'm unsure what you mean above. Would you please be more specific? Such as in an actual example?

Thanks!

David[/QUOTE]

Download the 32-bit .deb, expand it using the dpkg -x command, copy the pertinent file to the /usr/lib32 folder (.so.[some numbers]), make the symlinks (ln -s) and type sudo ldconfig

---

### Post by dawp on 2006-06-06
i get this odd little error when i do `make`

> ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.Q9AZ0H.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2
make[2]: Leaving directory `/home/daniel/tmp/dlls/gdi'
make[1]: *** [gdi] Error 2
make[1]: Leaving directory `/home/daniel/tmp/dlls'
make: *** [dlls] Error 2


---

### Post by psychosushi on 2006-06-06
[QUOTE=dawp]i get this odd little error when i do `make`[/QUOTE]
this is the same error I always got when I tried to compile wine in breezy amd64. Are you using breezy? I you are then this is insoluble to the best of my knowledge.

---

### Post by dawp on 2006-06-06
i'm on dapper

my sys specs are
optreron 165
asus a8n-sli premium
nvidia 6800gt
1 gig mem

---

### Post by dawp on 2006-06-06
i did a fresh install now i'm getting 
> 
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1063: undefined reference to `gluTessEndPolygon'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1072: undefined reference to `gluDeleteTess'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1029: undefined reference to `gluTessVertex'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1058: undefined reference to `gluTessEndContour'
collect2: ld returned 1 exit status
winegcc: gcc-3.4 failed.


how do i get the pakage for libxrender ?

i tried
sudo apt-get install build-essential libxrender-i386

---

### Post by psychosushi on 2006-06-06
[QUOTE=dawp]i get this odd little error when i do `make`[/QUOTE]

It looks like your libicu34 libraries aren't there. Check that you installed them correctly like I said in the howto. If that doesn't work, try copying them to /lib32 as well, but that really shouldn't be necessary.

---

### Post by psychosushi on 2006-06-06
[QUOTE=dawp]i did a fresh install now i'm getting 


how do i get the pakage for libxrender ?

i tried
sudo apt-get install build-essential libxrender-i386[/QUOTE]

You can't get a 32-bit version of libXrender like this, you need to install it manually (download the deb, copy files and make the appropriate symlinks). However, can you please post the full error message, because here it doesn't say which library has gone wrong, and usually it would.

---

### Post by dawp on 2006-06-06
full error message:

> 
wgl.o: In function `wglUseFontOutlines_common':/home/dan/tmp/wine/dlls/opengl32/wgl.c:943: undefined reference to `gluNewTess'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:946: undefined reference to `gluTessCallback'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:947: undefined reference to `gluTessCallback'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:948: undefined reference to `gluTessCallback'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1005: undefined reference to `gluTessBeginPolygon'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1012: undefined reference to `gluTessBeginContour'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1015: undefined reference to `gluTessVertex'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1042: undefined reference to `gluTessVertex'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1045: undefined reference to `gluTessVertex'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1051: undefined reference to `gluTessEndContour'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1063: undefined reference to `gluTessEndPolygon'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1072: undefined reference to `gluDeleteTess'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1029: undefined reference to `gluTessVertex'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1058: undefined reference to `gluTessEndContour'
collect2: ld returned 1 exit status
winegcc: gcc-3.4 failed.
make[2]: *** [opengl32.dll.so] Error 2
make[2]: Leaving directory `/home/dan/tmp/wine/dlls/opengl32'
make[1]: *** [opengl32] Error 2
make[1]: Leaving directory `/home/dan/tmp/wine/dlls'
make: *** [dlls] Error 2


and from config.log

> 
#define SONAME_LIBXRENDER "libXrender.so"
#define STDC_HEADERS 1
#define __ASM_FUNC(name) ".type " __ASM_NAME(name) ",@function"
#define __ASM_NAME(name) name
#endif
#ifdef __cplusplus
extern "C" void std::exit (int) throw (); using std::exit;

configure: exit 1


from the very end of the config file

---

### Post by Fedcer on 2006-06-06
Hi, i'm trying to install wine following this guide and when I get to the point in which I have to do "./configure" i get this error:
```

checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

---

### Post by Fedcer on 2006-06-06
I'm very sorry, I accidentally double posted. :(

---

### Post by Fedcer on 2006-06-06
Here it is the config.log

---

### Post by dawp on 2006-06-06
try 
> 
try typing in a terminal: sudo apt-get install libc6-i386 libc6-dev-i386


this from earlier in the thread

---

### Post by psychosushi on 2006-06-07
[QUOTE=dawp]full error message:



and from config.log



from the very end of the config file[/QUOTE]
try installing libxrender from a 32-bit .deb using the method I outlined for the others.

---

### Post by TerryB on 2006-06-14
I get up to this step "make depend && make" and I get this error everytime:

tdll  -L../../libs -lwine -L../../libs/unicode -lwine_unicode /usr/lib/libsicuuc.a /usr/lib/libsicudata.a -lstdc++ -lgcc_s -L../../libs/port -lwine_port -L/lib32/
ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.4ajp1s.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2
make[2]: Leaving directory `/home/brillt/tmp/wine-0.9.12~winehq1.orig/dlls/gdi'
make[1]: *** [gdi] Error 2
make[1]: Leaving directory `/home/brillt/tmp/wine-0.9.12~winehq1.orig/dlls'
make: *** [dlls] Error 2

I've tried a number of configure commands listed in this thread and I still get the same result.

---

### Post by psychosushi on 2006-06-15
[QUOTE=TerryB]I get up to this step "make depend && make" and I get this error everytime:

tdll  -L../../libs -lwine -L../../libs/unicode -lwine_unicode /usr/lib/libsicuuc.a /usr/lib/libsicudata.a -lstdc++ -lgcc_s -L../../libs/port -lwine_port -L/lib32/
ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.4ajp1s.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2
make[2]: Leaving directory `/home/brillt/tmp/wine-0.9.12~winehq1.orig/dlls/gdi'
make[1]: *** [gdi] Error 2
make[1]: Leaving directory `/home/brillt/tmp/wine-0.9.12~winehq1.orig/dlls'
make: *** [dlls] Error 2

I've tried a number of configure commands listed in this thread and I still get the same result.[/QUOTE]
You need to install the 32-bit version of libicu, like you did with the other 32-bit libraries. But if you are using Breezy, this error is insoluble.

---

### Post by dallag on 2006-08-20
É isso ai...Pra mim valeu, funfo legal.

Ubuntu rulez.... 64Bit's

It's good, very easy.:KS

---

### Post by tokyovigilante on 2006-09-01
I've found that adding

ln -s libfreetype.so.6 libfreetype.so
ln -s libz.so.1 libz.so

to the symlinks in /usr/lib32 will compile freetype support.

---

### Post by tokyovigilante on 2006-09-01
> **dawp said:**
> i did a fresh install now i'm getting 
```
                               :/home/dan/tmp/wine/dlls/opengl32/wgl.c:1063: undefined reference to `gluTessEndPolygon'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1072: undefined reference to `gluDeleteTess'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1029: undefined reference to `gluTessVertex'
:/home/dan/tmp/wine/dlls/opengl32/wgl.c:1058: undefined reference to `gluTessEndContour'
collect2: ld returned 1 exit status
winegcc: gcc-3.4 failed.
``` how do i get the pakage for libxrender ?

i tried
sudo apt-get install build-essential libxrender-i386
I've fixed this issue as well. The problem does not involve xrender, which is in fact installed correctly. The issue is an omission in the opengl32.dll makefile. It can be fixed by the following:
1. Link libGLU
```
cd /usr/lib32
sudo ln -s libGLU.so.1 libGLU.so
``` 2. Edit the Makefile
```
cd /<wine source dir>/dlls/opengl32
nano Makefile
``` Append the following (exactly!) to EXTRALIBS:
```
-lGLU
``` Ctrl X and Y to save the Makefile.
This compiles libGLU.so into opengl32.dll and ensures the availablilty of the OpenGL utilities.

Have a look at [this bug]("http://bugs.winehq.com/show_bug.cgi?id=5124") for details.

Now I can run WoW on my own Wine cross-compile!

At some stage it would be nice if all this information was rolled up into an ia32-libs-wine-dev package or somesuch so that all we'd need to do is install the build deps and run the compile.

---

### Post by mdr on 2006-09-15
I solved the libsicuuc.a no compile bug thanks to this post here:
[http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/1b5bd4fdb314d528/64e0967ed0e138ad](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/1b5bd4fdb314d528/64e0967ed0e138ad)

This re-creates / compiles the icu libs.  So I followed the instructions there and after some trial and error I to managed to create the libsicuuc.a and put it in lib32.

I then compiled wine using a mixture of psychosushi and Wine's suggested command

LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" CC="gcc-3.4 -m32" ./configure
 
Hope this helps those with invalid libsicuuc.a files as per error above. :biggrin:

---

### Post by tokyovigilante on 2006-09-15
> **mdr said:**
> I solved the libsicuuc.a no compile bug thanks to this post here:
[http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/1b5bd4fdb314d528/64e0967ed0e138ad](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/1b5bd4fdb314d528/64e0967ed0e138ad)

This re-creates / compiles the icu libs.  So I followed the instructions there and after some trial and error I to managed to create the libsicuuc.a and put it in lib32.

I then compiled wine using a mixture of psychosushi and Wine's suggested command

LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" CC="gcc-3.4 -m32" ./configure
 
Hope this helps those with invalid libsicuuc.a files as per error above. :biggrin:
Well spotted. I had been getting round this by removing my 64 bit libicu34-dev and symlinking the /usr/lib32 dependencies to /usr/lib, but this is a much neater way. 

I think if you're installing the 32 bit dependencies the way that psychosushi recommends, then you don't need to build your own libsicu, just change the gdi Makefile as the guide recommends.

I've also found that if you have libc-i386-dev installed, and all the 32 bit libs in the right place, that a simple ./configure is all thats required.

---

### Post by tokyovigilante on 2006-09-30
I've got Wine 0.9.21 and hopefully 22 to compile with gcc 4 by using the -fno-stack-protector CFLAG - ie

CFLAGS="-fno-stack-protector" ./configure

This avoids the segmentation faults when Wine is build with gcc 4.

---

### Post by nandanator on 2006-11-29
My version of wine is Wine 0.9.22
Now when i try to run the following ,I get a message like this.


:confused: 

nandu@nandu-desktop:~$ wine --version
Wine 0.9.22
nandu@nandu-desktop:~$
nandu@nandu-desktop:~$ cd Windows\ media\ player\ 10/
nandu@nandu-desktop:~/Windows media player 10$ wine Setup\ 10.exe
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15


Iam a newbie and what should I do?
:confused:

---

### Post by bodhi.zazen on 2006-11-30
Nice How-to 



This thread has been added to the UDSF wiki.



[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by roadcone on 2007-08-20
I have been trying to compile wine all day. I'm using a downloaded source folder for the simple fact that the .deb doesn't work. Neither does the source. When I configure it tells me that there is "No  openGL library found on this system", and "FreeType development files not found."

The config.log shows multiple files with this format: "/usr/bin/ld: skipping incompatible /usr/lib/libX11.so when searching for -lX11"

Also, when running wine after a make and install regardless of the errors, I get this message: "The X11 driver is missing.  Check your build!"

Can someone please give me some insight. I am about to give up, as not one single fix I've tried so far has put a dent in any of these problems. Thanks for any assistance you can give!

---


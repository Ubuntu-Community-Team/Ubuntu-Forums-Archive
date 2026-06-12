---
title: "Can't compile Audacity - problem finding wxWidgets"
date: 2009-02-09
forum: Packaging and Compiling Programs
---

### Post by alberto ferreira on 2009-02-09
**I compiled [COLOR=Red]wxGTK-2.8.9[/COLOR] from source;My steps:**
tar .....
cd .....
mkdir buildgtk
cd buildgtk
../configure --with-gtk
make
sudo make install
sudo ldconfig

^^^^^^^^^^^^^^^^^^Just like the instructions and everything seemed fine

**Then I did this for [COLOR=Red]Audacity[/COLOR]:**

tar ...
cd ......
./configure
 
and this appears at the end:
> checking for wx-config... /usr/local/bin/wx-config

  Warning: No config found to match: /usr/local/bin/wx-config --unicode=yes --version
           in /usr/local/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.

configure: Checking that the chosen version of wxWidgets is 2.8.x
configure: error: Unable to locate a suitable configuration of wxWidgets v2.8.x or higher.
The currently available configurations are listed below.  If necessary, either
install the package for your distribution or download the latest version of
wxWidgets
from [http://wxwidgets.org](http://wxwidgets.org).

    Default config is gtk2-ansi-release-2.8

  Default config will be used for output


Please help

---

### Post by khelben1979 on 2009-02-09
What version of Audacity are you trying to compile up?

---

### Post by alberto ferreira on 2009-02-09
1.3.7 - (I know I can use the repositories but I want to compile it)

---

### Post by alberto ferreira on 2009-02-11
bump

---

### Post by cmat on 2009-02-11
Did you also install wxWidget's dev files? Binary libraries aren't really useful if you're compiling source.

---

### Post by alberto ferreira on 2009-02-11
Thanks it's working !

---

### Post by alberto ferreira on 2009-02-11
Ok, I'm having some problems now:
1- I had used some options in ./configure and now they are stored even after deleting everything and re-extracting the source.
2- during make a lot of "$n translations done, $x of them approximate" being $n and $x numbers
3- when I do sudo make install this is what I get :
> make -C lib-src
make[1]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src'
make -C FileDialog
make[2]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/FileDialog'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/FileDialog'
ln -sf FileDialog/FileDialog.a FileDialog.a
make -C libresample libresample.a
make[2]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/libresample'
make[2]: `libresample.a' is up to date.
make[2]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/libresample'
ln -sf libresample/libresample.a libresample.a
make -C sbsms
make[2]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/sbsms'
Making all in src
make[3]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/sbsms/src'
make  all-am
make[4]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/sbsms/src'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/sbsms/src'
make[3]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/sbsms/src'
make[3]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/sbsms'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/sbsms'
make[2]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/sbsms'
ln -sf sbsms/src/.libs/libsbsms.a .
make -C libnyquist/misc
make[2]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/libnyquist/misc'
make[2]: `intgen' is up to date.
make[2]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/libnyquist/misc'
make -C libnyquist
make[2]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/libnyquist'
make[2]: Nothing to be done for `current'.
make[2]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/libnyquist'
ln -sf libnyquist/libnyquist.a libnyquist.a
make -C portaudio-v19 lib/libportaudio.la
make[2]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/portaudio-v19'
make[2]: `lib/libportaudio.la' is up to date.
make[2]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/portaudio-v19'
ln -sf .libs/libportaudio.a portaudio-v19/lib/libportaudio.a
make -C portmixer
make[2]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/portmixer'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/portmixer'
ln -sf portmixer/libportmixer.a .
make -C lib-widget-extra
make[2]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/lib-widget-extra'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/lib-widget-extra'
make -C libvamp sdkstatic
make[2]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/libvamp'
ranlib src/libvamp-sdk.a
ranlib src/libvamp-hostsdk.a
make[2]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/libvamp'
make -C portsmf
make[2]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/portsmf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src/portsmf'
make[1]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/lib-src'
make -C src
make[1]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/src'
make -C locale
make[1]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/locale'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/locale'
# install desktop file
/usr/bin/install -c -d /usr/local//share/applications
/usr/bin/install -c -m 644 src/audacity.desktop /usr/local//share/applications
# install MIME information
/usr/bin/install -c -d /usr/local//share/mime/packages
/usr/bin/install -c -m 644 src/audacity.xml /usr/local//share/mime/packages
# install the binary
/usr/bin/install -c -d /usr/local//bin
/usr/bin/install -c -m 755 audacity /usr/local//bin/audacity
# install docs
/usr/bin/install -c -d /usr/local//share/audacity
/usr/bin/install -c -d /usr/local//share/doc/audacity
/usr/bin/install -c -m 644 README.txt /usr/local//share/doc/audacity/README.txt
/usr/bin/install -c -m 644 LICENSE.txt /usr/local//share/doc/audacity/LICENSE.txt
# install manpage
/usr/bin/install -c -d /usr/local//share/man/man1
test -f help/audacity.1.gz && \
        /usr/bin/install -c -m 644 help/audacity.1.gz \
        /usr/local//share/man/man1/audacity.1.gz
# install nyquist
/usr/bin/install -c -d /usr/local//share/audacity/nyquist
/usr/bin/install -c -m 644 nyquist/*.lsp /usr/local//share/audacity/nyquist
# install plug-ins
/usr/bin/install -c -d /usr/local//share/audacity/plug-ins
/usr/bin/install -c -m 644 plug-ins/*.ny /usr/local//share/audacity/plug-ins
# install locales
make -C locale install
make[1]: Entering directory `/home/a/Downloads/audacity-src-1.3.7/locale'
linguas='af ar bn bg bs ca ca@valencia cs cy da de el es eu fa fi fr ga gl he hu id it ja ka km ko lt mk nb nl oc pl pt_BR ro ru sk sl sv tg tr uk vi zh zh_TW'; for lang in $linguas ; do \
       /usr/bin/install -c -d /usr/local//share/locale/$lang/LC_MESSAGES ; \
       /usr/bin/install -c -m 644 $lang/audacity.mo /usr/local//share/locale/$lang/LC_MESSAGES/audacity.mo ; \
    done
make[1]: Leaving directory `/home/a/Downloads/audacity-src-1.3.7/locale'
# install an icon for audacity
/usr/bin/install -c -d /usr/local//share/audacity/
/usr/bin/install -c -m 644 images/AudacityLogo48x48.xpm /usr/local//share/audacity/audacity.xpm
and in 2 seconds it fails completion

Please help as I'm completely new to compiling

---

### Post by alberto ferreira on 2009-02-27
bump

---

### Post by luctor on 2009-03-02
Did you run 'make' before 'make install' ?

---

### Post by alberto ferreira on 2009-03-07
Yes

---

### Post by yurtsev on 2009-04-25
Try this: 

[http://audacityteam.org/wiki/index.php?title=CompilingAudacityForBeginners](http://audacityteam.org/wiki/index.php?title=CompilingAudacityForBeginners)

---

### Post by alberto ferreira on 2009-04-26
Didn't help at all, same errors.

---


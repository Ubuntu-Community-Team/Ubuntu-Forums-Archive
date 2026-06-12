---
title: "how can I install Aurora Gtk engine?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Friccy on 2008-05-02
Hi there!

I am quite new in ubuntu so I would need some help.
I like very much the Aurora themes, but I have read that I need to install the engine.
Can any of you help me with this, please.
Thanks!

---

### Post by frup on 2008-05-02
Well where is the page you are getting it from? Usually they have half decent instructions at least. Otherwise the archive you download should have a readme file in it.

Most themes I have encountered can be installed through the System > Preferences > Appearance | Theme tab. Check inside the tar.gz file you have most likely downloaded of the theme that it is just the theme archive and not the readme etc aswell and then click install and select the theme archive.

---

### Post by gandaran on 2008-05-02
> **Friccy said:**
> Hi there!

I am quite new in ubuntu so I would need some help.
I like very much the Aurora themes, but I have read that I need to install the engine.
Can any of you help me with this, please.
Thanks!

get the rigth .deb package for your system, 32-bit or 64-bit and ubuntu 7.10 or 8.4
the .deb package, you just double click on it to install just like windows 
best place to get them, [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by aeiah on 2008-05-02
according to [this page](http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438) you can install them like this:

> To install the theme engine extract it to somewhere convenient and in that directory,
run: "./configure --prefix=/usr" then "make"
For animation support add "-enable-animation" when running "./configure"
Then as a root user "make install".

Then install the gtkrc themes by extracting them to your ~/.themes directory (3 themes in total).

To change your current theme to Aurora (under GNOME) open up Theme Preferences (usually somewhere under System > Preferences) click the Customize button and under the controls tab select the theme you want.


---

### Post by Friccy on 2008-05-02
Thanks for your help!
Like I said I am new in Linux, so I have a question that might soud silly to you:
- how do you run a command in a directory?
I have extracted the engine archive in to the Documents directory and I can't do the rest, I meen run "./configure --prefix=/usr".

---

### Post by Friccy on 2008-05-02
Thanks for your help!
Like I said I am new in Linux, so I have a question that might soud silly to you:
- how do you run a command in a directory?
I have extracted the engine archive in to the Documents directory and I can't do the rest, I meen run "./configure --prefix=/usr".

---

### Post by Perfect Storm on 2008-05-02
Tools you need:
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential auto-apt checkinstall
```


Extract the tar.gz package, then
```
cd <into the extracted package>
auto-apt run ./configure --prefix=/usr -enable-animation
make
checkinstall --install=no
sudo dpkg -i *.deb
```

If you can't use checkinstall use **sudo make install** instead.

---

### Post by Perfect Storm on 2008-05-02
ok I took the liberty/time to try the engine out;

Save it to your Desktop.
```
[size=1]sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential auto-apt checkinstall libgtk2.0-dev

cd ~/Desktop
tar jxfv 56438-Aurora-1.4.tar.bz2
tar zxfv aurora-1.4.tar.gz
cd aurora-1.4
auto-apt run ./configure --prefix=/usr -enable-animation
make
checkinstall --install=no
sudo dpkg -i *.deb
cd ..
tar jxfv gtkrc_themes.tar.bz2 -C ~/.themes[/size]
```

If **tar jxfv gtkrc_themes.tar.bz2 -C ~/.themes** fails you need to make the directory first with this command; **mkdir ~/.themes**
Now open Appearance and click "customize", you can now choose the Aurora themes (3 of them).

---

### Post by luisjorge on 2008-05-02
> sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential auto-apt checkinstall

cd ~/Desktop
tar jxfv 56438-Aurora-1.4.tar.bz2
tar zxfv aurora-1.4.tar.gz
cd aurora-1.4
auto-apt run ./configure --prefix=/usr -enable-animation
make
checkinstall --install=no
sudo dpkg -i *.deb
cd ..
tar jxfv gtkrc_themes.tar.bz2 -C ~/.themes

Hi everyone! I was trying to install the same engine, in Ubuntu 8.04, and I followed the instructions above, and also the ones from gnome-look.org and I get the same error, when running auto-apt run ./configure --prefix=/usr -enable-animation:

```
checking for GTK... no
configure: error: GTK+-2.10 is required to compile aurora
luisjorge@inspiron1525:~/Desktop/aurora-1.4$
```

I checked in synaptic, and I think this ubuntu has GTK version 2.12... How can I install this engine?

Thanks in advance!

Luis Jorge.

---

### Post by Perfect Storm on 2008-05-03
```
[size=1]sudo apt-get install libgtk2.0-dev[/size]
```

---

### Post by Friccy on 2008-05-03
Thanks a lot!
Your help was very useful! Now my computer looks much nicer then before!
Thanks again!

---

### Post by phelixnyc on 2008-05-03
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential auto-apt checkinstall

cd ~/Desktop
tar jxfv 56438-Aurora-1.4.tar.bz2
tar zxfv aurora-1.4.tar.gz
cd aurora-1.4
auto-apt run ./configure --prefix=/usr -enable-animation
make
checkinstall --install=no
sudo dpkg -i *.deb
cd ..
tar jxfv gtkrc_themes.tar.bz2 -C ~/.themes 

I ran the commands above and when it gets to what needs to be installed "Do you want to continue" I press "Y" and enter, it aborts.  Am I doing something wrong?

---

### Post by Perfect Storm on 2008-05-03
Try with between lower caser and upper case "Y". If it fails find them in synaptic and install them through there. Then continue with the guide.

Another option will be using aptitude instead of apt-get

---

### Post by phelixnyc on 2008-05-03
"Aptitude" worked. Thank you.

---

### Post by andd on 2009-01-04
I tried installing aurora engine using the instructions here but failed. I am using ubuntu 8.10 on a x64 machine. I get the following error:
> Exec ./configure failed, auto-apt failed

---

### Post by cajunlibra on 2009-04-09
Followed all advice from above and this is what happens when i run make, sudo make gave me more errors. I have everything installed that was recommended:

cajun@RossLaptop:~/Desktop/downloads/aurora-1.5$ make
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT aurora_rc_style.lo -MD -MP -MF .deps/aurora_rc_style.Tpo -c -o aurora_rc_style.lo `test -f './src/aurora_rc_style.c' || echo './'`./src/aurora_rc_style.c
 gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT aurora_rc_style.lo -MD -MP -MF .deps/aurora_rc_style.Tpo -c ./src/aurora_rc_style.c  -fPIC -DPIC -o .libs/aurora_rc_style.o
./src/aurora_rc_style.c:351: fatal error: opening dependency file .deps/aurora_rc_style.Tpo: Permission denied
compilation terminated.
make: *** [aurora_rc_style.lo] Error 1
cajun@RossLaptop:~/Desktop/downloads/aurora-1.5$ sudo make
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT aurora_rc_style.lo -MD -MP -MF .deps/aurora_rc_style.Tpo -c -o aurora_rc_style.lo `test -f './src/aurora_rc_style.c' || echo './'`./src/aurora_rc_style.c
 gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT aurora_rc_style.lo -MD -MP -MF .deps/aurora_rc_style.Tpo -c ./src/aurora_rc_style.c  -fPIC -DPIC -o .libs/aurora_rc_style.o
mv -f .deps/aurora_rc_style.Tpo .deps/aurora_rc_style.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT aurora_style.lo -MD -MP -MF .deps/aurora_style.Tpo -c -o aurora_style.lo `test -f './src/aurora_style.c' || echo './'`./src/aurora_style.c
 gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT aurora_style.lo -MD -MP -MF .deps/aurora_style.Tpo -c ./src/aurora_style.c  -fPIC -DPIC -o .libs/aurora_style.o
mv -f .deps/aurora_style.Tpo .deps/aurora_style.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT aurora_theme_main.lo -MD -MP -MF .deps/aurora_theme_main.Tpo -c -o aurora_theme_main.lo `test -f './src/aurora_theme_main.c' || echo './'`./src/aurora_theme_main.c
 gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT aurora_theme_main.lo -MD -MP -MF .deps/aurora_theme_main.Tpo -c ./src/aurora_theme_main.c  -fPIC -DPIC -o .libs/aurora_theme_main.o
mv -f .deps/aurora_theme_main.Tpo .deps/aurora_theme_main.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT support.lo -MD -MP -MF .deps/support.Tpo -c -o support.lo `test -f './src/support.c' || echo './'`./src/support.c
 gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT support.lo -MD -MP -MF .deps/support.Tpo -c ./src/support.c  -fPIC -DPIC -o .libs/support.o
mv -f .deps/support.Tpo .deps/support.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT animation.lo -MD -MP -MF .deps/animation.Tpo -c -o animation.lo `test -f './src/animation.c' || echo './'`./src/animation.c
 gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT animation.lo -MD -MP -MF .deps/animation.Tpo -c ./src/animation.c  -fPIC -DPIC -o .libs/animation.o
mv -f .deps/animation.Tpo .deps/animation.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT aurora_draw.lo -MD -MP -MF .deps/aurora_draw.Tpo -c -o aurora_draw.lo `test -f './src/aurora_draw.c' || echo './'`./src/aurora_draw.c
 gcc -DHAVE_CONFIG_H -I. -I./src -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT aurora_draw.lo -MD -MP -MF .deps/aurora_draw.Tpo -c ./src/aurora_draw.c  -fPIC -DPIC -o .libs/aurora_draw.o
mv -f .deps/aurora_draw.Tpo .deps/aurora_draw.Plo
/bin/bash ./libtool --tag=CC   --mode=link gcc  -g -O2 -module -avoid-version -no-undefined  -o libaurora.la -rpath /usr/lib/gtk-2.0/2.10.0/engines aurora_rc_style.lo aurora_style.lo aurora_theme_main.lo support.lo animation.lo aurora_draw.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0   
gcc -shared  .libs/aurora_rc_style.o .libs/aurora_style.o .libs/aurora_theme_main.o .libs/support.o .libs/animation.o .libs/aurora_draw.o  /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libpangoft2-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libgio-2.0.so /usr/lib/libcairo.so /usr/lib/libpango-1.0.so /usr/lib/libfreetype.so -lfontconfig /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libglib-2.0.so  -Wl,-soname -Wl,libaurora.so -o .libs/libaurora.so
creating libaurora.la
(cd .libs && rm -f libaurora.la && ln -s ../libaurora.la libaurora.la)

---

### Post by IbeeFreak705 on 2009-05-28
I have been trying to install a few login themes, two of them of the Aurora variety.  I cannot seem to find where the system stores themes, not to mention how to make them the theme file format.  When I try to find the gtk engines the readme's mention, I get led down a never ending path of required downloads.  I also ran into this when I tried to install desktop themes.  Any help?  I have Ubuntu 9.04.

Thanks.

---

### Post by Ms_Angel_D on 2009-05-28
Ironic I was just looking for .deb for this last night and found it here

[http://www.gnome-look.org/content/show.php/Aurora+Gtk2+Engine+DEB?content=96421]("http://www.gnome-look.org/content/show.php/Aurora+Gtk2+Engine+DEB?content=96421")

No need to compile anything just download & Install :D

I also attached the file

---

### Post by IbeeFreak705 on 2009-05-28
Sorry, but that didn't do it.  I moved files around and the others worked just fine.  For whatever reason, the Aurora themes will not register as theme archives.  I have extracted the folders, but that didn't help any.  Also, for others out there, the file above is meant for Intrepid Ibex.  Thanks anyways.

P.

---

### Post by Ms_Angel_D on 2009-05-28
> **IbeeFreak705 said:**
> Sorry, but that didn't do it.  I moved files around and the others worked just fine.  For whatever reason, the Aurora themes will not register as theme archives.  I have extracted the folders, but that didn't help any.  Also, for others out there, the file above is meant for Intrepid Ibex.  Thanks anyways.

P.

I have jaunty & the deb worked fine for me.

---

### Post by IbeeFreak705 on 2009-05-28
hmmm.  I reinstalled the package, but when I use the GUI to change the login theme selector, I'm still told the .tar is not a valid archive.  The name of the .tar is:  78120-Dark Ubuntu Aurora v2.tar.gz .  I'm beginning to think it's the file itself, since the other themes worked.  Thanks for trying.

P.

Just tried to install the aurora theme engine, but can't get it to work.  Whatever, I'm moving on.

---


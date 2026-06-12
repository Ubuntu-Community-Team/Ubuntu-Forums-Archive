---
title: "[SOLVED] Removing XMMS"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-09-02
[http://blog.xanda.org/?p=436](http://blog.xanda.org/?p=436)

I went here, and did the tutorial, and unsurprisingly was very dissatisfied with the player, and ironically can't remove it now.
I've tried, synaptic, sudo apt-get --purge remove...
How do I remove this?

I just want a player that works, and I hate this thing

---

### Post by iaculallad on 2008-09-02
> **Elephantman5 said:**
> [http://blog.xanda.org/?p=436](http://blog.xanda.org/?p=436)

I went here, and did the tutorial, and unsurprisingly was very dissatisfied with the player, and ironically can't remove it now.
I've tried, synaptic, sudo apt-get --purge remove...
How do I remove this?

I just want a player that works, and I hate this thing

Be sure that you still have the source files from where you installed your XMMS. Now on your terminal, try to search for the uninstall script and use it to remove your application.

---

### Post by aloshbennett on 2008-09-02
I havnt tried this, but if you still have the code

> sudo make uninstall

will create an uninstall script for you.

---

### Post by Elephantman5 on 2008-09-02
> **iaculallad said:**
> Be sure that you still have the source files from where you installed your XMMS. Now on your terminal, try to search for the uninstall script and use it to remove your application.

Tutorial has you delete it. I checked in the trash and didn't find it.

> **aloshbennett said:**
> I havnt tried this, but if you still have the code



will create an uninstall script for you.


So, now I went back to the site and started the beginning of the tutorial again, and have the build dir,
[COLOR=#C20CB9]**tar**[/COLOR] xvf xmms-1.2.11.tar.gz
[COLOR=#7A0874]**cd**[/COLOR] xmms-1.2.11[COLOR=#000000]**/**[/COLOR]


 can't make uninstall yet:

```
ajzimmerman@ajzimmerman-desktop:~/build/xmms-1.2.11$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
```

So, I guess I'm configuring:
.[COLOR=#000000]**/**[/COLOR]configure --[COLOR=#007800]prefix[/COLOR]=[COLOR=#000000]**/**[/COLOR]usr

---
Right then, towards the end now,I've "made" the uninstall
What do I do now? I'm still in the directory. 
ajzimmerman@ajzimmerman-desktop:~/build/xmms-1.2.11$

---

### Post by Perfect Storm on 2008-09-02
After configured it and make uninstall it should be it.

---

### Post by Elephantman5 on 2008-09-02
Let me get this straight.
After the "make uninstall" is done, it's been uninstalled?

---

### Post by aloshbennett on 2008-09-02
You have to run the uninstall script

> ./uninstall

---

### Post by Perfect Storm on 2008-09-02
```
tar xvf xmms-1.2.11.tar.gz
cd xmms-1.2.11
./configure --prefix=/usr
make
sudo make uninstall
```

Yes, it should after running these commands as long you don't get **make: *** No rule to make target `uninstall'.  Stop.**

---

### Post by Ripfox on 2008-09-02
oooh cool I can get my xmms back? Sweet! One man's ceiling is another man's floor.

---

### Post by Elephantman5 on 2008-09-02
> **Artificial Intelligence said:**
> ```
tar xvf xmms-1.2.11.tar.gz
cd xmms-1.2.11
./configure --prefix=/usr
make
sudo make uninstall
```Yes, it should after running these commands as long you don't get **make: *** No rule to make target `uninstall'.  Stop.**```


ajzimmerman@ajzimmerman-desktop:~/Desktop/build/xmms-1.2.11$ sudo make uninstall
[sudo] password for ajzimmerman: 
Making uninstall in intl
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/intl'
if { test "xmms" = "gettext-runtime" || test "xmms" = "gettext-tools"; } \
       && test 'no' = yes; then \
      rm -f /usr/include/libintl.h; \
      /bin/sh ../libtool --mode=uninstall \
        rm -f /usr/lib/libintl.a; \
    else \
      : ; \
    fi
if test "xmms" = "gettext-tools" \
       && test 'no' = no; then \
      rm -f /usr/lib/preloadable_libintl.so; \
    else \
      : ; \
    fi
if test 'no' = yes; then \
      if test -f /usr/lib/charset.alias; then \
        temp=/usr/lib/t-charset.alias; \
        dest=/usr/lib/charset.alias; \
        sed -f ref-del.sed $dest > $temp; \
        if grep '^# Packages using this file: $' $temp > /dev/null; then \
          rm -f $dest; \
        else \
          /usr/bin/install -c -m 644 $temp $dest; \
        fi; \
        rm -f $temp; \
      fi; \
      if test -f /usr/share/locale/locale.alias; then \
        temp=/usr/share/locale/t-locale.alias; \
        dest=/usr/share/locale/locale.alias; \
        sed -f ref-del.sed $dest > $temp; \
        if grep '^# Packages using this file: $' $temp > /dev/null; then \
          rm -f $dest; \
        else \
          /usr/bin/install -c -m 644 $temp $dest; \
        fi; \
        rm -f $temp; \
      fi; \
    else \
      : ; \
    fi
if test "xmms" = "gettext-tools"; then \
      for file in VERSION ChangeLog COPYING.LIB-2.0 COPYING.LIB-2.1 Makefile.in config.charset locale.alias ref-add.sin ref-del.sin gmo.h gettextP.h hash-string.h loadinfo.h plural-exp.h eval-plural.h localcharset.h relocatable.h os2compat.h libgnuintl.h.in bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c loadmsgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y plural-exp.c localcharset.c relocatable.c localename.c log.c osdep.c os2compat.c intl-compat.c plural.c; do \
        rm -f /usr/share/gettext/intl/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/intl'
Making uninstall in libxmms
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/libxmms'
+ list=libxmms.la
+ for p in '$list'
++ echo libxmms.la
++ sed -e 's|^.*/||'
+ p=libxmms.la
+ echo ' /bin/bash ./libtool --mode=uninstall rm -f '\''/usr/lib/libxmms.la'\'''
 /bin/bash ./libtool --mode=uninstall rm -f '/usr/lib/libxmms.la'
+ /bin/bash ./libtool --mode=uninstall rm -f /usr/lib/libxmms.la
 rm -f '/usr/include/xmms/configfile.h'
 rm -f '/usr/include/xmms/xmmsctrl.h'
 rm -f '/usr/include/xmms/dirbrowser.h'
 rm -f '/usr/include/xmms/util.h'
 rm -f '/usr/include/xmms/formatter.h'
 rm -f '/usr/include/xmms/titlestring.h'
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/libxmms'
Making uninstall in xmms
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/xmms'
Making uninstall in defskin
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/xmms/defskin'
make[2]: Nothing to be done for `uninstall'.
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/xmms/defskin'
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/xmms'
 rm -f '/usr/bin/xmms'
 rm -f '/usr/include/xmms/plugin.h'
 rm -f '/usr/include/xmms/fullscreen.h'
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/xmms'
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/xmms'
Making uninstall in Output
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output'
Making uninstall in OSS
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/OSS'
+ list=libOSS.la
+ for p in '$list'
++ echo libOSS.la
++ sed -e 's|^.*/||'
+ p=libOSS.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Output/libOSS.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Output/libOSS.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Output/libOSS.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/OSS'
Making uninstall in esd
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/esd'
+ list=libesdout.la
+ for p in '$list'
++ echo libesdout.la
++ sed -e 's|^.*/||'
+ p=libesdout.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Output/libesdout.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Output/libesdout.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Output/libesdout.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/esd'
Making uninstall in disk_writer
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/disk_writer'
+ list=libdisk_writer.la
+ for p in '$list'
++ echo libdisk_writer.la
++ sed -e 's|^.*/||'
+ p=libdisk_writer.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Output/libdisk_writer.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Output/libdisk_writer.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Output/libdisk_writer.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/disk_writer'
Making uninstall in solaris
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/solaris'
+ list=
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/solaris'
Making uninstall in sun
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/sun'
+ list=
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/sun'
Making uninstall in alsa
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/alsa'
+ list=libALSA.la
+ for p in '$list'
++ echo libALSA.la
++ sed -e 's|^.*/||'
+ p=libALSA.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Output/libALSA.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Output/libALSA.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Output/libALSA.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output/alsa'
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output'
make[2]: Nothing to be done for `uninstall-am'.
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output'
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Output'
Making uninstall in Input
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input'
Making uninstall in wav
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/wav'
+ list=libwav.la
+ for p in '$list'
++ echo libwav.la
++ sed -e 's|^.*/||'
+ p=libwav.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Input/libwav.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Input/libwav.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Input/libwav.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/wav'
Making uninstall in mpg123
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/mpg123'
+ list=libmpg123.la
+ for p in '$list'
++ echo libmpg123.la
++ sed -e 's|^.*/||'
+ p=libmpg123.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Input/libmpg123.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Input/libmpg123.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Input/libmpg123.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/mpg123'
Making uninstall in mikmod
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/mikmod'
+ list=libmikmod.la
+ for p in '$list'
++ echo libmikmod.la
++ sed -e 's|^.*/||'
+ p=libmikmod.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Input/libmikmod.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Input/libmikmod.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Input/libmikmod.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/mikmod'
Making uninstall in cdaudio
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/cdaudio'
+ list=libcdaudio.la
+ for p in '$list'
++ echo libcdaudio.la
++ sed -e 's|^.*/||'
+ p=libcdaudio.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Input/libcdaudio.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Input/libcdaudio.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Input/libcdaudio.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/cdaudio'
Making uninstall in tonegen
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/tonegen'
+ list=libtonegen.la
+ for p in '$list'
++ echo libtonegen.la
++ sed -e 's|^.*/||'
+ p=libtonegen.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Input/libtonegen.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Input/libtonegen.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Input/libtonegen.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/tonegen'
Making uninstall in vorbis
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/vorbis'
+ list=libvorbis.la
+ for p in '$list'
++ echo libvorbis.la
++ sed -e 's|^.*/||'
+ p=libvorbis.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Input/libvorbis.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Input/libvorbis.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Input/libvorbis.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input/vorbis'
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input'
make[2]: Nothing to be done for `uninstall-am'.
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input'
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Input'
Making uninstall in Effect
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Effect'
Making uninstall in voice
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Effect/voice'
+ list=libvoice.la
+ for p in '$list'
++ echo libvoice.la
++ sed -e 's|^.*/||'
+ p=libvoice.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Effect/libvoice.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Effect/libvoice.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Effect/libvoice.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Effect/voice'
Making uninstall in echo_plugin
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Effect/echo_plugin'
+ list=libecho.la
+ for p in '$list'
++ echo libecho.la
++ sed -e 's|^.*/||'
+ p=libecho.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Effect/libecho.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Effect/libecho.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Effect/libecho.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Effect/echo_plugin'
Making uninstall in stereo_plugin
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Effect/stereo_plugin'
+ list=libstereo.la
+ for p in '$list'
++ echo libstereo.la
++ sed -e 's|^.*/||'
+ p=libstereo.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Effect/libstereo.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Effect/libstereo.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Effect/libstereo.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Effect/stereo_plugin'
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Effect'
make[2]: Nothing to be done for `uninstall-am'.
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Effect'
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Effect'
Making uninstall in General
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/General'
Making uninstall in ir
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/General/ir'
+ list=libir.la
+ for p in '$list'
++ echo libir.la
++ sed -e 's|^.*/||'
+ p=libir.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/General/libir.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/General/libir.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/General/libir.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/General/ir'
Making uninstall in joystick
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/General/joystick'
+ list=libjoy.la
+ for p in '$list'
++ echo libjoy.la
++ sed -e 's|^.*/||'
+ p=libjoy.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/General/libjoy.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/General/libjoy.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/General/libjoy.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/General/joystick'
Making uninstall in song_change
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/General/song_change'
+ list=libsong_change.la
+ for p in '$list'
++ echo libsong_change.la
++ sed -e 's|^.*/||'
+ p=libsong_change.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/General/libsong_change.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/General/libsong_change.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/General/libsong_change.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/General/song_change'
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/General'
make[2]: Nothing to be done for `uninstall-am'.
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/General'
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/General'
Making uninstall in Visualization
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Visualization'
Making uninstall in blur_scope
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Visualization/blur_scope'
+ list=libbscope.la
+ for p in '$list'
++ echo libbscope.la
++ sed -e 's|^.*/||'
+ p=libbscope.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Visualization/libbscope.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Visualization/libbscope.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Visualization/libbscope.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Visualization/blur_scope'
Making uninstall in sanalyzer
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Visualization/sanalyzer'
+ list=libsanalyzer.la
+ for p in '$list'
++ echo libsanalyzer.la
++ sed -e 's|^.*/||'
+ p=libsanalyzer.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Visualization/libsanalyzer.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Visualization/libsanalyzer.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Visualization/libsanalyzer.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Visualization/sanalyzer'
Making uninstall in opengl_spectrum
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Visualization/opengl_spectrum'
+ list=libogl_spectrum.la
+ for p in '$list'
++ echo libogl_spectrum.la
++ sed -e 's|^.*/||'
+ p=libogl_spectrum.la
+ echo ' /bin/bash ../../libtool --mode=uninstall rm -f '\''/usr/lib/xmms/Visualization/libogl_spectrum.la'\'''
 /bin/bash ../../libtool --mode=uninstall rm -f '/usr/lib/xmms/Visualization/libogl_spectrum.la'
+ /bin/bash ../../libtool --mode=uninstall rm -f /usr/lib/xmms/Visualization/libogl_spectrum.la
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Visualization/opengl_spectrum'
make[2]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Visualization'
make[2]: Nothing to be done for `uninstall-am'.
make[2]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Visualization'
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/Visualization'
Making uninstall in wmxmms
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/wmxmms'
 rm -f '/usr/bin/wmxmms'
 rm -f '/usr/share/xmms/wmxmms.xpm'
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/wmxmms'
Making uninstall in po
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/po'
catalogs='af.gmo az.gmo be.gmo bg.gmo bs.gmo ca.gmo cs.gmo cy.gmo da.gmo de.gmo el.gmo en.gmo en_GB.gmo eo.gmo es.gmo et.gmo eu.gmo fi.gmo fr.gmo ga.gmo gl.gmo hr.gmo hu.gmo id.gmo it.gmo ja.gmo ka.gmo ko.gmo lt.gmo lv.gmo mk.gmo ms.gmo nn.gmo nl.gmo no.gmo pl.gmo pt.gmo pt_BR.gmo ro.gmo ru.gmo sk.gmo sl.gmo sq.gmo sr.gmo sr@Latn.gmo sv.gmo tg.gmo th.gmo tr.gmo uk.gmo uz.gmo vi.gmo wa.gmo zh_CN.gmo zh_TW.gmo'; \
    for cat in $catalogs; do \
      cat=`basename $cat`; \
      lang=`echo $cat | sed -e 's/\.gmo$//'`; \
      for lc in LC_MESSAGES ; do \
        rm -f /usr/share/locale/$lang/$lc/xmms.mo; \
      done; \
    done
if test "xmms" = "gettext-tools"; then \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed en@quot.header en@boldquot.header insert-header.sin Rules-quot   Makevars.template; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11/po'
make[1]: Entering directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11'
 rm -f '/usr/bin/xmms-config'
 rm -f '/usr/share/aclocal/xmms.m4'
 rm -f '/usr/man/man1/xmms.1'
 rm -f '/usr/man/man1/wmxmms.1'
make[1]: Leaving directory `/home/ajzimmerman/Desktop/build/xmms-1.2.11'
ajzimmerman@ajzimmerman-desktop:~/Desktop/build/xmms-1.2.11$ ./uninstall
bash: ./uninstall: No such file or directory


```

[aloshbennett]("http://ubuntuforums.org/member.php?u=276808") 				your command didn't work.

---

### Post by Perfect Storm on 2008-09-02
It's now uninstalled. you might delete .xmms in your home directory if you don't want to keep/safe your personal settings from it.

---

### Post by Elephantman5 on 2008-09-02
> **Artificial Intelligence said:**
> It's now uninstalled. you might delete .xmms in your home directory if you don't want to keep/safe your personal settings from it.

Thank you ArtificialIntelligence.

Your avatar is quite awesome.

---

### Post by Perfect Storm on 2008-09-02
My Pleasure ^_^

If you're looking for something similar to XMMS but newer there's audacious (in the repo).
Also audacious 2 is under construction from what I can read from their homepage.

---

### Post by Elephantman5 on 2008-09-02
> **Artificial Intelligence said:**
> My Pleasure ^_^

If you're looking for something similar to XMMS but newer there's audacious (in the repo).
Also audacious 2 is under construction from what I can read from their homepage.

Wow...my god, I'm enjoying this tremendously. 
I'm converted!

---


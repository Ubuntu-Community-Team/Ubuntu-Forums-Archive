---
title: "HOWTO: Compile DVDStyler-1.5b7 for Edgy"
date: 2007-01-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Nick Rivers on 2007-01-19
With a bit of work and some googling I managed to compile DVDStyler-1.5b7 and wxsvg-1.0b7 from source.  Since it was a pain figuring it out I thought I would share how I did it.

Install build-essential, gcc, checkinstall:
```
sudo apt-get install build-essential gcc checkinstall
```

Install dvdauthor, mjpegtools, netpbm, mpgtx, mkisofs, dvd+rw-tools, libjpeg62-dev, libwxgtk2.6-dev, libart-2.0-dev, libpango1.0-dev :
```
sudo apt-get install dvdauthor mjpegtools netpbm mpgtx mkisofs dvd+rw-tools libjpeg62-dev libwxgtk2.6-dev libart-2.0-dev libpango1.0-dev
```

Download the source for DVDStyler-1.5b7 and wxsvg-1.0b7 from [http://www.dvdstyler.de/downloads.html](http://www.dvdstyler.de/downloads.html)

Extract the files by right-clicking on them and selecting *Open with "Archive Manager"*

The wrong version of *SVGCanvasTextFreetype.cpp* is included in the wxsvg source.  Download the proper version from [http://sourceforge.net/tracker/download.php?group_id=124832&atid=700774&file_id=200156&aid=1576542](http://sourceforge.net/tracker/download.php?group_id=124832&atid=700774&file_id=200156&aid=1576542)
Save it to /path/to/wxsvg-1.0b7/src/freetype/

Enter the wxsvg-1.0b7 folder:
```
cd /path/to/wxsvg-1.0b7
```

Configure the source.  Since DVDStyler looks for libwxsvg.so.0 in /usr/lib we need to set the install path for wxsvg to /usr since the default installation path is /usr/local :
```
./configure --prefix="/usr"
```

Make the installation files:
```
make
```

Create and install .deb package for wxsvg using checkinstall:
```
sudo checkinstall
```
Just hit ENTER when checkinstall prompts you.

Enter the DVDStyler-1.5b7 folder:
```
cd /path/to/DVDStyler-1.5b7
```

Configure the source:
```
./configure
```

Make the installation files:
```
make
```

Create and install .deb package for dvdstyler using checkinstall:
```
sudo checkinstall
```
Just hit ENTER when checkinstall prompts you.

Create the menu entry for DVDStyler:
```
sudo gedit /usr/share/applications/dvdstyler.desktop
```

Copy and paste the following text:
```

[Desktop Entry]
Encoding=UTF-8
Name=DVD Styler
Comment=DVD Authoring GUI
Exec=dvdstyler
Icon=/usr/local/share/dvdstyler/rc/dvdstyler.png
Terminal=false
Type=Application
Categories=GNOME;Application;AudioVideo;Audio;Video

```

Save the file and exit GEdit.

You should now have an entry under Applications | Sound & Video for DVD Styler.  Click it and *hopefully* DVD Styler will run.

If you run into any problems let me know as I wrote this HOWTO at 4am in the morning and may have forgotten something.

---

### Post by vhscampos on 2007-01-19
Hi!

When I enter './configure --prefix="/usr"', after several checkings, the command returns an error message:

> checking for PANGO... configure: error: Package requirements (pangoft2 >= 1.2.0) were not met:

No package 'pangoft2' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PANGO_CFLAGS
and PANGO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Does anyone know what is the problem?

---

### Post by Nick Rivers on 2007-01-19
> **vhscampos said:**
> Hi!

When I enter './configure --prefix="/usr"', after several checkings, the command returns an error message:
```

checking for PANGO... configure: error: Package requirements (pangoft2 >= 1.2.0) were not met:

No package 'pangoft2' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PANGO_CFLAGS
and PANGO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Does anyone know what is the problem?

You need to install libpango1.0-dev
```
sudo apt-get install libpango1.0-dev
```

---

### Post by vhscampos on 2007-01-19
I forgot to install this package ](*,)   thanks for the advise.

---

### Post by Nick Rivers on 2007-01-19
> **vhscampos said:**
> I forgot to install this package ](*,)   thanks for the advise.
It was my fault actually... I wrote this HOWTO after being up *way too late* and didn't take the time to check all the dependecies.  I have updated the HOWTO so that all dependencies - hopefully - will now be met.

---

### Post by fenian on 2007-01-19
Worked well for me...Thank You.

---

### Post by rai4shu2 on 2007-01-19
At some point you'll probably need to fix this:

> Error: mpeg2enc could not read YUV4MPEG2 header : Stream requires unsupported features

There is a problem with mjpegtools >1.6.2 by menu generating.
To fix it you need to add "-S 420mpeg2" to ppmtoy4m command
in DVDStyler core settings or downgrade mjpegtools.

see [http://dvdstyler.sourceforge.net/wiki/FAQMjpegtoolsError](http://dvdstyler.sourceforge.net/wiki/FAQMjpegtoolsError)

---

### Post by Nick Rivers on 2007-01-20
> **rai4shu2 said:**
> At some point you'll probably need to fix this:
```
Error: mpeg2enc could not read YUV4MPEG2 header : Stream requires unsupported features

There is a problem with mjpegtools >1.6.2 by menu generating.
To fix it you need to add "-S 420mpeg2" to ppmtoy4m command
in DVDStyler core settings or downgrade mjpegtools.
```

see [http://dvdstyler.sourceforge.net/wiki/FAQMjpegtoolsError](http://dvdstyler.sourceforge.net/wiki/FAQMjpegtoolsError)
I checked the core settings in DVDStyler-1.5b7 and I don't see the ppmtoy4m command anywhere, so this may be a problem with older versions of DVDStyler.

---

### Post by vhscampos on 2007-01-20
> **Nick Rivers said:**
> I checked the core settings in DVDStyler-1.5b7 and I don't see the ppmtoy4m command anywhere, so this may be a problem with older versions of DVDStyler.

Yes, this problem only occurs in older versions. I made a DVD yesterday with the latest version and went fine.

---

### Post by BrowneR on 2007-01-24
I have been trying to follow this how-to in order to update my installed version of wxsvg from beta5 (which i installed from a deb) to beta7 to fix some bugs in dvdstyler.

All dependencies are met and wxsvg configures correctly however i get errors when trying to compile.

At first i was trying to compile **without** the updated SVGCanvasTextFreetype.cpp. When i realised this and **substituted the updated file in its place** the compilation proceeded further but now crashes out with a **new** error message again related to freetype.

Does anyone by chance have a copy of the wxsvg.deb they built with checkinstall that they could attach? Not sure if it would work on my system but it's worth a try. 

Or maybe someone has some suggestions that i could try although i realise this is probably an issue to take up with the developer.

---

### Post by vhscampos on 2007-01-24
> Does anyone by chance have a copy of the wxsvg.deb they built with checkinstall that they could attach? Not sure if it would work on my system but it's worth a try.

The resulting package:
[wxSVG 1.0 beta7]("http://rapidshare.com/files/13257100/wxsvg_1.0b7-1_i386.deb.html")

---

### Post by LucasLinard on 2007-01-25
Does ANyone know how to change the subtitle font, size, and etc?
Where can I find the xml file that has spumux configs?

---

### Post by BrowneR on 2007-01-25
> **vhscampos said:**
> The resulting package:
[wxSVG 1.0 beta7]("http://rapidshare.com/files/13257100/wxsvg_1.0b7-1_i386.deb.html")

Thank you Sir! =D> 

It's working well for me although there is a bug causing objects to appear totally black when selected. Not a problem though as its still totally usable and it has fixed another annoying issue with buttons.

---

### Post by Dubbayoo on 2007-02-08
I'm getting an error compiling on Edgy. Configure works fine. 


> teve@ubu:~/tmp/dvd/DVDStyler-1.5b7_1$ **make**
Making all in wxVillaLib
make[1]: Entering directory `/home/steve/tmp/dvd/DVDStyler-1.5b7_1/wxVillaLib'
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\"  -MT ImageProc.o -MD -MP -MF ".deps/ImageProc.Tpo" \
          -c -o ImageProc.o `test -f 'ImageProc.cpp' || echo './'`ImageProc.cpp; \
        then mv -f ".deps/ImageProc.Tpo" ".deps/ImageProc.Po"; \
        else rm -f ".deps/ImageProc.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\"  -MT imagjpg.o -MD -MP -MF ".deps/imagjpg.Tpo" \
          -c -o imagjpg.o `test -f 'imagjpg.cpp' || echo './'`imagjpg.cpp; \
        then mv -f ".deps/imagjpg.Tpo" ".deps/imagjpg.Po"; \
        else rm -f ".deps/imagjpg.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\"  -MT PipeExecute.o -MD -MP -MF ".deps/PipeExecute.Tpo" \
          -c -o PipeExecute.o `test -f 'PipeExecute.cpp' || echo './'`PipeExecute.cpp; \
        then mv -f ".deps/PipeExecute.Tpo" ".deps/PipeExecute.Po"; \
        else rm -f ".deps/PipeExecute.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\"  -MT PropDlg.o -MD -MP -MF ".deps/PropDlg.Tpo" \
          -c -o PropDlg.o `test -f 'PropDlg.cpp' || echo './'`PropDlg.cpp; \
        then mv -f ".deps/PropDlg.Tpo" ".deps/PropDlg.Po"; \
        else rm -f ".deps/PropDlg.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\"  -MT SConv.o -MD -MP -MF ".deps/SConv.Tpo" \
          -c -o SConv.o `test -f 'SConv.cpp' || echo './'`SConv.cpp; \
        then mv -f ".deps/SConv.Tpo" ".deps/SConv.Po"; \
        else rm -f ".deps/SConv.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\"  -MT Thumbnails.o -MD -MP -MF ".deps/Thumbnails.Tpo" \
          -c -o Thumbnails.o `test -f 'Thumbnails.cpp' || echo './'`Thumbnails.cpp; \
        then mv -f ".deps/Thumbnails.Tpo" ".deps/Thumbnails.Po"; \
        else rm -f ".deps/Thumbnails.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\"  -MT ThumbnailFactory.o -MD -MP -MF ".deps/ThumbnailFactory.Tpo" \
          -c -o ThumbnailFactory.o `test -f 'ThumbnailFactory.cpp' || echo './'`ThumbnailFactory.cpp; \
        then mv -f ".deps/ThumbnailFactory.Tpo" ".deps/ThumbnailFactory.Po"; \
        else rm -f ".deps/ThumbnailFactory.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\"  -MT utils.o -MD -MP -MF ".deps/utils.Tpo" \
          -c -o utils.o `test -f 'utils.cpp' || echo './'`utils.cpp; \
        then mv -f ".deps/utils.Tpo" ".deps/utils.Po"; \
        else rm -f ".deps/utils.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\"  -MT VerticalToolbar.o -MD -MP -MF ".deps/VerticalToolbar.Tpo" \
          -c -o VerticalToolbar.o `test -f 'VerticalToolbar.cpp' || echo './'`VerticalToolbar.cpp; \
        then mv -f ".deps/VerticalToolbar.Tpo" ".deps/VerticalToolbar.Po"; \
        else rm -f ".deps/VerticalToolbar.Tpo"; exit 1; \
        fi
rm -f libwxvilla.a
ar cru libwxvilla.a ImageProc.o imagjpg.o PipeExecute.o PropDlg.o SConv.o Thumbnails.o ThumbnailFactory.o utils.o VerticalToolbar.o 
ranlib libwxvilla.a
make[1]: Leaving directory `/home/steve/tmp/dvd/DVDStyler-1.5b7_1/wxVillaLib'
Making all in src
make[1]: Entering directory `/home/steve/tmp/dvd/DVDStyler-1.5b7_1/src'
Making all in rc
make[2]: Entering directory `/home/steve/tmp/dvd/DVDStyler-1.5b7_1/src/rc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steve/tmp/dvd/DVDStyler-1.5b7_1/src/rc'
make[2]: Entering directory `/home/steve/tmp/dvd/DVDStyler-1.5b7_1/src'
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\" -I.. -MT About.o -MD -MP -MF ".deps/About.Tpo" \
          -c -o About.o `test -f 'About.cpp' || echo './'`About.cpp; \
        then mv -f ".deps/About.Tpo" ".deps/About.Po"; \
        else rm -f ".deps/About.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\" -I.. -MT Config.o -MD -MP -MF ".deps/Config.Tpo" \
          -c -o Config.o `test -f 'Config.cpp' || echo './'`Config.cpp; \
        then mv -f ".deps/Config.Tpo" ".deps/Config.Po"; \
        else rm -f ".deps/Config.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\" -I.. -MT Languages.o -MD -MP -MF ".deps/Languages.Tpo" \
          -c -o Languages.o `test -f 'Languages.cpp' || echo './'`Languages.cpp; \
        then mv -f ".deps/Languages.Tpo" ".deps/Languages.Po"; \
        else rm -f ".deps/Languages.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\" -I.. -MT hyperlink.o -MD -MP -MF ".deps/hyperlink.Tpo" \
          -c -o hyperlink.o `test -f 'hyperlink.cpp' || echo './'`hyperlink.cpp; \
        then mv -f ".deps/hyperlink.Tpo" ".deps/hyperlink.Po"; \
        else rm -f ".deps/hyperlink.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\" -I.. -MT DVD.o -MD -MP -MF ".deps/DVD.Tpo" \
          -c -o DVD.o `test -f 'DVD.cpp' || echo './'`DVD.cpp; \
        then mv -f ".deps/DVD.Tpo" ".deps/DVD.Po"; \
        else rm -f ".deps/DVD.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\" -I.. -MT Palette3D.o -MD -MP -MF ".deps/Palette3D.Tpo" \
          -c -o Palette3D.o `test -f 'Palette3D.cpp' || echo './'`Palette3D.cpp; \
        then mv -f ".deps/Palette3D.Tpo" ".deps/Palette3D.Po"; \
        else rm -f ".deps/Palette3D.Tpo"; exit 1; \
        fi
if g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"DVDStyler\ 1.0\" -DPACKAGE_BUGREPORT=\"dvdstyler-users@lists.sourceforge.net\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -I. -I.     -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA     -DDATADIR=\"/usr/local/share/dvdstyler\" -I.. -MT MenuObject.o -MD -MP -MF ".deps/MenuObject.Tpo" \
          -c -o MenuObject.o `test -f 'MenuObject.cpp' || echo './'`MenuObject.cpp; \
        then mv -f ".deps/MenuObject.Tpo" ".deps/MenuObject.Po"; \
        else rm -f ".deps/MenuObject.Tpo"; exit 1; \
        fi
MenuObject.cpp: In member function &#8216;void MenuObject::Forward()&#8217;:
MenuObject.cpp:522: error: &#8216;class wxSVGUseElement&#8217; has no member named &#8216;GetNextSibling&#8217;
MenuObject.cpp:526: error: &#8216;class wxSVGElement&#8217; has no member named &#8216;GetNextSibling&#8217;
MenuObject.cpp: In member function &#8216;void MenuObject::Backward()&#8217;:
MenuObject.cpp:532: error: &#8216;class wxSVGUseElement&#8217; has no member named &#8216;GetPreviousSibling&#8217;
MenuObject.cpp: In member function &#8216;void MenuObject::ToBack()&#8217;:
MenuObject.cpp:542: error: &#8216;class wxSVGElement&#8217; has no member named &#8216;GetFirstChild&#8217;
MenuObject.cpp:545: error: &#8216;class wxSVGElement&#8217; has no member named &#8216;GetNextSibling&#8217;
MenuObject.cpp: In member function &#8216;bool MenuObject::IsFirst()&#8217;:
MenuObject.cpp:553: error: &#8216;class wxSVGUseElement&#8217; has no member named &#8216;GetPreviousSibling&#8217;
MenuObject.cpp: In member function &#8216;bool MenuObject::IsLast()&#8217;:
MenuObject.cpp:558: error: &#8216;class wxSVGUseElement&#8217; has no member named &#8216;GetNextSibling&#8217;
make[2]: *** [MenuObject.o] Error 1
make[2]: Leaving directory `/home/steve/tmp/dvd/DVDStyler-1.5b7_1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steve/tmp/dvd/DVDStyler-1.5b7_1/src'
make: *** [all-recursive] Error 1

---

### Post by Dubbayoo on 2007-02-08
Anyone have a deb for DVDStyler-1.5b7?

---

### Post by psych-major on 2007-02-18
Yep, see attached.

BTW, I used the wxsvg deb posted above, 'cuz I could't get it to compile either, worked like a charm!

---

### Post by LucasLinard on 2007-04-07
Hi I Get his error when compiling wxsvg:

> 
checking for strip... strip
checking for correct ltmain.sh version... no
configure: error:

*** [Gentoo] sanity check failed! ***
*** libtool.m4 and ltmain.sh have a version mismatch! ***
*** (libtool.m4 = 1.5.22, ltmain.sh = "1.5.22 Debian 1.5.22-4") ***

Please run:

  libtoolize --copy --force

if appropriate, please contact the maintainer of this
package (or your distribution) for help.


I'm using feisty.

---

### Post by nim278 on 2007-04-24
I've managed to get past this one by editing the ltmain.sh to the version number is exactly 1.5.22 (no quotation marks). However, then it complains that ```
checking for wxWindows version >= 2.6.3... no (version 2.4.5 is not new enough)
```, so I think I'm SOL unless i can find a wxwin2.6 package... .. or someone can tell me how to get the i386 deb package running on amd64 :(

---

### Post by ryboto on 2007-04-27
> **nim278 said:**
> I've managed to get past this one by editing the ltmain.sh to the version number is exactly 1.5.22 (no quotation marks). However, then it complains that ```
checking for wxWindows version >= 2.6.3... no (version 2.4.5 is not new enough)
```, so I think I'm SOL unless i can find a wxwin2.6 package... .. or someone can tell me how to get the i386 deb package running on amd64 :(

I'm in the exact same boat...Can't use the i386 packages, and I keep getting a version conflict with ltmain.sh.  I don't want to have to boot to windows to use dvdstyler, but if i have to...

---

### Post by Tomas_IV on 2007-06-07
I'm on Feisty and this howto doesn't work for me. Since the wxsvg download mentioned in previous posts no longer works, I was searching other source of binary package. I found a multimedia repository for Dapper containing both dvdstyler 1.5b7 and wxsvg 1.0b7. Since it is for Dapper, I did not added it to my sources.list, instead I just downloaded the two debs from [http://lprod.org/deb/dapper/](http://lprod.org/deb/dapper/) and installed them like this:
```
sudo dpkg -i wxsvg_1.0b7.3-lprod.org1_i386.deb dvdstyler_1.5-b7.3-lprod.org1_i386.deb
```
It works :D, and it solved my problems with missing buttons I had with both 1.4 and 1.5b4 versions (although probably connected to corresponding wxsvg version).

---

### Post by euxneks on 2007-06-20
I have to compile this from source because I'm using feisty x64, so I did - my steps are as follows:

All apt-get steps as in the first post, then
download source for wxsvg (1.0b7_3 as of this post) and extract it somewhere, then run these commands in the directory where you extracted everything (CLI of course)

```
./autogen.sh
./configure --prefix="/usr"
make
sudo checkinstall

```
You might have to do ```
libtoolize --force
``` before you can configure properly (ignore [FONT="Courier New"]--copy[/FONT],  I was able to get this to work without it)

Next, install DVDstyler, same thing again, extract it, go to the directory, do like so:

```
./autogen.sh
./configure --prefix="/usr"
make
sudo checkinstall

```
I'm using feisty - and now, also dvdstyler
Edit: I use checkinstall because then it's easy to remove software if you want to, using dpkg

---

### Post by LucasLinard on 2007-06-22
> **euxneks said:**
> I have to compile this from source because I'm using feisty x64, so I did - my steps are as follows:

All apt-get steps as in the first post, then
download source for wxsvg (1.0b7_3 as of this post) and extract it somewhere, then run these commands in the directory where you extracted everything (CLI of course)

```
./autogen.sh
./configure --prefix="/usr"
make
sudo checkinstall

```
You might have to do ```
libtoolize --force
``` before you can configure properly (ignore [FONT="Courier New"]--copy[/FONT],  I was able to get this to work without it)

Next, install DVDstyler, same thing again, extract it, go to the directory, do like so:

```
./autogen.sh
./configure --prefix="/usr"
make
sudo checkinstall

```
I'm using feisty - and now, also dvdstyler
Edit: I use checkinstall because then it's easy to remove software if you want to, using dpkg


Hi.

I actualy installed the the debs. but I couldn't get the SVGCanvasTextFreetype.cpp
can anyone send me them?

---

### Post by Nick Rivers on 2007-06-25
Sorry I haven't responded to this thread in so long.  However, I have written a new HOWTO for DVDStyler 1.5 Final on i386 Feisty.  The compile process is much easier this time around.  For those of you who would rather just download and install binaries instead of compiling from source, I have also posted download links to i386 feisty debs for wxsvg-1.07b_2 and dvdstyler-1.5 which I compiled myself. 

[_HOWTO: DVDStyler 1.5 Final on i386 Feisty by Nick Rivers_]("http://ubuntuforums.org/showthread.php?t=482761")


Nick Rivers

---

### Post by computx on 2007-10-19
I am installing on amd64 gutsy. FYI latest DVDStyler depends on gettext so grab that from the repos also. Otherwise it does install under gutsy gibbon using the amd64 instructions.

---

### Post by mortinc on 2007-10-20
Trying to install under cygwin, so the .debs are'nt going to work for me. Any chance someone could be kind enough to post the SVGCanvasTextFreetype.cpp

Thanks

---

### Post by computx on 2007-10-20
I think the latest wxsvg has that file as I couldn't find it either and everything compiled ok and works fine.

---

### Post by mortinc on 2007-10-22
Hi Comutx,
 Here's the steps I'm taking and latest errors:

Downloaded wxsvg-1.0b7_3

[PHP]
$ touch NEWS
$ touch README
$ touch ltmain.sh
$ automake --add-missing
$ ./configure
$ make

Making all in src
make[1]: Entering directory `/wxsvg-1.0b7_3/src'
Making all in xml
make[2]: Entering directory `/wxsvg-1.0b7_3/src/xml'
Making all in expat
make[3]: Entering directory `/wxsvg-1.0b7_3/src/xml/expat'
/bin/sh ../../../libtool --tag=CC   --mode=compile gcc -DPACKAGE_NAME=\"wxsvgtest\" -DPACKAGE_TARNAME=\"wxsvgtest\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"wxsvgtest\ 1.0\" -DPACKAGE_BUGREPORT=\"wx-svg-users@lists.sourceforge.net\" -DPACKAGE=\"wxsvgtest\" -DVERSION=\"1.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -I.     -g -O2 -MT xmlrole.lo -MD -MP -MF .deps/xmlrole.Tpo -c -o xmlrole.lo xmlrole.c
mv -f .deps/xmlrole.Tpo .deps/xmlrole.Plo
mv: cannot stat `.deps/xmlrole.Tpo': No such file or directory
make[3]: *** [xmlrole.lo] Error 1
make[3]: Leaving directory `/wxsvg-1.0b7_3/src/xml/expat'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/wxsvg-1.0b7_3/src/xml'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/wxsvg-1.0b7_3/src'
make: *** [all-recursive] Error 1
[/PHP]

---

### Post by computx on 2007-10-23
Hmm you are using a newer version than I have. I am using wxsvg-1.0b7_2 , get that version at sourceforge and try it. I suspect that not all of the package's dependancies are met in cygwin. If you could track down what package supplies xmlrole.lo and install that you may get farther but I can't help much there. I havent used cygwin in years. Maybe a vmware ubuntu install would be easier.

---


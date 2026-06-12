---
title: "HOWTO: Compile DVDStyler 1.5 Final on i386 Feisty"
date: 2007-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Nick Rivers on 2007-06-24
Since my HOWTO for DVDStyler 1.5b7 is outdated, I decided to see if I could compile DVDStyler 1.5 Final.  With a little bit of googling and some tweaking I was able to make it happen. 

OK... on to the HOWTO!

Install build-essential, gcc, checkinstall:
```
sudo apt-get install build-essential gcc checkinstall
```

Install dvdauthor, mjpegtools, netpbm, mpgtx, mkisofs, dvd+rw-tools, libjpeg62-dev, libwxgtk2.6-dev, libart-2.0-dev, libpango1.0-dev gettext libtool libltdl3 libltdl3-dev autoconf autoconf2.13 automake:
```
sudo apt-get install dvdauthor mjpegtools netpbm mpgtx mkisofs dvd+rw-tools libjpeg62-dev libwxgtk2.6-dev libart-2.0-dev libpango1.0-dev gettext libtool libltdl3 libltdl3-dev autoconf autoconf2.13 automake
```

Download the source for DVDStyler-1.5 and wxsvg-1.0b7_2 from the following URLs:

[DVDStyler-1.5.tar.gz]("http://prdownloads.sourceforge.net/dvdstyler/DVDStyler-1.5.tar.gz?download")
[wxsvg-1.0b7_2.tar.gz]("http://prdownloads.sourceforge.net/wxsvg/wxsvg-1.0b7_2.tar.gz?download")

Extract the files by right-clicking on them and selecting Open with "Archive Manager"

Enter the wxsvg-1.0b7 folder:
```
cd /path/to/wxsvg-1.0b7_2
```

We need to create two text files that the author forgot to place in the source code.  They aren't necessary for anything but autoreconf whines if they aren't present.  
```
gedit NEWS
```

Save the file and then do the same again for README
```
gedit README
```

Save the file.

We need to do a bit of magic on the source code before we can configure it.
```
autoreconf --install --force -v
```

Configure the source. Since DVDStyler looks for libwxsvg.so.0 in /usr/lib we need to set the install path for wxsvg to /usr since the default installation path is /usr/local :
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

Just hit ENTER when checkinstall prompts you, or you can follow the menu prompts to enter you maintainer information, etc.


Enter the DVDStyler-1.5 folder:
```
cd /path/to/DVDStyler-1.5
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

Just hit ENTER when checkinstall prompts you, or you can follow the menu prompts to enter you maintainer information, etc.

Create the menu entry for DVDStyler:
```
sudo gedit /usr/share/applications/dvdstyler.desktop
```

Copy and paste the following text:```

[Desktop Entry]
Encoding=UTF-8
Name=DVD Styler
Comment=DVD Authoring GUI
Exec=dvdstyler
Icon=/usr/local/share/dvdstyler/rc/logo.png
Terminal=false
Type=Application
Categories=GNOME;Application;AudioVideo;Audio;Video
```

Save the file and exit GEdit.

You should now have an entry under Applications | Sound & Video for DVD Styler. Click it and *hopefully* DVD Styler will run.

If you run into any problems let me know. :)



Nick Rivers

---

### Post by LucasLinard on 2007-06-25
thanks for the howto! I'll try it tonight!

---

### Post by vibertholdo on 2007-06-26
adding this to my MAIN How-Tos =p
Thanks, dude! \o/

---

### Post by bruenig on 2007-06-26
Wrote a script to automate this. Simply get the script below make it executable.
```
chmod +x dvdstylerinstall.sh
```
And then run it as root
```
sudo ./dvdstylerinstall.sh
```

---

### Post by DC@DR on 2007-06-26
Neat and nice HOWTO, many thanks :-)

---

### Post by erwall on 2007-06-26
I'm getting this when I run the script:

Error compiling and installing wxsvg.

Any ideas?

---

### Post by bruenig on 2007-06-26
do the compiling wxsvg stuff step by step and see where the problem is:
#Compile wxsvg
echo "Compiling wxsvg..."
tar xf  wxsvg-1.0b7_2.tar.gz
cd  wxsvg-1.0b7_2
touch NEWS README
autoreconf --install --force -v
./configure --prefix=/usr
make
checkinstall

---

### Post by erwall on 2007-06-26
NM, used the deb and worked great!  Thanks for the help.

---

### Post by LucasLinard on 2007-06-26
Hi
I can compile both dvdstyler and wxsvg, but dvdstryler doesn't work. It works, but there's no way to insert a button in a menu. anyone can help?

---

### Post by psych-major on 2007-07-10
These instructions worked perfectly on my 64bit core 2 duo! Compiled 64bit debs are linked below.

[dvdstyler_1.5-1_amd64.deb]("http://home.earthlink.net/~corey.maddocks/data/dvdstyler_1.5-1_amd64.deb")

[wxsvg_1.0b7_2-1_amd64.deb]("http://home.earthlink.net/~corey.maddocks/data/wxsvg_1.0b7_2-1_amd64.deb")

---

### Post by spainjd on 2007-09-29
I'm doing this for DVDStyler 1.5.1_2, so this may not apply, but on the configure step for DVDStyler I got the following warning.

"WARNING: libgnomeui will not be used for rendering of thumbnails"

Installing libgnomeui-dev from the repositories corrected this, and it installed flawlessly, so you might add this to your list of packages.

Great tutorial thanks.

---

### Post by bretticus on 2007-10-27
Wasted time installing previous debs for my athlon using Gutsy. Either couldn't build or got seg faults on the deb packages. This all worked like a charm. THANK YOU! I love dvdstyler. Certianly the best free DVD authoring program (much better than tovid IMHO.)

---

### Post by piponline on 2007-10-28
I get this error when I try to start DVD Styler:

"dvdstyler: error while loading shared libraries: libwx_gtk2_core-2.8.so.0: cannot open shared object file: No such file or directory".

Any help?

Thks!

---

### Post by adwatkin19 on 2007-12-14
Thank you so much for this, i really needed this program and didnt want to have to go back to the 32bit edition, this worked a treat for me thanks alot. 

Adam

---

### Post by earther on 2008-02-28
This HOWTO was very helpful.  DVDStyler 1.5 is up and running!

Now I want to upgrade to DVDStyler v1.6.0.  I tried a few things but no joy.  Any pointers would be very welcome.

Thanks.

---


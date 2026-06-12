---
title: "Dvdstyler fails to compile anyone?"
date: 2007-10-22
forum: Programming Talk
---

### Post by mickbuntu on 2007-10-22
Hello,

Anyone know what is going on the compile fails  here is the log below:

[HTML]

make[2]: Entering directory `/home/Desktop/DVDStyler-1.5.1_2/src'
g++  -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -DGNOME2 -DDATADIR=\"/usr/share/dvdstyler\" -I..   -o dvdstyler About.o Config.o Languages.o hyperlink.o KeyDlg.o DVD.o Palette3D.o MenuObject.o MenuPalettes.o Menu.o Slideshow.o MPEG.o SettingsDlg.o NewProjectDlg.o DVDPropDlg.o AVPropDlg.o MenuPropDlg.o TitlePropDlg.o MenuObjectPropDlg.o MenuEditor.o TitlesetManager.o BurnDlg.o ProgressDlg.o MainWin.o dvdstyler.o ../wxVillaLib/libwxvilla.a -pthread   -lwx_gtk2u_core-2.8 -lwx_baseu-2.8 -lwx_gtk2u_html-2.8   -lwxsvg -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgconf-2 -lgmodule-2.0 -ldl -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0   
../wxVillaLib/libwxvilla.a(PropDlg.o): In function `wxStringBase':
/usr/include/wx-2.8/wx/string.h:368: undefined reference to `wxGridNameStr'
collect2: ld returned 1 exit status
make[2]: *** [dvdstyler] Error 1
make[2]: Leaving directory `/home/rooty/Desktop/DVDStyler-1.5.1_2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rooty/Desktop/DVDStyler-1.5.1_2/src'
make: *** [all-recursive] Error 1


[/HTML]

---

### Post by mickbuntu on 2007-10-23
Post pump from below.

---

### Post by scorp123 on 2007-10-23
> **mickbuntu said:**
>  Anyone know what is going on the compile fails  here is the log below There are *.deb packages you could download and install, e.g. from [here]("http://www.getdeb.net/app.php?name=DVDStyler")

The packages I linked to are for "Feisty". If you need "Gutsy" packages you have to click on "Categories" on the left and then tell the web page you'd like to see "other versions". It should then let you select "Gutsy" packages.

---

### Post by mickbuntu on 2007-10-23
> **scorp123 said:**
> There are *.deb packages you could download and install, e.g. from [here]("http://www.getdeb.net/app.php?name=DVDStyler")

The packages I linked to are for "Feisty". If you need "Gutsy" packages you have to click on "Categories" on the left and then tell the web page you'd like to see "other versions". It should then let you select "Gutsy" packages.

Thank you for the links, looked other day could not find it without you. When i'm on  my other machine i'll consider the debs. Although the  building is  puzzling and have contacted the  project   leader on sourceforge.

---

### Post by Orra on 2007-10-28
> **mickbuntu said:**
> Hello,

Anyone know what is going on the compile fails  here is the log below:

[HTML]

make[2]: Entering directory `/home/Desktop/DVDStyler-1.5.1_2/src'
g++  -g -O2  -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -DGNOME2 -DDATADIR=\"/usr/share/dvdstyler\" -I..   -o dvdstyler About.o Config.o Languages.o hyperlink.o KeyDlg.o DVD.o Palette3D.o MenuObject.o MenuPalettes.o Menu.o Slideshow.o MPEG.o SettingsDlg.o NewProjectDlg.o DVDPropDlg.o AVPropDlg.o MenuPropDlg.o TitlePropDlg.o MenuObjectPropDlg.o MenuEditor.o TitlesetManager.o BurnDlg.o ProgressDlg.o MainWin.o dvdstyler.o ../wxVillaLib/libwxvilla.a -pthread   -lwx_gtk2u_core-2.8 -lwx_baseu-2.8 -lwx_gtk2u_html-2.8   -lwxsvg -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgconf-2 -lgmodule-2.0 -ldl -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0   
../wxVillaLib/libwxvilla.a(PropDlg.o): In function `wxStringBase':
/usr/include/wx-2.8/wx/string.h:368: undefined reference to `wxGridNameStr'
collect2: ld returned 1 exit status
make[2]: *** [dvdstyler] Error 1
make[2]: Leaving directory `/home/rooty/Desktop/DVDStyler-1.5.1_2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rooty/Desktop/DVDStyler-1.5.1_2/src'
make: *** [all-recursive] Error 1


[/HTML]
Heya, I had the exact same problem as you. I fixed it by uninstalling the wxWidgets 2.8.x development packages, installing the wxWidgets 2.6.x development packages. Then I got a fresh copy of the source, and it compiled fine.

The advantage of this opposed to the packages is that DVD Styler 2.5's newer than DVD Styler 2.4 ;)

---

### Post by mickbuntu on 2007-10-30
> **Orra said:**
> Heya, I had the exact same problem as you. I fixed it by uninstalling the wxWidgets 2.8.x development packages, installing the wxWidgets 2.6.x development packages. Then I got a fresh copy of the source, and it compiled fine.

The advantage of this opposed to the packages is that DVD Styler 2.5's newer than DVD Styler 2.4 ;)

Thank You fix worked, seems needs older libs. The one on getdeb is nice but this one has nothing missing. Devede is nice too but in my view and opinion is not as customizable. Each to their own!!

---


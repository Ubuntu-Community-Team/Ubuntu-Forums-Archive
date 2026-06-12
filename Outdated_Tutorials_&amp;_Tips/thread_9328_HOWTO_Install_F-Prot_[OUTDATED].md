---
title: "HOWTO: Install F-Prot [OUTDATED]"
date: 2004-12-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2004-12-27
**OBSOLITE!!! Check the howto on 5.04 it works as well on 4.10 [http://www.ubuntuforums.org/showthread.php?t=25421](http://www.ubuntuforums.org/showthread.php?t=25421)**


Hello there!
      
      If you are one of them who do dual boot with a win OS or Connecting via network to a win OS computer this is a _must_!
 As for linux there aren't a really threat when we are talking about viruses and alike, there some few viruses for linux out there, but the chance to get virus on Linux is almost non-existing, a firewall is better as protection.
      
      But anyway here it is:
      
      Grab F-prot [here]("http://www.f-prot.com/products/home_use/linux/") and pick the debian/gnu file
      
      and the nice gui to F-Prot [here]("http://web.tiscali.it/sharp/xfprot/") (XFProt v 1.9 )
      
      Make sure that **libwww-perl** is installed in ubuntu, if you're not sure check your Package management.
      
      ```

      cd /where/you/saved/the/files/
      sudo dpkg -i  fp-linux-ws.deb
      
```
      
 Now extract xfprot-1.9.tar.gz by right clicking on it and choose 'extract here' some may prefer using the terminal to do it, but I think this is the easist way, no need to make it more complicated than it is (that's just my opinion) ;)
      
      ```

      cd xfprot-1.9
      ./configure
      make
      sudo make install
      
      nautilus applications:///System
      
```
      
      file menu ----> **Create launcher**
      
      basic tab ----> 
      Name: **F-Prot**
      Command:[b] xfprot
      [/b]Icon: **/usr/local/xfprot/icons/antivirus-48x48.png**
      
    Check the attached screenshot of it.
   For F-prot manual: /usr/local/f-prot/doc_ws/index.html
  
  The F-prot can't get updated through xf-prot because it ask for **su** password and ubuntu it's **sudo **so you have to do it manually:
  
  ```

  sudo /usr/local/f-prot/tools/check-updates.pl
  
```
  
  for automatically updates check the doc:
  /usr/local/f-prot/doc_ws/auto_updt.html
  
      
      
      .:=The AI Dude=:.

---

### Post by Perfect Storm on 2005-01-28
EDIT: Corrected some typo errors  :???:

---

### Post by NeoChaosX on 2005-01-29
I keep getting a blank error message whenever I try to run XFProt 1.9.  Is there something I did wrong?

---

### Post by Perfect Storm on 2005-01-31
I'm still at XFprot 1.8 but I'll give it a try soon.

---

### Post by Perfect Storm on 2005-01-31
Okay I tried the new version and I havn't encountered any problems.

When you compiling it should look something like this:


```

orion@Universe:/usr/local $ cd /home/orion/Documents/Software/F-Prot/xfprot-1.9
orion@Universe:~/Documents/Software/F-Prot/xfprot-1.9 $ **./configure**
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Checking for su.....OK

Using default values for f-prot's install directory: /usr/local/f-prot

If you experience problems with the default settings try
the --autodetect switch or change them by editing manually config.h.

Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for xterm.....OK
Found Gtk+ libs version 1.2.10
Found Gtk+ libs version 2.4.10
Which one should I use?
[1] Gtk+-1.2.10
[2] Gtk+-2.4.10
[1/2]>**2**
Using Gtk+ 2.4.10 libs
Build with debug statements?
[1] Yes
[2] No
[1/2]>**1**
Adding debug statements to Makefile.in
Setting language to en_GB, you can override this with: --with-lang=xx_XX
Supported languages are:
en_GB
es_ES
fr_FR
pl_PL
pt_BR
orion@Universe:~/Documents/Software/F-Prot/xfprot-1.9 $ **make**
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -c -o xfprot-gtk.o xfprot-gtk.c
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -c -o TextViewWindow.o TextViewWindow.c
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -c -o TextEditWindow.o TextEditWindow.c
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -c -o AboutWindow.o AboutWindow.c
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -c -o TextCommon.o TextCommon.c
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -c -o DialogWindow.o DialogWindow.c
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -c -o FileSelector.o FileSelector.c
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -DL_window_create -DL_table_create -DL_frame_create_on_table -DL_text_box_create_on_table -DL_button_create_on_table -DL_radio_create_on_table -DL_check_create_on_table -DL_label_create_on_table -DL_textpad_create_on_table -DL_default_button_box_create_on_table -DL_button_create_in_container -DL_radio_create -DL_check_create -DL_button_create -DL_button_box_create_on_table -DL_statusbar_create_on_table -DL_main_loop -DL_main_menu_create -DL_attach_to_table -DL_window_close -DL_progressbar_create_on_table -DL_progress_destroy -DL_progressbar_create -DL_progress_timeout -DL_about_callback -c -o mygtk.o mygtk.c
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -DL_msg -DL_err_msg -DL_xsnprintf -DL_xcalloc -DL_xalloc_die -DL_xmake_message -DL_xmalloc -DL_xpclose_nostdin -DL_xfclose_nostdin -DL_xgetcwd -DL_xpopen -DL_xopen_die -DL_xconcat_path_file -DL_xrealloc -DL_xstrncat -DL_xchmod -DL_xchown -DL_xchdir -DL_xputs -DL_xmkdir -DL_last_char_is -DL_xstrdup  -DL_xfgetc_nbuf -DL_xfree -DL_xstrlen -c -o mylib.o mylib.c
cc -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -o xfprot-gtk xfprot-gtk.o TextViewWindow.o TextEditWindow.o AboutWindow.o TextCommon.o DialogWindow.o FileSelector.o mygtk.o mylib.o
orion@Universe:~/Documents/Software/F-Prot/xfprot-1.9 $ **sudo make install**
mkdir -p /usr/local/xfprot
chmod 0755 /usr/local/xfprot
cp xfprot-gtk /usr/local/xfprot
chmod  0755 /usr/local/xfprot/xfprot-gtk
cp COPYING /usr/local/xfprot
chmod 0644 /usr/local/xfprot/COPYING
cp README /usr/local/xfprot
chmod 0644 /usr/local/xfprot/README
cp eicar.com.txt /usr/local/xfprot/eicar.com
chmod 0644 /usr/local/xfprot/eicar.com
mkdir /usr/local/xfprot/icons
chmod 0755 /usr/local/xfprot/icons
cp icons/antivirus-128x128.png /usr/local/xfprot/icons/antivirus-128x128.png
chmod 0644 /usr/local/xfprot/icons/antivirus-128x128.png
cp icons/antivirus-32x32.png /usr/local/xfprot/icons/antivirus-32x32.png
chmod 0644 /usr/local/xfprot/icons/antivirus-32x32.png
cp icons/antivirus-48x48.png /usr/local/xfprot/icons/antivirus-48x48.png
chmod 0644 /usr/local/xfprot/icons/antivirus-48x48.png
cp icons/antivirus-64x64.png /usr/local/xfprot/icons/antivirus-64x64.png
chmod 0644 /usr/local/xfprot/icons/antivirus-64x64.png
cp icons/README /usr/local/xfprot/icons/README
chmod 0644 /usr/local/xfprot/icons/README
mkdir -p /usr/local/bin
ln -s ../xfprot/xfprot-gtk /usr/local/bin/xfprot
ln: `/usr/local/bin/xfprot': File exists
orion@Universe:~/Documents/Software/F-Prot/xfprot-1.9 $



```

---

### Post by angrylittleman on 2005-02-02
Works great for me! Now I am now scanning my network....works great!

---

### Post by Perfect Storm on 2005-02-03
Good to hear ^_^



*Updated the HOWTO to match v 1.9*

---

### Post by iotc247 on 2005-02-13
root@alexs-lappy:/home/alex/Deb/xfprot-1.9 # make
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_0 -c -o xfprot-gtk.o xfprot-gtk.c
In file included from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from mygtk.h:28,
                 from <command line>:15:
/usr/include/gtk-2.0/gtk/gtkaboutdialog.h:108: warning: declaration of `link' shadows a global declaration
/usr/include/unistd.h:722: warning: shadowed declaration is here
In file included from <command line>:15:
mygtk.h:394: error: syntax error before "GtkItemFactoryEntry"
xfprot-gtk.c:938: error: syntax error before "xfprot_menu_items"
xfprot-gtk.c:938: warning: type defaults to `int' in declaration of `xfprot_menu_items'
xfprot-gtk.c:939: warning: braces around scalar initializer
xfprot-gtk.c:939: warning: (near initialization for `xfprot_menu_items[0]')
xfprot-gtk.c:939: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:939: warning: excess elements in scalar initializer
xfprot-gtk.c:939: warning: (near initialization for `xfprot_menu_items[0]')
xfprot-gtk.c:939: warning: excess elements in scalar initializer
xfprot-gtk.c:939: warning: (near initialization for `xfprot_menu_items[0]')
xfprot-gtk.c:939: warning: excess elements in scalar initializer
xfprot-gtk.c:939: warning: (near initialization for `xfprot_menu_items[0]')
xfprot-gtk.c:939: warning: excess elements in scalar initializer
xfprot-gtk.c:939: warning: (near initialization for `xfprot_menu_items[0]')
xfprot-gtk.c:939: warning: excess elements in scalar initializer
xfprot-gtk.c:939: warning: (near initialization for `xfprot_menu_items[0]')
xfprot-gtk.c:940: warning: braces around scalar initializer
xfprot-gtk.c:940: warning: (near initialization for `xfprot_menu_items[1]')
xfprot-gtk.c:940: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:940: warning: excess elements in scalar initializer
xfprot-gtk.c:940: warning: (near initialization for `xfprot_menu_items[1]')
xfprot-gtk.c:940: warning: excess elements in scalar initializer
xfprot-gtk.c:940: warning: (near initialization for `xfprot_menu_items[1]')
xfprot-gtk.c:940: warning: excess elements in scalar initializer
xfprot-gtk.c:940: warning: (near initialization for `xfprot_menu_items[1]')
xfprot-gtk.c:940: warning: excess elements in scalar initializer
xfprot-gtk.c:940: warning: (near initialization for `xfprot_menu_items[1]')
xfprot-gtk.c:940: warning: excess elements in scalar initializer
xfprot-gtk.c:940: warning: (near initialization for `xfprot_menu_items[1]')
xfprot-gtk.c:941: warning: braces around scalar initializer
xfprot-gtk.c:941: warning: (near initialization for `xfprot_menu_items[2]')
xfprot-gtk.c:941: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:941: warning: excess elements in scalar initializer
xfprot-gtk.c:941: warning: (near initialization for `xfprot_menu_items[2]')
xfprot-gtk.c:941: warning: excess elements in scalar initializer
xfprot-gtk.c:941: warning: (near initialization for `xfprot_menu_items[2]')
xfprot-gtk.c:941: warning: excess elements in scalar initializer
xfprot-gtk.c:941: warning: (near initialization for `xfprot_menu_items[2]')
xfprot-gtk.c:941: warning: excess elements in scalar initializer
xfprot-gtk.c:941: warning: (near initialization for `xfprot_menu_items[2]')
xfprot-gtk.c:941: warning: excess elements in scalar initializer
xfprot-gtk.c:941: warning: (near initialization for `xfprot_menu_items[2]')
xfprot-gtk.c:942: warning: braces around scalar initializer
xfprot-gtk.c:942: warning: (near initialization for `xfprot_menu_items[3]')
xfprot-gtk.c:942: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:942: warning: excess elements in scalar initializer
xfprot-gtk.c:942: warning: (near initialization for `xfprot_menu_items[3]')
xfprot-gtk.c:942: warning: excess elements in scalar initializer
xfprot-gtk.c:942: warning: (near initialization for `xfprot_menu_items[3]')
xfprot-gtk.c:942: warning: excess elements in scalar initializer
xfprot-gtk.c:942: warning: (near initialization for `xfprot_menu_items[3]')
xfprot-gtk.c:942: warning: excess elements in scalar initializer
xfprot-gtk.c:942: warning: (near initialization for `xfprot_menu_items[3]')
xfprot-gtk.c:942: warning: excess elements in scalar initializer
xfprot-gtk.c:942: warning: (near initialization for `xfprot_menu_items[3]')
xfprot-gtk.c:943: warning: braces around scalar initializer
xfprot-gtk.c:943: warning: (near initialization for `xfprot_menu_items[4]')
xfprot-gtk.c:943: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:943: warning: excess elements in scalar initializer
xfprot-gtk.c:943: warning: (near initialization for `xfprot_menu_items[4]')
xfprot-gtk.c:943: warning: excess elements in scalar initializer
xfprot-gtk.c:943: warning: (near initialization for `xfprot_menu_items[4]')
xfprot-gtk.c:943: warning: excess elements in scalar initializer
xfprot-gtk.c:943: warning: (near initialization for `xfprot_menu_items[4]')
xfprot-gtk.c:943: warning: excess elements in scalar initializer
xfprot-gtk.c:943: warning: (near initialization for `xfprot_menu_items[4]')
xfprot-gtk.c:943: warning: excess elements in scalar initializer
xfprot-gtk.c:943: warning: (near initialization for `xfprot_menu_items[4]')
xfprot-gtk.c:944: warning: braces around scalar initializer
xfprot-gtk.c:944: warning: (near initialization for `xfprot_menu_items[5]')
xfprot-gtk.c:944: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:944: warning: excess elements in scalar initializer
xfprot-gtk.c:944: warning: (near initialization for `xfprot_menu_items[5]')
xfprot-gtk.c:944: warning: excess elements in scalar initializer
xfprot-gtk.c:944: warning: (near initialization for `xfprot_menu_items[5]')
xfprot-gtk.c:944: warning: excess elements in scalar initializer
xfprot-gtk.c:944: warning: (near initialization for `xfprot_menu_items[5]')
xfprot-gtk.c:944: warning: excess elements in scalar initializer
xfprot-gtk.c:944: warning: (near initialization for `xfprot_menu_items[5]')
xfprot-gtk.c:944: warning: excess elements in scalar initializer
xfprot-gtk.c:944: warning: (near initialization for `xfprot_menu_items[5]')
xfprot-gtk.c:945: warning: braces around scalar initializer
xfprot-gtk.c:945: warning: (near initialization for `xfprot_menu_items[6]')
xfprot-gtk.c:945: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:945: warning: excess elements in scalar initializer
xfprot-gtk.c:945: warning: (near initialization for `xfprot_menu_items[6]')
xfprot-gtk.c:945: warning: excess elements in scalar initializer
xfprot-gtk.c:945: warning: (near initialization for `xfprot_menu_items[6]')
xfprot-gtk.c:945: warning: excess elements in scalar initializer
xfprot-gtk.c:945: warning: (near initialization for `xfprot_menu_items[6]')
xfprot-gtk.c:945: warning: excess elements in scalar initializer
xfprot-gtk.c:945: warning: (near initialization for `xfprot_menu_items[6]')
xfprot-gtk.c:945: warning: excess elements in scalar initializer
xfprot-gtk.c:945: warning: (near initialization for `xfprot_menu_items[6]')
xfprot-gtk.c:946: warning: braces around scalar initializer
xfprot-gtk.c:946: warning: (near initialization for `xfprot_menu_items[7]')
xfprot-gtk.c:946: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:946: warning: excess elements in scalar initializer
xfprot-gtk.c:946: warning: (near initialization for `xfprot_menu_items[7]')
xfprot-gtk.c:946: warning: excess elements in scalar initializer
xfprot-gtk.c:946: warning: (near initialization for `xfprot_menu_items[7]')
xfprot-gtk.c:946: warning: excess elements in scalar initializer
xfprot-gtk.c:946: warning: (near initialization for `xfprot_menu_items[7]')
xfprot-gtk.c:946: warning: excess elements in scalar initializer
xfprot-gtk.c:946: warning: (near initialization for `xfprot_menu_items[7]')
xfprot-gtk.c:946: warning: excess elements in scalar initializer
xfprot-gtk.c:946: warning: (near initialization for `xfprot_menu_items[7]')
xfprot-gtk.c:947: warning: braces around scalar initializer
xfprot-gtk.c:947: warning: (near initialization for `xfprot_menu_items[8]')
xfprot-gtk.c:947: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:947: warning: excess elements in scalar initializer
xfprot-gtk.c:947: warning: (near initialization for `xfprot_menu_items[8]')
xfprot-gtk.c:947: warning: excess elements in scalar initializer
xfprot-gtk.c:947: warning: (near initialization for `xfprot_menu_items[8]')
xfprot-gtk.c:947: warning: excess elements in scalar initializer
xfprot-gtk.c:947: warning: (near initialization for `xfprot_menu_items[8]')
xfprot-gtk.c:947: warning: excess elements in scalar initializer
xfprot-gtk.c:947: warning: (near initialization for `xfprot_menu_items[8]')
xfprot-gtk.c:947: warning: excess elements in scalar initializer
xfprot-gtk.c:947: warning: (near initialization for `xfprot_menu_items[8]')
xfprot-gtk.c:948: warning: braces around scalar initializer
xfprot-gtk.c:948: warning: (near initialization for `xfprot_menu_items[9]')
xfprot-gtk.c:948: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:948: warning: excess elements in scalar initializer
xfprot-gtk.c:948: warning: (near initialization for `xfprot_menu_items[9]')
xfprot-gtk.c:948: warning: excess elements in scalar initializer
xfprot-gtk.c:948: warning: (near initialization for `xfprot_menu_items[9]')
xfprot-gtk.c:948: warning: excess elements in scalar initializer
xfprot-gtk.c:948: warning: (near initialization for `xfprot_menu_items[9]')
xfprot-gtk.c:948: warning: excess elements in scalar initializer
xfprot-gtk.c:948: warning: (near initialization for `xfprot_menu_items[9]')
xfprot-gtk.c:948: warning: excess elements in scalar initializer
xfprot-gtk.c:948: warning: (near initialization for `xfprot_menu_items[9]')
xfprot-gtk.c:949: warning: braces around scalar initializer
xfprot-gtk.c:949: warning: (near initialization for `xfprot_menu_items[10]')
xfprot-gtk.c:949: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:949: warning: excess elements in scalar initializer
xfprot-gtk.c:949: warning: (near initialization for `xfprot_menu_items[10]')
xfprot-gtk.c:949: warning: excess elements in scalar initializer
xfprot-gtk.c:949: warning: (near initialization for `xfprot_menu_items[10]')
xfprot-gtk.c:949: warning: excess elements in scalar initializer
xfprot-gtk.c:949: warning: (near initialization for `xfprot_menu_items[10]')
xfprot-gtk.c:949: warning: excess elements in scalar initializer
xfprot-gtk.c:949: warning: (near initialization for `xfprot_menu_items[10]')
xfprot-gtk.c:949: warning: excess elements in scalar initializer
xfprot-gtk.c:949: warning: (near initialization for `xfprot_menu_items[10]')
xfprot-gtk.c:950: warning: braces around scalar initializer
xfprot-gtk.c:950: warning: (near initialization for `xfprot_menu_items[11]')
xfprot-gtk.c:950: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:950: warning: excess elements in scalar initializer
xfprot-gtk.c:950: warning: (near initialization for `xfprot_menu_items[11]')
xfprot-gtk.c:950: warning: excess elements in scalar initializer
xfprot-gtk.c:950: warning: (near initialization for `xfprot_menu_items[11]')
xfprot-gtk.c:950: warning: excess elements in scalar initializer
xfprot-gtk.c:950: warning: (near initialization for `xfprot_menu_items[11]')
xfprot-gtk.c:950: warning: excess elements in scalar initializer
xfprot-gtk.c:950: warning: (near initialization for `xfprot_menu_items[11]')
xfprot-gtk.c:950: warning: excess elements in scalar initializer
xfprot-gtk.c:950: warning: (near initialization for `xfprot_menu_items[11]')
xfprot-gtk.c:951: warning: braces around scalar initializer
xfprot-gtk.c:951: warning: (near initialization for `xfprot_menu_items[12]')
xfprot-gtk.c:951: warning: initialization makes integer from pointer without a cast
xfprot-gtk.c:951: warning: excess elements in scalar initializer
xfprot-gtk.c:951: warning: (near initialization for `xfprot_menu_items[12]')
xfprot-gtk.c:951: warning: excess elements in scalar initializer
xfprot-gtk.c:951: warning: (near initialization for `xfprot_menu_items[12]')
xfprot-gtk.c:951: warning: excess elements in scalar initializer
xfprot-gtk.c:951: warning: (near initialization for `xfprot_menu_items[12]')
xfprot-gtk.c:951: warning: excess elements in scalar initializer
xfprot-gtk.c:951: warning: (near initialization for `xfprot_menu_items[12]')
xfprot-gtk.c:951: warning: excess elements in scalar initializer
xfprot-gtk.c:951: warning: (near initialization for `xfprot_menu_items[12]')
xfprot-gtk.c:953: error: ISO C forbids data definition with no type or storage class
xfprot-gtk.c: In function `main':
xfprot-gtk.c:1172: error: `GtkItemFactoryEntry' undeclared (first use in this function)
xfprot-gtk.c:1172: error: (Each undeclared identifier is reported only once
xfprot-gtk.c:1172: error: for each function it appears in.)
xfprot-gtk.c:1172: error: syntax error before ')' token
make: *** [xfprot-gtk.o] Error 1

---

### Post by A-star on 2005-02-24
When I do ./configure, I get the following error:
```

Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Checking for su.....OK

Using default values for f-prot's install directory: /usr/local/f-prot

If you experience problems with the default settings try
the --autodetect switch or change them by editing manually config.h.

Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for xterm.....OK
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
You have to install the Gtk+ 1.x  or Gtk+2.x devel libraries
filip@star1:~/xfprot-1.9 $ make
cc -DIS_LINUX -include mylib.h -include mygtk.h -include config.h -include xfprot.h  -c -o xfprot-gtk.o xfprot-gtk.c
make: execvp: cc: Permission denied
make: *** [xfprot-gtk.o] Error 127

```
Any help?

---

### Post by Perfect Storm on 2005-02-27
Install libgtk2.0-dev from Synaptic Package Management.

---

### Post by hamil on 2005-02-27
Hello there!

Pretty newbie, tryed to install f-prot, it worked fine.
But when I get to the Xfprot, i get an errormessage I really dont understand. 

lars@nautilus:~/xfprot-1.9 $ make
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -c -o xfprot-gtk.o xfprot-gtk.c
make: cc: Command not found
make: *** [xfprot-gtk.o] Error 127

Anyone have any ideas what this means?

I made sure that gtk2 devel is installed, toghter with a bunch of other gtk libraries etc.


Thanx
Lars

---

### Post by Sapper2ID on 2005-03-02
Install went fine and all seems to function fine also. When I click on update I'm asked for my password. I never saw a chance to input a password and when I try mine is says it's a bad psswrd. ???? I can manually update using  "sudo /usr/local/f-prot/tools/check-updates.pl " I haven't found a way to change the word either.

---

### Post by Perfect Storm on 2005-03-05
[QUOTE=hamil]Hello there!

Pretty newbie, tryed to install f-prot, it worked fine.
But when I get to the Xfprot, i get an errormessage I really dont understand. 

lars@nautilus:~/xfprot-1.9 $ make
cc -DIS_LINUX -DDEBUG  -Wall -Wunused -Wshadow -Wmissing-noreturn -Wunused-function  -Wunused-label  -Wunused-parameter -Wunused-value  -Wunused-variable  -pedantic  -O2 -fno-builtin -std=gnu99 -include i18n/en_GB.h -D_en_GB -include mylib.h -include mygtk.h -include config.h -include xfprot.h -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DUSE_GTK_2_4 -DUSE_GTK_2_0 -c -o xfprot-gtk.o xfprot-gtk.c
make: cc: Command not found
make: *** [xfprot-gtk.o] Error 127

Anyone have any ideas what this means?

I made sure that gtk2 devel is installed, toghter with a bunch of other gtk libraries etc.


Thanx
Lars[/QUOTE]

You need 'gcc'

---

### Post by Bogart on 2005-03-28
[QUOTE=NeoChaosX]I keep getting a blank error message whenever I try to run XFProt 1.9.  Is there something I did wrong?[/QUOTE]

The same with me. Everything went fine, I installed f-prot and it works. Then installed the gui and it went ok. But when I open it I get a window saying error, but with no message at all. Any ideas?

---

### Post by mesocool on 2005-03-29
When I tried to dpkg fp-linux-ws.deb, it asked me libwww-perl. When I install libwww-perl, I asked me something else. When I got that, it asked me something new again.. And I cannot see libwww-perl from package manager and I get it online..  O:) 

> 
root@Home:/home/joseph/Desktop/AntiVirus # sudo dpkg -i  fp-linux-ws.deb
Selecting previously deselected package fp-linux-ws.
(Reading database ... 70821 files and directories currently installed.)
Unpacking fp-linux-ws (from fp-linux-ws.deb) ...
dpkg: dependency problems prevent configuration of fp-linux-ws:
 fp-linux-ws depends on libwww-perl; however:
  Package libwww-perl is not installed.
dpkg: error processing fp-linux-ws (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fp-linux-ws
root@Home:/home/joseph/Desktop/AntiVirus # web [http://ftp.us.debian.org/debian/pool/main/libw/libwww-perl/libwww-perl_5.64-1_all.deb](http://ftp.us.debian.org/debian/pool/main/libw/libwww-perl/libwww-perl_5.64-1_all.deb)
bash: web: command not found
root@Home:/home/joseph/Desktop/AntiVirus # wget [http://ftp.us.debian.org/debian/pool/main/libw/libwww-perl/libwww-perl_5.64-1_all.deb](http://ftp.us.debian.org/debian/pool/main/libw/libwww-perl/libwww-perl_5.64-1_all.deb)
--12:24:56--  [http://ftp.us.debian.org/debian/pool/main/libw/libwww-perl/libwww-perl_5.64-1_all.deb](http://ftp.us.debian.org/debian/pool/main/libw/libwww-perl/libwww-perl_5.64-1_all.deb)
           => `libwww-perl_5.64-1_all.deb'
Resolving ftp.us.debian.org... 128.101.80.133, 204.152.189.120, 208.185.25.35, ...
Connecting to ftp.us.debian.org[128.101.80.133]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 293,062 [application/x-debian-package]

100%[====================================>] 293,062        4.74K/s    ETA 00:00

12:25:58 (4.72 KB/s) - `libwww-perl_5.64-1_all.deb' saved [293062/293062]

root@Home:/home/joseph/Desktop/AntiVirus # dpkg -i libwww*
Selecting previously deselected package libwww-perl.
(Reading database ... 70866 files and directories currently installed.)
Unpacking libwww-perl (from libwww-perl_5.64-1_all.deb) ...
dpkg: dependency problems prevent configuration of libwww-perl:
 libwww-perl depends on libnet-perl (>= 1:1.09); however:
  Package libnet-perl is not installed.
 libwww-perl depends on libmime-base64-perl (>= 2.1); however:
  Package libmime-base64-perl is not installed.
 libwww-perl depends on liburi-perl (>= 1.10); however:
  Package liburi-perl is not installed.
 libwww-perl depends on libhtml-parser-perl (>= 2.20); however:
  Package libhtml-parser-perl is not installed.
 libwww-perl depends on libhtml-tree-perl (>= 3.11); however:
  Package libhtml-tree-perl is not installed.
dpkg: error processing libwww-perl (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libwww-perl



---

### Post by cfa on 2005-03-29
i done a deb package tell me if is working or not :

[http://rapidshare.de/files/1054722/xfprot-1.10_1.10-1_i386.deb.html](http://rapidshare.de/files/1054722/xfprot-1.10_1.10-1_i386.deb.html)

c ya  8)

---

### Post by mesocool on 2005-03-29
Where is file menu ----> Create launcher at?

---

### Post by mesocool on 2005-03-29
I got it.. It works well. Thx..

But why my UI is not as nice as yours??  :-k

---

### Post by cfa on 2005-03-29
sorry but you have to make the menu entry yourself  :-( 

newt time maybe !

---

### Post by Perfect Storm on 2005-08-01
People who want's to install it should check this thread:

[http://www.ubuntuforums.org/showthread.php?t=25421](http://www.ubuntuforums.org/showthread.php?t=25421)

Though it's on 5.04 it works as well on 4.10
I'm to lazy to update two threads :P

---


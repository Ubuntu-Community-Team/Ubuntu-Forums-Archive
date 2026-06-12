---
title: "gedit IDE hack"
date: 2011-08-11
forum: Programming Talk
---

### Post by mr bob on 2011-08-11
Hi,

Recently I decided to review which IDE I wished to use. I prefer lightweights IDE with plugins and so my choice ended up between Geany (which I have been using for a couple of years) and Gedit which I now prefer because of its snippets and the ability to write plugins in python.

However, I also want to use gedit as a simple text editor too. So I have hacked gedit to create a separate application that:

a) runs as a separate instance of gedit (called geditIDE).
b) has it's own profile (using a sub-directory in gconf) - therefore opening with and remembering different preferences.
c) has a separate menu place.

Here is the quick hack. It works for me but I can't guarantee it will work for others. I recommend you only try this if you know what you are doing

1) Download the source of the version of gedit you wish to hack from here: [http://ftp.acc.umu.se/pub/GNOME/sources/gedit/](http://ftp.acc.umu.se/pub/GNOME/sources/gedit/)

I'm using the stable version of gedit on Ubuntu and Mint - 2.30.4

2) Make the changes to the files. 

2.1) First replace all references to the application menu file "gedit.desktop" with "geditIDE.desktop".

You need to find and replace these in ./configure and data/Makefile.am.

2.2) I have listed all other file changes in the diff file below:
```

diff -r gedit-2.30.4/configure geditIDE-2.30.4/configure
564c564
< PACKAGE_NAME='gedit'
---
> PACKAGE_NAME='geditIDE'
567c567
< PACKAGE_STRING='gedit 2.30.4'
---
> PACKAGE_STRING='geditIDE 2.30.4'
diff -r gedit-2.30.4/gedit/gedit.c geditIDE-2.30.4/gedit/gedit.c
626c626
< 	connection = bacon_message_connection_new ("gedit");
---
> 	connection = bacon_message_connection_new ("geditIDE");
diff -r gedit-2.30.4/gedit/gedit-prefs-manager.h geditIDE-2.30.4/gedit/gedit-prefs-manager.h
38c38
< #define GEDIT_BASE_KEY	"/apps/gedit-2"
---
> #define GEDIT_BASE_KEY	"/apps/gedit-2/IDE"
diff -r gedit-2.30.4/gedit/gedit-window.c geditIDE-2.30.4/gedit/gedit-window.c
2206c2206
< 		gedit_osx_set_window_title (window, "gedit", NULL);
---
> 		gedit_osx_set_window_title (window, "geditIDE", NULL);
2208c2208
< 		gtk_window_set_title (GTK_WINDOW (window), "gedit");
---
> 		gtk_window_set_title (GTK_WINDOW (window), "geditIDE");
2269c2269
< 			title = g_strdup_printf ("%s [%s] (%s) - gedit", 
---
> 			title = g_strdup_printf ("%s [%s] (%s) - geditIDE", 
2274c2274
< 			title = g_strdup_printf ("%s [%s] - gedit", 
---
> 			title = g_strdup_printf ("%s [%s] - geditIDE", 
2281c2281
< 			title = g_strdup_printf ("%s (%s) - gedit", 
---
> 			title = g_strdup_printf ("%s (%s) - geditIDE", 
2285c2285
< 			title = g_strdup_printf ("%s - gedit", 
---
> 			title = g_strdup_printf ("%s - geditIDE", 
diff -r gedit-2.30.4/gedit/Makefile.am geditIDE-2.30.4/gedit/Makefile.am
8c8
< bin_PROGRAMS = gedit
---
> bin_PROGRAMS = geditIDE
diff -r gedit-2.30.4/gedit/Makefile.in geditIDE-2.30.4/gedit/Makefile.in
40c40
< bin_PROGRAMS = gedit$(EXEEXT)
---
> bin_PROGRAMS = geditIDE$(EXEEXT)
659,660c659,660
< gedit$(EXEEXT): $(gedit_OBJECTS) $(gedit_DEPENDENCIES) 
< 	@rm -f gedit$(EXEEXT)
---
> geditIDE$(EXEEXT): $(gedit_OBJECTS) $(gedit_DEPENDENCIES) 
> 	@rm -f geditIDE$(EXEEXT)

```

It is probably worth copying and pasting the above diff file into your own diff file.

3) Now create geditIDE.desktop.in and geditIDE.desktop.in.in in the data folder and copy and paste the text below:

```

[Desktop Entry]
_Name=geditIDE
_GenericName=Integrated Development Environment
_Comment=gedit IDE hack
Exec=geditIDE %U
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;text/x-chdr;text/x-csrc;text/x-c++hdr;text/x-c++src;text/x-java;text/x-dsrc;text/x-pascal;text/x-perl;text/x-python;application/x-php;application/x-httpd-php3;application/x-httpd-php4;application/x-httpd-php5;application/xml;text/html;text/css;text/x-sql;text/x-diff;
Icon=accessories-text-editor
Categories=GNOME;GTK;Development;IDE;
X-GNOME-DocPath=gedit/gedit.xml
_X-GNOME-FullName=gedit IDE
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit IDE
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.4
X-GNOME-Bugzilla-ExtraInfoScript=/usr/libexec/gedit-2/gedit-bugreport.sh

```


4) Then perform the usual process to install from the source:
```

./configure
make
sudo make install

```

4.1) The configuration may fail if other packages are needed. You may need to install these required packages before configuring.

```

sudo apt-get install intltool
sudo apt-get install libenchant-dev
sudo apt-get install libxml2-dev
sudo apt-get install libgtk2.0-dev
sudo apt-get install libgtksourceview2.0-dev
sudo apt-get install libgconf2-dev

```

This should have installed geditIDE. 

5) The application is likely to be installed into /usr/local/bin. 

To be able to use the gedit plugins already installed, it is necessary to create links to the current gedit plugin directory:

```

cd /usr/local/share/gedit-2
sudo rm -rf plugins
sudo ln -s /usr/share/gedit-2/plugins
cd /usr/local/lib/gedit-2
sudo rm -rf plugin*
sudo ln -s /usr/lib/gedit-2/plugin-loaders
sudo ln -s /usr/lib/gedit-2/plugins

```

6) If the menu doesn't display geditIDE, you may have to copy the .desktop file:

```

sudo cp /usr/local/share/applications/geditIDE.desktop /usr/share/applications/

```


***********************************************************************

Explanation of the code changes:

1) Replacing "gedit.desktop" with "geditIDE.desktop" in ./configure and data/Makefile.am

This will to point to new application menu files that will be installed as geditIDE.desktop. This file will contain the change in name and comment and will reside in the "Development" or "Programming" sub menu.

2) Changing the application name in configuration and make

in ./configure
```

PACKAGE_NAME='geditIDE'
...
PACKAGE_STRING='geditIDE 2.30.4'

```

in gedit/Makefile.am
```

bin_PROGRAMS = geditIDE

```

in gedit/Makefile.in
```

bin_PROGRAMS = geditIDE$(EXEEXT)
....
geditIDE$(EXEEXT): $(gedit_OBJECTS) $(gedit_DEPENDENCIES) 
	@rm -f geditIDE$(EXEEXT)

```

3) Creating a separate instance for geditIDE, so that gedit and geditIDE can run simultaneously

in gedit.c:main()
```

connection = bacon_message_connection_new ("geditIDE");

```

4) Creating a separate "profile" for geditIDE, by creating the gconf subdirectory /apps/gedit-2/IDE

in gedit-prefs-manager.h
```

#define GEDIT_BASE_KEY	"/apps/gedit-2/IDE"

```

5) Changing the main window name from gedit to geditIDE

in gedit-window.c:set_title() change all occurrences of "gedit" to "geditIDE"


***********************************************************************

If anybody wishes to create a proper patch that would be great but I don't have the time unfortunately.

Hope this helps though, regards Mr Bob

---


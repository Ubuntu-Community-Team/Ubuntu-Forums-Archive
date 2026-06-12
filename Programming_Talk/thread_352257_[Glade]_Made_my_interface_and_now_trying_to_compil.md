---
title: "[Glade] Made my interface and now trying to compile - need some help"
date: 2007-02-03
forum: Programming Talk
---

### Post by faraazs on 2007-02-03
I've made my interface with glade and want to play around with some stuff and so I am trying to compile the program loading the xml with libglade directly as this is how people have been telling me to do it. However, when I try to compile I am receiving these errors:```
$ g++ main.cpp
g++: gtk2: No such file or directory
g++: pkg-config -cflags -libs gtk+2.0: No such file or directory
main.cpp:1:21: error: gtk/gtk.h: No such file or directory
main.cpp:2:25: error: glade/glade.h: No such file or directory

```There are obviously more but are only a result of the compiler not being able to locate these files. I've installed libgtk2.0-dev and libgnome2-dev and am now at a loss as to why the compiler can't find these files. Does it have to do with my PATH settings? Funny thing is, I can compile programs from source just fine...

Any help is much appreciated...

---

I got it to remove the gtk error with using g++ -Wall -g main.cpp `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0` as the build command. I just need to know now the stuff for glade. I can figure out the pkg-config stuff on my own I guess.

---

Got it to work. Thanks :).

---

### Post by lazka on 2007-02-03
`pkg-config libglade-2.0 --cflags` and `pkg-config libglade-2.0 --libs`

if someone is looking for the same thing..

---

### Post by lnostdal on 2007-02-03
you can do this ```
pkg-config --list-all
``` to see all libraries you can use with pkg-config .. for instance ```
pgk-config --list-all | grep glade
```

you can also type ```
pkg-config --cflags --libs libglade-2.0
``` which will give you both compiler and linker flags in one go

---

### Post by faraazs on 2007-02-03
Thanks for all the help :). This is the second time you have helped me in such a short time :D. Thanks :).

I got everything to work and everything compiles smoothly. I just have two questions now...I try to run the program and get an error that it's expecting a gtk-interface and got a glade-interface. I found a tutorial that uses a gtk interface and so I used that instead and changed the mainwindow to load first and all went well, so how do I get the output interface and the one the program is looking for to sync up properly? Here is the compile command:```
g++ main.cpp -o gAthan `libglade-config --cflags --libs`
```

Secondly, how will all of this fall together in compiling from source from people who download my program? Right now, only a standalone file is being made, so should I just move this to like /usr/bin or something to be launched by commandline? And will I have to distribute the .glade file when packaging this?

---

### Post by lnostdal on 2007-02-03
i'm having a hard time understanding you; could you post the complete source code + glade file and the command(s) you use to compile? 

edit: ..or if you can just the minimal code and stuff necessary to show the problem?

---

### Post by faraazs on 2007-02-03
Source code is still pretty basic right now. I'm just trying to get a feel of what is going on before actually making a lot of changes and additions:```
#include <gtk/gtk.h>
#include <glade/glade.h>

int main(int argc, char *argv[])
{
	GladeXML *xml;
	
	//glade_init();
	gtk_init(&argc, &argv);

	/* load the interface */
	xml = glade_xml_new("gAthan.glade", "mainWindow");

	/* connect the signals in the interface */
	glade_xml_signal_autoconnect(xml);

	/* start the event loop */
	gtk_main();

	return 0;
}

```Here is my .glade file as well:```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--*- mode: xml -*-->
<glade-interface>
  <widget class="GtkWindow" id="mainWindow">
    <property name="visible">True</property>
    <property name="title" translatable="yes">gAthan v1.0</property>
    <property name="resizable">False</property>
    <child>
      <widget class="GtkFixed" id="fixed1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkMenuBar" id="menubar1">
            <property name="width_request">736</property>
            <property name="height_request">27</property>
            <property name="visible">True</property>
            <child>
              <widget class="GtkMenuItem" id="menuitem1">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_File</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="menu1">
                    <property name="visible">True</property>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem1">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">gtk-new</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem2">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">gtk-open</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem3">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">gtk-save</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem4">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">gtk-save-as</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkSeparatorMenuItem" id="separatormenuitem1">
                        <property name="visible">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem5">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">gtk-quit</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
            <child>
              <widget class="GtkMenuItem" id="menuitem2">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_Edit</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="menu2">
                    <property name="visible">True</property>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem6">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">gtk-cut</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem7">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">gtk-copy</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem8">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">gtk-paste</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem9">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">gtk-delete</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
            <child>
              <widget class="GtkMenuItem" id="menuitem3">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_View</property>
                <property name="use_underline">True</property>
              </widget>
            </child>
            <child>
              <widget class="GtkMenuItem" id="menuitem4">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_Help</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="menu3">
                    <property name="visible">True</property>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem10">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">gtk-about</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
          </widget>
        </child>
        <child>
          <widget class="GtkStatusbar" id="statusbar1">
            <property name="width_request">736</property>
            <property name="height_request">20</property>
            <property name="visible">True</property>
            <property name="has_resize_grip">False</property>
          </widget>
          <packing>
            <property name="y">375</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```The error I get is this:```
** WARNING **: Expecting GTK-Interface.  Got glade-interface
Message: *** 'property' tag found while in state WIDGET_CHILD_ATTRIBUTE
Message: *** 'child' tag found while in state WIDGET_CHILD_ATTRIBUTE
Message: *** 'child' tag found while in state WIDGET_CHILD_ATTRIBUTE

** CRITICAL **: file glade-xml.c: line 1148 (glade_xml_build_interface): assertion `wid != NULL' failed.
```It hasnt even gotten to parsing the xml because its not in the first format...

---

Ok, you are going to think I am an idiot, which I probably am, but using your help earlier I got it to work. Thanks dude :). Sorry for all the trouble.

---

### Post by lnostdal on 2007-02-03
hm .. i'm not sure what's causing that .. i did change some minor things and the code looks like:

```

/*
  gcc -std=c99 -Wall -g `pkg-config --libs --cflags gtk+-2.0` `pkg-config --libs --cflags libglade-2.0` gtk-test.c -o gtk-test
*/
  
#include <gtk/gtk.h>
#include <glade/glade.h>

int main(int argc, char *argv[])
{
  GladeXML *xml;
  
  //glade_init();
  gtk_init(&argc, &argv);
  
  /* load the interface */
  xml = glade_xml_new("gAthan.glade", NULL, NULL);
  
  /* connect the signals in the interface */
  glade_xml_signal_autoconnect(xml);
  
  /* start the event loop */
  gtk_main();
  
  return 0;
}

```

(i've also stated how i compile the thing in a comment at the top)

---

### Post by faraazs on 2007-02-03
Yeah I got it to work...sorry about all the trouble :(.

---


---
title: "Simple glade program doesn't work"
date: 2008-04-28
forum: Programming Talk
---

### Post by skip mcshwang on 2008-04-28
Hi all,

I'm just starting to learn glade and so I wrote this little program:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <gtk/gtk.h>
#include <gdk/gdkx.h>
#include <glade/glade.h>

int main(int argc, char **argv)
{

	GladeXML *xml;

	printf("starting window1\n");

	gtk_init(&argc, &argv);

	if (!(xml = glade_xml_new("test.glade", "window1", 0)))
	{
	   printf("window1 failed to load\n");
	}

	glade_xml_signal_autoconnect(xml);

	gtk_main();

	return 0;

}
```

When I run it, it does this:

```
skip@skip-desktop:~/Projects/c++/test$ ./test
starting window1

```

It just sits there, no dialog box appears and I have to press ^C. Am I missing something? Here's the test.glade if it helps:

```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.2 on Mon Apr 28 15:18:02 2008 -->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <property name="title" translatable="yes">Hello World</property>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <property name="border_width">4</property>
        <property name="spacing">4</property>
        <child>
          <widget class="GtkLabel" id="label1">
            <property name="visible">True</property>
            <property name="label" translatable="yes">Enter your name:</property>
          </widget>
        </child>
        <child>
          <widget class="GtkEntry" id="entry1">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <property name="border_width">4</property>
            <property name="spacing">4</property>
            <property name="homogeneous">True</property>
            <child>
              <widget class="GtkButton" id="button1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">gtk-apply</property>
                <property name="use_stock">True</property>
                <property name="response_id">0</property>
              </widget>
            </child>
            <child>
              <widget class="GtkButton" id="button2">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">gtk-close</property>
                <property name="use_stock">True</property>
                <property name="response_id">0</property>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

---

### Post by RIchard James13 on 2008-04-28
When you use glade 3 it doesn't make the parent window visible by default. You need to change that value in your glade file. It a property of the main window under the common tab named visible. The other way to do it is to tell glade/gtk to make the window visible at run time. Currently I am not using Glade in C/C++ just GTK and I can't compile your code so I can't remember the specific way to tell it to be visible.

---

### Post by skip mcshwang on 2008-04-28
Doh!! Thanks Richard, that was it.

---

### Post by samjh on 2008-04-28
> **RIchard James13 said:**
> When you use glade 3 it doesn't make the parent window visible by default. You need to change that value in your glade file.

When I first used Glade 3, it took me hours to figure that one out! :)

That sort of feature-change should be clearly documented, but alas no... :(

---


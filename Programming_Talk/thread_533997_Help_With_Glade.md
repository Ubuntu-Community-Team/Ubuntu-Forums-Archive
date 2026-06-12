---
title: "Help With Glade"
date: 2007-08-24
forum: Programming Talk
---

### Post by charlie763 on 2007-08-24
I would like to create a feature matrix for a program I am developing, [Gladex]("http://www.openphysics.org/~gladex/"). For consistency, I would like the matrix to look like the one in gparted in the attached screenshot. Since we are using libglade for a GUI I need to make this in glade, but I'm not sure how to do it. None of the widgets seem to be the right ones. Would anyone be able to help me out? It would be ideal if someone would whip up something similar in Glade, so I can take a look at how it's set up. Thank.

---

### Post by christhemonkey on 2007-08-24
Something like this....

---

### Post by charlie763 on 2007-08-24
Ah, treeview. Thanks.

---

### Post by slavik on 2007-08-24
my own experimentation with glade treeview: creates 2 columns of stuff:

[SIZE="5"]**PERL CODE**[/SIZE]

```

#!/usr/bin/perl -w

#       treeview.pl
#
#       Copyright 2007 Vyacheslav Goltser <slavik@slavik-gx620>
#
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 3 of the License, or
#       (at your option) any later version.
#
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.

use strict;
use Gtk2::GladeXML;
use Gtk2 -init;
my $passwd; #file ref to the passwd file

my $app = new Gtk2::GladeXML("treeview.glade");
$app->signal_autoconnect_from_package("cb");

### Populate the treeview ...
open $passwd, "/etc/passwd";
my %users = map { $_ =~ /^(.*?)(?::.*?)+:(.*?):.*?/gis } <$passwd>;
close $passwd;

my $list_store = new Gtk2::ListStore("Glib::String","Glib::String");

for (keys %users) {
	$list_store->set($list_store->append,0,$_,1,$users{$_});
}

my $tv = $app->get_widget("treeview1");

my $renderer = new Gtk2::CellRendererText;
my $tvc = Gtk2::TreeViewColumn->new_with_attributes("User Name",$renderer,"text",0);
$tvc->set_resizable(1);
$tvc->set_sort_column_id(0);
$tv->append_column($tvc);

$renderer = new Gtk2::CellRendererText;
$tvc = Gtk2::TreeViewColumn->new_with_attributes("Home Directory",$renderer,"text",1);
$tvc->set_resizable(1);
$tvc->set_sort_column_id(1);
$tv->append_column($tvc);

$tv->set_model($list_store);

Gtk2->main();

package cb;

sub quit_cb {
	Gtk2->main_quit();
	return 1;
}

```

[SIZE="5"]**AND THE GLADE XML FILE**[/SIZE]
```

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.2.0 on Tue Jul 24 22:16:32 2007 by slavik@slavik-desktop-->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <property name="width_request">640</property>
    <property name="height_request">480</property>
    <property name="visible">True</property>
    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
    <property name="title" translatable="yes">Named Zone Config</property>
    <signal name="delete_event" handler="quit_cb"/>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
        <child>
          <widget class="GtkMenuBar" id="menubar1">
            <property name="visible">True</property>
            <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
            <child>
              <widget class="GtkMenuItem" id="menuitem1">
                <property name="visible">True</property>
                <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                <property name="label" translatable="yes">_File</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="menu1">
                    <property name="visible">True</property>
                    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem1">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                        <property name="label" translatable="yes">gtk-new</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem2">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                        <property name="label" translatable="yes">gtk-open</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem3">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                        <property name="label" translatable="yes">gtk-save</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem4">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                        <property name="label" translatable="yes">gtk-save-as</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkSeparatorMenuItem" id="separatormenuitem1">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem5">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
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
                <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                <property name="label" translatable="yes">_Edit</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="menu2">
                    <property name="visible">True</property>
                    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem6">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                        <property name="label" translatable="yes">gtk-cut</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem7">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                        <property name="label" translatable="yes">gtk-copy</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem8">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                        <property name="label" translatable="yes">gtk-paste</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem9">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
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
                <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                <property name="label" translatable="yes">_View</property>
                <property name="use_underline">True</property>
              </widget>
            </child>
            <child>
              <widget class="GtkMenuItem" id="menuitem4">
                <property name="visible">True</property>
                <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                <property name="label" translatable="yes">_Help</property>
                <property name="use_underline">True</property>
                <child>
                  <widget class="GtkMenu" id="menu3">
                    <property name="visible">True</property>
                    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem10">
                        <property name="visible">True</property>
                        <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
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
          <packing>
            <property name="expand">False</property>
          </packing>
        </child>
        <child>
          <widget class="GtkScrolledWindow" id="scrolledwindow1">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
            <property name="hscrollbar_policy">GTK_POLICY_AUTOMATIC</property>
            <property name="vscrollbar_policy">GTK_POLICY_AUTOMATIC</property>
            <child>
              <widget class="GtkTreeView" id="treeview1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                <property name="headers_clickable">True</property>
              </widget>
            </child>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

---

### Post by charlie763 on 2007-08-25
Thanks, slavik, that really helped. :)

---


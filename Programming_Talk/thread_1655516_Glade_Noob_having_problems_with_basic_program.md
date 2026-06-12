---
title: "Glade Noob having problems with basic program"
date: 2010-12-29
forum: Programming Talk
---

### Post by Newbie2910 on 2010-12-29
Much experience with WPF but just starting to play with Glade and GTK+.

Using Monodevelop, I put together a basic app:

using System;
using Gtk;
using Glade;


namespace XS
{
    public class GladeApp
    {
        public static void Main (string[] args)
        {
                new GladeApp (args);
        }
 
        public GladeApp (string[] args) 
        {
                Application.Init();
 
                Glade.XML gxml = new Glade.XML (null, "window1.glade", "window1", null);

                gxml.Autoconnect (this);
                Application.Run();
        }
    }
}

And I created a Glade file (window1.glade) and using the Glade editor and saved it in a folder named Resources.

I added window1.glade to the project and set it's build options as "embed as resource".

But when I go to run the app, I get an error:
   Cannot get resource file 'window1.glade'
   Parameter name: resource_name

on this line:
   Glade.XML gxml = new Glade.XML (null, "window1.glade", "window1", null);

I have tried this with window1.glade saved in all of the projects various folders (and fresh Rebuild Alls), but same result.  What am I doing wrong here?

Thanks.  Using 10.04LTS.

---

### Post by MadCow108 on 2010-12-29
wild guess (as I am not very familiar with with C# and gtk):
glade offers you the possibility to save as a gtkbuilder format or libglade format.
Your code seems to use libglade variant, if the file is gtkbuilder format it won't recognize it.

(I think gtkbuilder is the recommended way)

---

### Post by Newbie2910 on 2010-12-29
Well, I checked and my Glade project is set as Libglade.

I tried this:

Glade.XML gxml = new Glade.XML (null, "XS.Resources.window1.glade", "window1", null);

because the ResourceID is actually XS.Resources.window1.glade.

Now, I get past that error but nothing ever shows up on the screen.

Contents of the window1.glade file:
<?xml version="1.0"?>
<glade-interface>
  <!-- interface-requires gtk+ 2.16 -->
  <!-- interface-naming-policy project-wide -->
  <widget class="GtkWindow" id="window1">
    <property name="border_width">5</property>
    <property name="title" translatable="yes">XS</property>
    <property name="default_width">100</property>
    <property name="default_height">200</property>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <placeholder/>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <child>
              <widget class="GtkVBox" id="vbox2">
                <property name="visible">True</property>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <widget class="GtkTreeView" id="treeview1">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                  </widget>
                  <packing>
                    <property name="position">1</property>
                  </packing>
                </child>
                <child>
                  <placeholder/>
                </child>
              </widget>
              <packing>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <widget class="GtkVBox" id="vbox3">
                <property name="visible">True</property>
                <child>
                  <widget class="GtkHBox" id="hbox2">
                    <property name="visible">True</property>
                    <child>
                      <placeholder/>
                    </child>
                    <child>
                      <widget class="GtkVBox" id="vbox4">
                        <property name="visible">True</property>
                        <child>
                          <placeholder/>
                        </child>
                        <child>
                          <widget class="GtkLayout" id="layout1">
                            <property name="visible">True</property>
                          </widget>
                          <packing>
                            <property name="position">1</property>
                          </packing>
                        </child>
                      </widget>
                      <packing>
                        <property name="position">1</property>
                      </packing>
                    </child>
                  </widget>
                  <packing>
                    <property name="position">0</property>
                  </packing>
                </child>
                <child>
                  <placeholder/>
                </child>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <widget class="GtkTable" id="table1">
                <property name="visible">True</property>
                <property name="n_rows">10</property>
                <property name="n_columns">2</property>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <placeholder/>
                </child>
              </widget>
              <packing>
                <property name="position">2</property>
              </packing>
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


(just some empty layout stuff.  I did set the window size to some fixed values since there aren't really any controls defined anywhere).

and the Main.cs file:
using System;
using Gtk;
using Glade;


namespace XS
{
    public class GladeApp
    {
        public static void Main (string[] args)
        {
                new GladeApp (args);
        }
 
        public GladeApp (string[] args) 
        {
                Application.Init();
 
                Glade.XML gxml = new Glade.XML (null, "XS.Resources.window1.glade", "window1", null);

                gxml.Autoconnect (this);
                Application.Run();
        }
    }
}

shouldn't I at least see something show up on the screen?

---

### Post by Newbie2910 on 2010-12-29
Went back and rechecked the visibility of the Window, somehow it got set to No.  Changed to Yes and now it's working.

---

### Post by bruce89 on 2010-12-29
I implore you to not use the libglade format and instead use Gtk.Builder (I guessed the name).

---


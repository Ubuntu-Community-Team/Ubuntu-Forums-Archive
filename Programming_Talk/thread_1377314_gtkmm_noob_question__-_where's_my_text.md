---
title: "gtkmm noob question  - where's my text?"
date: 2010-01-10
forum: Programming Talk
---

### Post by pootle1 on 2010-01-10
Just starting to use gtkmm / glade for the first time.

My little app starts up OK, and the text initialised in the glade file appears in the textaea OK, but when I update the text buffer, it never appears on the screen.  What should I do to flush the output?

At the top level my app is just sitting in run for the Gtk::main object.  I can pop up and close a new dialogue box (file open for example) OK as well.

here's the glade file:```

<?xml version="1.0"?>
<glade-interface>
  <!-- interface-requires gtk+ 2.16 -->
  <!-- interface-naming-policy project-wide -->
  <widget class="GtkWindow" id="topwin">
    <property name="visible">True</property>
    <property name="border_width">3</property>
    <property name="title" translatable="yes">Iain's raw zero proggy</property>
    <property name="default_width">600</property>
    <property name="default_height">400</property>
    <signal name="destroy" handler="gtk_main_quit"/>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <property name="orientation">vertical</property>
        <child>
          <widget class="GtkMenuBar" id="menubar1">
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
                        <property name="label">gtk-new</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem2">
                        <property name="label">gtk-open</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem3">
                        <property name="label">gtk-save</property>
                        <property name="visible">True</property>
                        <property name="sensitive">False</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem4">
                        <property name="label">gtk-save-as</property>
                        <property name="visible">True</property>
                        <property name="sensitive">False</property>
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
                        <property name="label">gtk-quit</property>
                        <property name="visible">True</property>
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
                        <property name="label">gtk-cut</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem7">
                        <property name="label">gtk-copy</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem8">
                        <property name="label">gtk-paste</property>
                        <property name="visible">True</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </widget>
                    </child>
                    <child>
                      <widget class="GtkImageMenuItem" id="imagemenuitem9">
                        <property name="label">gtk-delete</property>
                        <property name="visible">True</property>
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
                        <property name="label">gtk-about</property>
                        <property name="visible">True</property>
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
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkTextView" id="textview1">
            <property name="visible">True</property>
            <property name="sensitive">False</property>
            <property name="can_focus">True</property>
            <property name="double_buffered">False</property>
            <property name="text" translatable="yes">willy wonka's chocolate factory</property>
          </widget>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
        <child>
          <widget class="GtkStatusbar" id="statusbar1">
            <property name="visible">True</property>
            <property name="double_buffered">False</property>
            <property name="spacing">2</property>
            <property name="has_resize_grip">False</property>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="pack_type">end</property>
            <property name="position">0</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
  <widget class="GtkFileChooserDialog" id="filechooserdialog1">
    <property name="border_width">5</property>
    <property name="modal">True</property>
    <property name="type_hint">normal</property>
    <property name="has_separator">False</property>
    <child internal-child="vbox">
      <widget class="GtkVBox" id="dialog-vbox1">
        <property name="visible">True</property>
        <property name="orientation">vertical</property>
        <property name="spacing">2</property>
        <child>
          <placeholder/>
        </child>
        <child internal-child="action_area">
          <widget class="GtkHButtonBox" id="dialog-action_area1">
            <property name="visible">True</property>
            <property name="layout_style">end</property>
            <child>
              <widget class="GtkButton" id="fcd2">
                <property name="label">gtk-cancel</property>
                <property name="response_id">-6</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="has_default">True</property>
                <property name="receives_default">True</property>
                <property name="use_stock">True</property>
                <signal name="clicked" handler="gtk_false" after="yes"/>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <widget class="GtkButton" id="fcd1">
                <property name="label">gtk-ok</property>
                <property name="response_id">-5</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="has_default">True</property>
                <property name="receives_default">True</property>
                <property name="use_stock">True</property>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="pack_type">end</property>
            <property name="position">0</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

---

### Post by SledgeHammer_999 on 2010-01-10
> **pootle1 said:**
> but when I update the text buffer, it never appears on the screen.

What do you mean by that? How do you "update the buffer"? (example code)

---

### Post by pootle1 on 2010-01-10
I've attached an archive of all the source files, but the bit in question (I think) is in the constructor in the dervied class from textview:
```
tiffWin::tiffWin(GtkTextView* cobject,
                   const Glib::RefPtr<Gnome::Glade::Xml>& glade_xml)
                   : text1Win(cobject, glade_xml) {
  info = get_buffer();
  printf("first I have:%s:",info->get_text().c_str());
  info->set_text("buffer starts again");
  set_buffer(info);
}
```The wierd thing I've noticed since first post is that the printf statement shows the text set in the following statement as well! - but the text itself never appears in the textview window.

It's been a bit messy trying to use gtkmm with glade - most examples and tutorials I've found are either glade with C, or gtkmm with C++, but not many with all 3!, so its probably just me misunderstanding something

---

### Post by SledgeHammer_999 on 2010-01-10
I never have used gtkmm with glade. Only pure gtkmm. I did look however your code. It doesn't **seem** to do something wrong. After a little tinkering with the compiled program it seems that the textview isn't being updated. Eg I open menu and close it the menu's *drop-down image** stays above the textview. But the textview's text gets displayed above the drop-down image. This is odd. Moreover the text gets darker and darker after some time passes, as if it is constantly being painted. I'll provide a screeshot.

Maybe try your luck with the gtkmm irc and mailing list(provide the same code and glade file). Or maybe there is a bug in glademm.

---

### Post by pootle1 on 2010-01-10
Will do, thanks for that, always useful to have another pair of eyes look for anything stupid.

I don't get anything like your screenshot by the way - the menu seems to behave fine and disappears as soon as something selected., that's something for another day I think..

---


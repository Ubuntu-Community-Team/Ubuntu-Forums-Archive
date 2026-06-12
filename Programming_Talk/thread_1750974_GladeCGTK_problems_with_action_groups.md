---
title: "Glade/C/GTK problems with action groups"
date: 2011-05-06
forum: Programming Talk
---

### Post by r-senior on 2011-05-06
I've been playing around with Glade, creating a simple little GUI. When I create action groups and put actions in them, then link those to menu items and toolbar buttons, I get one of these errors for each action that I have in an action group:

```
Gtk-CRITICAL **: IA__gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
```

Any keyboard accelerators I set up on the actions don't seem to take effect. The program runs OK and I can set up keyboard accelerators directly on the menu items.

Any ideas? Here is my Glade file:

```
<?xml version="1.0" encoding="UTF-8"?>
<interface>
  <requires lib="gtk+" version="2.24"/>
  <!-- interface-requires gtksourceview 0.0 -->
  <!-- interface-naming-policy project-wide -->
  <object class="GtkAction" id="action_about">
    <property name="label" translatable="yes">About</property>
    <property name="tooltip" translatable="yes">Displays information about this program</property>
    <property name="stock_id">gtk-about</property>
    <signal name="activate" handler="on_action_about_activate" swapped="no"/>
  </object>
  <object class="GtkAction" id="action_jump_to">
    <property name="label" translatable="yes">Jump to line</property>
    <property name="short_label" translatable="yes">Jump</property>
    <property name="stock_id">gtk-jump-to</property>
    <signal name="activate" handler="on_action_jump_to_activate" swapped="no"/>
  </object>
  <object class="GtkAction" id="action_new">
    <property name="label" translatable="yes">New</property>
    <property name="tooltip" translatable="yes">Create a new document</property>
    <property name="stock_id">gtk-new</property>
    <signal name="activate" handler="on_action_new_activate" swapped="no"/>
  </object>
  <object class="GtkAction" id="action_open">
    <property name="label" translatable="yes">Open</property>
    <property name="tooltip" translatable="yes">Open an existing file</property>
    <property name="stock_id">gtk-open</property>
    <signal name="activate" handler="on_action_open_activate" swapped="no"/>
  </object>
  <object class="GtkAction" id="action_quit">
    <property name="label" translatable="yes">Quit</property>
    <property name="tooltip" translatable="yes">Quits the application</property>
    <property name="stock_id">gtk-quit</property>
    <property name="is_important">True</property>
    <signal name="activate" handler="on_action_quit_activate" swapped="no"/>
  </object>
  <object class="GtkAction" id="action_save">
    <property name="label" translatable="yes">Save</property>
    <property name="short_label" translatable="yes">Save</property>
    <property name="tooltip" translatable="yes">Save the current document</property>
    <property name="stock_id">gtk-save</property>
    <signal name="activate" handler="on_action_save_activate" swapped="no"/>
  </object>
  <object class="GtkAction" id="action_save_as">
    <property name="label" translatable="yes">Save As</property>
    <property name="tooltip" translatable="yes">Save the current file under a different name</property>
    <property name="stock_id">gtk-save-as</property>
    <signal name="activate" handler="on_action_save_as_activate" swapped="no"/>
  </object>
  <object class="GtkActionGroup" id="actions_clip">
    <child>
      <object class="GtkAction" id="action_paste">
        <property name="label" translatable="yes">Paste</property>
        <property name="tooltip" translatable="yes">Pastes the text from the clipboard</property>
        <property name="stock_id">gtk-paste</property>
        <signal name="activate" handler="on_action_paste_activate" swapped="no"/>
      </object>
      <accelerator key="v" modifiers="GDK_CONTROL_MASK"/>
    </child>
  </object>
  <object class="GtkActionGroup" id="actions_selection">
    <child>
      <object class="GtkAction" id="action_copy">
        <property name="label" translatable="yes">Copy</property>
        <property name="tooltip" translatable="yes">Copies the selected text to the clipboard</property>
        <property name="stock_id">gtk-copy</property>
        <signal name="activate" handler="on_action_copy_activate" swapped="no"/>
      </object>
    </child>
    <child>
      <object class="GtkAction" id="action_cut">
        <property name="label" translatable="yes">Cut</property>
        <property name="tooltip" translatable="yes">Cuts the selected text to the clipboard</property>
        <property name="stock_id">gtk-cut</property>
        <signal name="activate" handler="on_action_cut_activate" swapped="no"/>
      </object>
    </child>
    <child>
      <object class="GtkAction" id="action_delete">
        <property name="label" translatable="yes">Delete</property>
        <property name="tooltip" translatable="yes">Deletes the selected text</property>
        <property name="stock_id">gtk-delete</property>
        <signal name="activate" handler="on_action_delete_activate" swapped="no"/>
      </object>
    </child>
  </object>
  <object class="GtkTextBuffer" id="textbuffer">
    <signal name="changed" handler="on_textbuffer_changed" swapped="no"/>
  </object>
  <object class="GtkWindow" id="window">
    <property name="can_focus">False</property>
    <property name="title" translatable="yes">Ted</property>
    <property name="default_width">800</property>
    <property name="default_height">600</property>
    <property name="icon">ted.svg</property>
    <signal name="delete-event" handler="on_window_delete_event" swapped="no"/>
    <child>
      <object class="GtkVBox" id="vbox">
        <property name="visible">True</property>
        <property name="can_focus">False</property>
        <child>
          <object class="GtkMenuBar" id="menubar">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <child>
              <object class="GtkMenuItem" id="menuitem_file">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="use_action_appearance">False</property>
                <property name="label" translatable="yes">_File</property>
                <property name="use_underline">True</property>
                <child type="submenu">
                  <object class="GtkMenu" id="menu_file">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <child>
                      <object class="GtkImageMenuItem" id="menuitem_new">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_new</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <accelerator key="n" signal="activate" modifiers="GDK_CONTROL_MASK"/>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="menuitem_open">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_open</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <accelerator key="o" signal="activate" modifiers="GDK_CONTROL_MASK"/>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="menuitem_save">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_save</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <accelerator key="s" signal="activate" modifiers="GDK_CONTROL_MASK"/>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="menuitem_save_as">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_save_as</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <accelerator key="s" signal="activate" modifiers="GDK_SHIFT_MASK | GDK_CONTROL_MASK"/>
                      </object>
                    </child>
                    <child>
                      <object class="GtkSeparatorMenuItem" id="separatormenuitem1">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="use_action_appearance">False</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="menuitem_quit">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_quit</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <accelerator key="q" signal="activate" modifiers="GDK_CONTROL_MASK"/>
                      </object>
                    </child>
                  </object>
                </child>
              </object>
            </child>
            <child>
              <object class="GtkMenuItem" id="menuitem_edit">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="use_action_appearance">False</property>
                <property name="label" translatable="yes">_Edit</property>
                <property name="use_underline">True</property>
                <child type="submenu">
                  <object class="GtkMenu" id="menu_edit">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <child>
                      <object class="GtkImageMenuItem" id="menuitem_cut">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_cut</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <accelerator key="x" signal="activate" modifiers="GDK_CONTROL_MASK"/>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="menuitem_copy">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_copy</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <accelerator key="c" signal="activate" modifiers="GDK_CONTROL_MASK"/>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="menuitem_paste">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_paste</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <accelerator key="v" signal="activate" modifiers="GDK_CONTROL_MASK"/>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="menuitem_delete">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_delete</property>
                        <property name="use_stock">True</property>
                        <accelerator key="Delete" signal="activate"/>
                      </object>
                    </child>
                    <child>
                      <object class="GtkSeparatorMenuItem" id="menuitem1">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="use_action_appearance">False</property>
                      </object>
                    </child>
                    <child>
                      <object class="GtkImageMenuItem" id="gtk-jump-to">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_jump_to</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                        <accelerator key="i" signal="activate" modifiers="GDK_CONTROL_MASK"/>
                      </object>
                    </child>
                  </object>
                </child>
              </object>
            </child>
            <child>
              <object class="GtkMenuItem" id="menuitem_sep1">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="use_action_appearance">False</property>
                <property name="label" translatable="yes">_View</property>
                <property name="use_underline">True</property>
              </object>
            </child>
            <child>
              <object class="GtkMenuItem" id="menuitem_help">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="use_action_appearance">False</property>
                <property name="label" translatable="yes">_Help</property>
                <child type="submenu">
                  <object class="GtkMenu" id="menu_help">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <child>
                      <object class="GtkImageMenuItem" id="menuitem_about">
                        <property name="visible">True</property>
                        <property name="can_focus">False</property>
                        <property name="related_action">action_about</property>
                        <property name="use_underline">True</property>
                        <property name="use_stock">True</property>
                      </object>
                    </child>
                  </object>
                </child>
              </object>
            </child>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkToolbar" id="toolbar">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <property name="toolbar_style">both</property>
            <child>
              <object class="GtkToolButton" id="toolbutton_new">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="related_action">action_new</property>
                <property name="label" translatable="yes">New</property>
                <property name="use_underline">True</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkToolButton" id="toolbutton_open">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="related_action">action_open</property>
                <property name="label" translatable="yes">Open</property>
                <property name="use_underline">True</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkToolButton" id="toolbutton_save">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="related_action">action_save</property>
                <property name="label" translatable="yes">Save</property>
                <property name="use_underline">True</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkToolButton" id="toolbutton_save_as">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="related_action">action_save_as</property>
                <property name="label" translatable="yes">toolbutton1</property>
                <property name="use_underline">True</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkSeparatorToolItem" id="toolbutton_sep1">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="use_action_appearance">False</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkToolButton" id="Cut">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="related_action">action_cut</property>
                <property name="label" translatable="yes">toolbutton1</property>
                <property name="use_underline">True</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkToolButton" id="Copy">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="related_action">action_copy</property>
                <property name="label" translatable="yes">toolbutton1</property>
                <property name="use_underline">True</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkToolButton" id="Paste">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="related_action">action_paste</property>
                <property name="label" translatable="yes">toolbutton1</property>
                <property name="use_underline">True</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkToolButton" id="Delete">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="related_action">action_delete</property>
                <property name="label" translatable="yes">toolbutton1</property>
                <property name="use_underline">True</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkSeparatorToolItem" id="&lt;separator&gt;">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="use_action_appearance">False</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkToolButton" id="Jump To">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="related_action">action_jump_to</property>
                <property name="label" translatable="yes">toolbutton1</property>
                <property name="use_underline">True</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="homogeneous">True</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <object class="GtkScrolledWindow" id="scrolled_window">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="hscrollbar_policy">automatic</property>
            <property name="vscrollbar_policy">automatic</property>
            <child>
              <object class="GtkSourceView" id="source_view">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="has_focus">True</property>
                <property name="left_margin">2</property>
                <property name="right_margin">2</property>
                <property name="buffer">textbuffer</property>
                <property name="show_line_numbers">True</property>
                <property name="auto_indent">True</property>
              </object>
            </child>
          </object>
          <packing>
            <property name="expand">True</property>
            <property name="fill">True</property>
            <property name="position">2</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>
```

---

### Post by r-senior on 2011-05-08
Bump on this - I've not found a solution yet - any ideas?

---


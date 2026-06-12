---
title: "Gtk-sharp and stetic action problem"
date: 2010-05-22
forum: Programming Talk
---

### Post by matmatmat on 2010-05-22
Hi, I've been developing with Mono, C# and gtk-sharp recently, I've hit a problem with actions. I want to have a toolbar with a button on and a menubar:

gui.stetic
```

<?xml version="1.0" encoding="utf-8"?>
<stetic-interface>
  <configuration>
    <images-root-path>..</images-root-path>
    <target-gtk-version>2.12</target-gtk-version>
  </configuration>
  <import>
    <widget-library name="glade-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f" />
    <widget-library name="gtksourceview2-sharp, Version=2.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f" />
    <widget-library name="../bin/Debug/Kronos.exe" internal="true" />
  </import>
  <widget class="Gtk.Window" id="Kronos.MainWindow" design-size="646 529">
    <action-group name="Default">
      <action id="addAction">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes" />
        <property name="StockId">gtk-add</property>
        <signal name="Activated" handler="OnAddActionActivated" />
      </action>
      <action id="FileAction">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">File</property>
        <property name="ShortLabel" translatable="yes">File</property>
      </action>
    </action-group>
    <property name="MemberName" />
    <property name="Title" translatable="yes">Kronos</property>
    <property name="WindowPosition">CenterOnParent</property>
    <signal name="DeleteEvent" handler="OnDeleteEvent" />
    <child>
      <widget class="Gtk.VBox" id="vbox3">
        <property name="MemberName" />
        <property name="Spacing">6</property>
        <child>
          <widget class="Gtk.MenuBar" id="menubar3">
            <property name="MemberName" />
            <node name="menubar3" type="Menubar">
              <node type="Menu" />
              <node type="Menu" action="FileAction" />
            </node>
          </widget>
          <packing>
            <property name="Position">0</property>
            <property name="AutoSize">True</property>
            <property name="Expand">False</property>
            <property name="Fill">False</property>
          </packing>
        </child>
        <child>
          <widget class="Gtk.Toolbar" id="toolbar1">
            <property name="MemberName" />
            <property name="ShowArrow">False</property>
            <property name="ButtonStyle">Icons</property>
            <property name="IconSize">LargeToolbar</property>
            <node name="__gtksharp_75_Stetic_Editor_ActionToolbar" type="Toolbar">
              <node type="Toolitem" />
              <node type="Toolitem" action="addAction" />
            </node>
          </widget>
          <packing>
            <property name="Position">1</property>
            <property name="AutoSize">True</property>
            <property name="Expand">False</property>
            <property name="Fill">False</property>
          </packing>
        </child>
        <child>
          <widget class="Gtk.VPaned" id="vpaned1">
            <property name="MemberName" />
            <property name="CanFocus">True</property>
            <property name="Position">153</property>
            <child>
              <widget class="Gtk.HBox" id="hbox1">
                <property name="MemberName" />
                <property name="Spacing">6</property>
                <child>
                  <widget class="Gtk.ScrolledWindow" id="scrolledwindow1">
                    <property name="MemberName" />
                    <property name="CanFocus">True</property>
                    <property name="ShadowType">In</property>
                    <child>
                      <widget class="Gtk.TreeView" id="treeviewLanguage">
                        <property name="MemberName" />
                        <property name="CanFocus">True</property>
                      </widget>
                    </child>
                  </widget>
                  <packing>
                    <property name="Position">0</property>
                    <property name="AutoSize">True</property>
                  </packing>
                </child>
                <child>
                  <widget class="Gtk.ScrolledWindow" id="scrolledwindow3">
                    <property name="MemberName" />
                    <property name="CanFocus">True</property>
                    <property name="ShadowType">In</property>
                    <child>
                      <widget class="Gtk.TreeView" id="treeviewName">
                        <property name="MemberName" />
                        <property name="CanFocus">True</property>
                      </widget>
                    </child>
                  </widget>
                  <packing>
                    <property name="Position">1</property>
                    <property name="AutoSize">True</property>
                  </packing>
                </child>
              </widget>
              <packing>
                <property name="Resize">False</property>
              </packing>
            </child>
            <child>
              <widget class="Gtk.VBox" id="vbox2">
                <property name="MemberName" />
                <property name="Spacing">6</property>
                <child>
                  <widget class="Gtk.Table" id="table1">
                    <property name="MemberName" />
                    <property name="NRows">3</property>
                    <property name="NColumns">2</property>
                    <property name="RowSpacing">6</property>
                    <property name="ColumnSpacing">6</property>
                    <child>
                      <widget class="Gtk.Entry" id="entryLanguage">
                        <property name="MemberName" />
                        <property name="CanFocus">True</property>
                        <property name="IsEditable">False</property>
                        <property name="InvisibleChar">&#9679;</property>
                      </widget>
                      <packing>
                        <property name="TopAttach">1</property>
                        <property name="BottomAttach">2</property>
                        <property name="LeftAttach">1</property>
                        <property name="RightAttach">2</property>
                        <property name="AutoSize">True</property>
                        <property name="YOptions">Fill</property>
                        <property name="XExpand">True</property>
                        <property name="XFill">True</property>
                        <property name="XShrink">False</property>
                        <property name="YExpand">False</property>
                        <property name="YFill">True</property>
                        <property name="YShrink">False</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="Gtk.Entry" id="entryName">
                        <property name="MemberName" />
                        <property name="CanFocus">True</property>
                        <property name="IsEditable">False</property>
                        <property name="InvisibleChar">&#9679;</property>
                      </widget>
                      <packing>
                        <property name="LeftAttach">1</property>
                        <property name="RightAttach">2</property>
                        <property name="AutoSize">True</property>
                        <property name="YOptions">Fill</property>
                        <property name="XExpand">True</property>
                        <property name="XFill">True</property>
                        <property name="XShrink">False</property>
                        <property name="YExpand">False</property>
                        <property name="YFill">True</property>
                        <property name="YShrink">False</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="Gtk.ScrolledWindow" id="GtkScrolledWindow">
                        <property name="MemberName" />
                        <property name="ShadowType">In</property>
                        <child>
                          <widget class="Gtk.TextView" id="textviewDescription">
                            <property name="MemberName" />
                            <property name="CanFocus">True</property>
                            <property name="ShowScrollbars">True</property>
                            <property name="Editable">False</property>
                            <property name="Text" translatable="yes" />
                          </widget>
                        </child>
                      </widget>
                      <packing>
                        <property name="TopAttach">2</property>
                        <property name="BottomAttach">3</property>
                        <property name="LeftAttach">1</property>
                        <property name="RightAttach">2</property>
                        <property name="AutoSize">True</property>
                        <property name="YOptions">Fill</property>
                        <property name="XExpand">True</property>
                        <property name="XFill">True</property>
                        <property name="XShrink">False</property>
                        <property name="YExpand">False</property>
                        <property name="YFill">True</property>
                        <property name="YShrink">False</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="Gtk.Label" id="label1">
                        <property name="MemberName" />
                        <property name="LabelProp" translatable="yes">Name</property>
                      </widget>
                      <packing>
                        <property name="AutoSize">True</property>
                        <property name="XOptions">Fill</property>
                        <property name="YOptions">Fill</property>
                        <property name="XExpand">False</property>
                        <property name="XFill">True</property>
                        <property name="XShrink">False</property>
                        <property name="YExpand">False</property>
                        <property name="YFill">True</property>
                        <property name="YShrink">False</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="Gtk.Label" id="label2">
                        <property name="MemberName" />
                        <property name="LabelProp" translatable="yes">Description</property>
                      </widget>
                      <packing>
                        <property name="TopAttach">2</property>
                        <property name="BottomAttach">3</property>
                        <property name="AutoSize">True</property>
                        <property name="XOptions">Fill</property>
                        <property name="YOptions">Fill</property>
                        <property name="XExpand">False</property>
                        <property name="XFill">True</property>
                        <property name="XShrink">False</property>
                        <property name="YExpand">False</property>
                        <property name="YFill">True</property>
                        <property name="YShrink">False</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="Gtk.Label" id="label3">
                        <property name="MemberName" />
                        <property name="LabelProp" translatable="yes">Language</property>
                      </widget>
                      <packing>
                        <property name="TopAttach">1</property>
                        <property name="BottomAttach">2</property>
                        <property name="AutoSize">True</property>
                        <property name="XOptions">Fill</property>
                        <property name="YOptions">Fill</property>
                        <property name="XExpand">False</property>
                        <property name="XFill">True</property>
                        <property name="XShrink">False</property>
                        <property name="YExpand">False</property>
                        <property name="YFill">True</property>
                        <property name="YShrink">False</property>
                      </packing>
                    </child>
                  </widget>
                  <packing>
                    <property name="Position">0</property>
                    <property name="AutoSize">True</property>
                    <property name="Expand">False</property>
                    <property name="Fill">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="Gtk.ScrolledWindow" id="scrolledwindowSource">
                    <property name="MemberName" />
                    <property name="CanFocus">True</property>
                    <property name="ShadowType">In</property>
                    <child>
                      <widget class="Gtk.Viewport" id="GtkViewport">
                        <property name="MemberName" />
                        <property name="ShadowType">None</property>
                        <child>
                          <placeholder />
                        </child>
                      </widget>
                    </child>
                  </widget>
                  <packing>
                    <property name="Position">1</property>
                    <property name="AutoSize">True</property>
                  </packing>
                </child>
              </widget>
            </child>
          </widget>
          <packing>
            <property name="Position">2</property>
            <property name="AutoSize">True</property>
          </packing>
        </child>
        <child>
          <widget class="Gtk.Statusbar" id="statusbar2">
            <property name="MemberName" />
            <property name="Spacing">6</property>
            <child>
              <placeholder />
            </child>
            <child>
              <placeholder />
            </child>
          </widget>
          <packing>
            <property name="Position">3</property>
            <property name="AutoSize">True</property>
            <property name="Expand">False</property>
            <property name="Fill">False</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
  <widget class="Gtk.Dialog" id="Kronos.AddDialog" design-size="441 483">
    <property name="MemberName" />
    <property name="Title" translatable="yes">Add snippet</property>
    <property name="WindowPosition">CenterOnParent</property>
    <property name="Buttons">2</property>
    <property name="HelpButton">False</property>
    <child internal-child="VBox">
      <widget class="Gtk.VBox" id="dialog1_VBox">
        <property name="MemberName" />
        <property name="BorderWidth">2</property>
        <child>
          <widget class="Gtk.VPaned" id="vpaned2">
            <property name="MemberName" />
            <property name="CanFocus">True</property>
            <property name="Position">211</property>
            <child>
              <widget class="Gtk.Table" id="table1">
                <property name="MemberName" />
                <property name="NRows">4</property>
                <property name="NColumns">2</property>
                <property name="RowSpacing">6</property>
                <property name="ColumnSpacing">6</property>
                <child>
                  <widget class="Gtk.Entry" id="entryName">
                    <property name="MemberName" />
                    <property name="CanFocus">True</property>
                    <property name="IsEditable">True</property>
                    <property name="InvisibleChar">&#9679;</property>
                  </widget>
                  <packing>
                    <property name="LeftAttach">1</property>
                    <property name="RightAttach">2</property>
                    <property name="AutoSize">True</property>
                    <property name="XOptions">Fill</property>
                    <property name="YOptions">Fill</property>
                    <property name="XExpand">False</property>
                    <property name="XFill">True</property>
                    <property name="XShrink">False</property>
                    <property name="YExpand">False</property>
                    <property name="YFill">True</property>
                    <property name="YShrink">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="Gtk.ScrolledWindow" id="GtkScrolledWindow">
                    <property name="MemberName" />
                    <property name="ShadowType">In</property>
                    <child>
                      <widget class="Gtk.TextView" id="textviewDescription">
                        <property name="MemberName" />
                        <property name="CanFocus">True</property>
                        <property name="ShowScrollbars">True</property>
                        <property name="Text" translatable="yes" />
                      </widget>
                    </child>
                  </widget>
                  <packing>
                    <property name="TopAttach">2</property>
                    <property name="BottomAttach">3</property>
                    <property name="LeftAttach">1</property>
                    <property name="RightAttach">2</property>
                    <property name="AutoSize">True</property>
                    <property name="XOptions">Fill</property>
                    <property name="YOptions">Fill</property>
                    <property name="XExpand">False</property>
                    <property name="XFill">True</property>
                    <property name="XShrink">False</property>
                    <property name="YExpand">False</property>
                    <property name="YFill">True</property>
                    <property name="YShrink">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="Gtk.HBox" id="hbox3">
                    <property name="MemberName" />
                    <property name="Spacing">6</property>
                    <child>
                      <widget class="Gtk.ComboBox" id="comboboxLanguage">
                        <property name="MemberName" />
                        <property name="IsTextCombo">True</property>
                        <property name="Items" translatable="yes" />
                      </widget>
                      <packing>
                        <property name="Position">0</property>
                        <property name="AutoSize">True</property>
                        <property name="Expand">False</property>
                        <property name="Fill">False</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="Gtk.Button" id="buttonLanguage">
                        <property name="MemberName" />
                        <property name="CanFocus">True</property>
                        <property name="UseStock">True</property>
                        <property name="Type">StockItem</property>
                        <property name="StockId">gtk-add</property>
                        <signal name="Clicked" handler="onButtonLanguageClicked" />
                        <property name="label">gtk-add</property>
                      </widget>
                      <packing>
                        <property name="Position">1</property>
                        <property name="AutoSize">True</property>
                        <property name="Expand">False</property>
                        <property name="Fill">False</property>
                      </packing>
                    </child>
                  </widget>
                  <packing>
                    <property name="TopAttach">1</property>
                    <property name="BottomAttach">2</property>
                    <property name="LeftAttach">1</property>
                    <property name="RightAttach">2</property>
                    <property name="AutoSize">True</property>
                    <property name="XOptions">Fill</property>
                    <property name="YOptions">Fill</property>
                    <property name="XExpand">False</property>
                    <property name="XFill">True</property>
                    <property name="XShrink">False</property>
                    <property name="YExpand">False</property>
                    <property name="YFill">True</property>
                    <property name="YShrink">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="Gtk.HBox" id="hbox4">
                    <property name="MemberName" />
                    <property name="Spacing">6</property>
                    <child>
                      <widget class="Gtk.Entry" id="entryNewitem">
                        <property name="MemberName" />
                        <property name="CanFocus">True</property>
                        <property name="IsEditable">True</property>
                        <property name="InvisibleChar">&#9679;</property>
                      </widget>
                      <packing>
                        <property name="Position">0</property>
                        <property name="AutoSize">True</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="Gtk.Button" id="buttonNewitem">
                        <property name="MemberName" />
                        <property name="CanFocus">True</property>
                        <property name="UseStock">True</property>
                        <property name="Type">StockItem</property>
                        <property name="StockId">gtk-add</property>
                        <signal name="Clicked" handler="onNewItemClicked" />
                        <property name="label">gtk-add</property>
                      </widget>
                      <packing>
                        <property name="Position">1</property>
                        <property name="AutoSize">True</property>
                        <property name="Expand">False</property>
                        <property name="Fill">False</property>
                      </packing>
                    </child>
                  </widget>
                  <packing>
                    <property name="TopAttach">3</property>
                    <property name="BottomAttach">4</property>
                    <property name="LeftAttach">1</property>
                    <property name="RightAttach">2</property>
                    <property name="AutoSize">True</property>
                    <property name="XOptions">Fill</property>
                    <property name="YOptions">Fill</property>
                    <property name="XExpand">False</property>
                    <property name="XFill">True</property>
                    <property name="XShrink">False</property>
                    <property name="YExpand">False</property>
                    <property name="YFill">True</property>
                    <property name="YShrink">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="Gtk.Label" id="label1">
                    <property name="MemberName" />
                    <property name="LabelProp" translatable="yes">Name</property>
                  </widget>
                  <packing>
                    <property name="AutoSize">True</property>
                    <property name="XOptions">Fill</property>
                    <property name="YOptions">Fill</property>
                    <property name="XExpand">False</property>
                    <property name="XFill">True</property>
                    <property name="XShrink">False</property>
                    <property name="YExpand">False</property>
                    <property name="YFill">True</property>
                    <property name="YShrink">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="Gtk.Label" id="label2">
                    <property name="MemberName" />
                    <property name="LabelProp" translatable="yes">Language</property>
                  </widget>
                  <packing>
                    <property name="TopAttach">1</property>
                    <property name="BottomAttach">2</property>
                    <property name="AutoSize">True</property>
                    <property name="XOptions">Fill</property>
                    <property name="YOptions">Fill</property>
                    <property name="XExpand">False</property>
                    <property name="XFill">True</property>
                    <property name="XShrink">False</property>
                    <property name="YExpand">False</property>
                    <property name="YFill">True</property>
                    <property name="YShrink">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="Gtk.Label" id="label3">
                    <property name="MemberName" />
                    <property name="LabelProp" translatable="yes">Description</property>
                  </widget>
                  <packing>
                    <property name="TopAttach">2</property>
                    <property name="BottomAttach">3</property>
                    <property name="AutoSize">True</property>
                    <property name="XOptions">Fill</property>
                    <property name="YOptions">Fill</property>
                    <property name="XExpand">False</property>
                    <property name="XFill">True</property>
                    <property name="XShrink">False</property>
                    <property name="YExpand">False</property>
                    <property name="YFill">True</property>
                    <property name="YShrink">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="Gtk.Label" id="label5">
                    <property name="MemberName" />
                    <property name="LabelProp" translatable="yes">New item</property>
                  </widget>
                  <packing>
                    <property name="TopAttach">3</property>
                    <property name="BottomAttach">4</property>
                    <property name="AutoSize">True</property>
                    <property name="XOptions">Fill</property>
                    <property name="YOptions">Fill</property>
                    <property name="XExpand">False</property>
                    <property name="XFill">True</property>
                    <property name="XShrink">False</property>
                    <property name="YExpand">False</property>
                    <property name="YFill">True</property>
                    <property name="YShrink">False</property>
                  </packing>
                </child>
              </widget>
              <packing>
                <property name="Resize">False</property>
              </packing>
            </child>
            <child>
              <widget class="Gtk.ScrolledWindow" id="scrolledwindowSource">
                <property name="MemberName" />
                <property name="CanFocus">True</property>
                <property name="ShadowType">In</property>
                <child>
                  <widget class="Gtk.Viewport" id="GtkViewport">
                    <property name="MemberName" />
                    <property name="ShadowType">None</property>
                    <child>
                      <placeholder />
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
          </widget>
          <packing>
            <property name="Position">0</property>
            <property name="AutoSize">True</property>
          </packing>
        </child>
      </widget>
    </child>
    <child internal-child="ActionArea">
      <widget class="Gtk.HButtonBox" id="dialog1_ActionArea">
        <property name="MemberName" />
        <property name="Spacing">10</property>
        <property name="BorderWidth">5</property>
        <property name="Size">2</property>
        <property name="LayoutStyle">End</property>
        <child>
          <widget class="Gtk.Button" id="buttonCancel">
            <property name="MemberName" />
            <property name="CanDefault">True</property>
            <property name="CanFocus">True</property>
            <property name="UseStock">True</property>
            <property name="Type">StockItem</property>
            <property name="StockId">gtk-cancel</property>
            <property name="ResponseId">-6</property>
            <signal name="Clicked" handler="onCancel" />
            <property name="label">gtk-cancel</property>
          </widget>
          <packing>
            <property name="Expand">False</property>
            <property name="Fill">False</property>
          </packing>
        </child>
        <child>
          <widget class="Gtk.Button" id="buttonOk">
            <property name="MemberName" />
            <property name="CanDefault">True</property>
            <property name="CanFocus">True</property>
            <property name="UseStock">True</property>
            <property name="Type">StockItem</property>
            <property name="StockId">gtk-ok</property>
            <property name="ResponseId">-5</property>
            <signal name="Clicked" handler="onOK" />
            <property name="label">gtk-ok</property>
          </widget>
          <packing>
            <property name="Position">1</property>
            <property name="Expand">False</property>
            <property name="Fill">False</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</stetic-interface>

```

As far as I can tell all the action names line up, but when I run it, it starts up with no button:
```

(K:2681): Gtk-WARNING **: menu: missing action (null)

(K:2681): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(K:2681): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(K:2681): Gtk-WARNING **: toolitem: missing action (null)

```

Can anyone tell me why?

---


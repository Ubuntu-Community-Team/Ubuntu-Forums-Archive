---
title: "Python change text in a GTK TextView"
date: 2014-09-07
forum: Programming Talk
---

### Post by saty2 on 2014-09-07
Ok, I'm kinda newb to GTK/Python
I have created a window using glade with a text view.

It displays fine, but when I show the window I would like to change the text in the text view.

I'm stuck as I don't know how to get an the text view and how to change it's text.
I have looked at as much docs as I can but still clueless

In fact i would like to display shell output in the textview1 which have been created using glade


Can you tell me how I can do this please

Here my code from file grov_ihm.ui

```
<?xml version="1.0" encoding="UTF-8"?>
<interface>
  <!-- interface-requires gtk+ 3.0 -->
  <object class="GtkDialog" id="window1">
    <property name="can_focus">False</property>
    <property name="border_width">5</property>
    <property name="title" translatable="yes">Disclaimer</property>
    <property name="window_position">center</property>
    <property name="type_hint">dialog</property>
    <child internal-child="vbox">
      <object class="GtkBox" id="dialog-vbox1">
        <property name="can_focus">False</property>
        <property name="orientation">vertical</property>
        <property name="spacing">2</property>
        <child internal-child="action_area">
          <object class="GtkButtonBox" id="dialog-action_area1">
            <property name="can_focus">False</property>
            <property name="layout_style">end</property>
            <child>
              <object class="GtkButton" id="button6">
                <property name="label" translatable="yes">I Agree</property>
                <property name="use_action_appearance">False</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="use_action_appearance">False</property>
                <signal name="clicked" handler="fct_btn_accept" swapped="no"/>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="fill">True</property>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkButton" id="button7">
                <property name="label" translatable="yes">Quit</property>
                <property name="use_action_appearance">False</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="use_action_appearance">False</property>
                <signal name="clicked" handler="fct_btn_quit" swapped="no"/>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="fill">True</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="pack_type">end</property>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkLabel" id="lab_disclaimer">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <property name="no_show_all">True</property>
            <property name="label" translatable="yes">Warranty Disclaimer</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="position">1</property>
          </packing>
        </child>
      </object>
    </child>
    <action-widgets>
      <action-widget response="0">button6</action-widget>
      <action-widget response="0">button7</action-widget>
    </action-widgets>
  </object>
  <object class="GtkWindow" id="window2">
    <property name="width_request">800</property>
    <property name="height_request">400</property>
    <property name="can_focus">False</property>
    <property name="title" translatable="yes">GROV Wireless Audit 1.0</property>
    <property name="role">GROV Wireless Audit 1.0</property>
    <property name="window_position">center</property>
    <property name="icon">grov_icon.png</property>
    <property name="icon_name">network-wireless</property>
    <child>
      <object class="GtkPaned" id="paned1">
        <property name="visible">True</property>
        <property name="can_focus">True</property>
        <property name="orientation">vertical</property>
        <child>
          <object class="GtkPaned" id="paned3">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <child>
              <object class="GtkBox" id="box1">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="orientation">vertical</property>
                <child>
                  <object class="GtkButton" id="btn_scan">
                    <property name="label" translatable="yes">Scan</property>
                    <property name="use_action_appearance">False</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <property name="hexpand">True</property>
                    <property name="vexpand">True</property>
                    <property name="use_action_appearance">False</property>
                    <signal name="clicked" handler="fct_btn_scan" swapped="no"/>
                  </object>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">True</property>
                    <property name="position">0</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkButton" id="btn_start">
                    <property name="label" translatable="yes">Start</property>
                    <property name="use_action_appearance">False</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <property name="hexpand">True</property>
                    <property name="vexpand">True</property>
                    <property name="use_action_appearance">False</property>
                    <signal name="clicked" handler="fct_btn_start" swapped="no"/>
                  </object>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">True</property>
                    <property name="position">1</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkSeparator" id="separator1">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <property name="valign">start</property>
                  </object>
                  <packing>
                    <property name="expand">True</property>
                    <property name="fill">False</property>
                    <property name="position">2</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkButton" id="btn_settings">
                    <property name="label" translatable="yes">Settings</property>
                    <property name="use_action_appearance">False</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <property name="hexpand">True</property>
                    <property name="vexpand">True</property>
                    <property name="use_action_appearance">False</property>
                    <signal name="clicked" handler="fct_btn_settings" swapped="no"/>
                  </object>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">True</property>
                    <property name="position">3</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkSeparator" id="separator2">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <property name="valign">start</property>
                  </object>
                  <packing>
                    <property name="expand">True</property>
                    <property name="fill">False</property>
                    <property name="position">6</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkButton" id="btn_help">
                    <property name="label" translatable="yes">Help</property>
                    <property name="use_action_appearance">False</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <property name="hexpand">True</property>
                    <property name="vexpand">True</property>
                    <property name="use_action_appearance">False</property>
                    <signal name="clicked" handler="fct_btn_help" swapped="no"/>
                  </object>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">True</property>
                    <property name="position">7</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkButton" id="btn_about">
                    <property name="label" translatable="yes">About</property>
                    <property name="use_action_appearance">False</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <property name="hexpand">True</property>
                    <property name="vexpand">True</property>
                    <property name="use_action_appearance">False</property>
                    <signal name="clicked" handler="fct_btn_about" swapped="no"/>
                  </object>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">True</property>
                    <property name="position">8</property>
                  </packing>
                </child>
              </object>
              <packing>
                <property name="resize">False</property>
                <property name="shrink">True</property>
              </packing>
            </child>
            <child>
              <object class="GtkGrid" id="grid2">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="row_spacing">5</property>
                <property name="column_spacing">5</property>
                <child>
                  [COLOR=#ff8c00]<object class="GtkTextView" id="textview1">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="margin_top">4</property>
                    <property name="hexpand">True</property>
                    <property name="vexpand">True</property>
                    <property name="editable">False</property>
                    <property name="cursor_visible">False</property>[/COLOR]
                  </object>
                  <packing>
                    <property name="left_attach">0</property>
                    <property name="top_attach">0</property>
                    <property name="width">1</property>
                    <property name="height">1</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkTextView" id="textview7">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="hexpand">True</property>
                    <property name="vexpand">True</property>
                    <property name="editable">False</property>
                    <property name="cursor_visible">False</property>
                  </object>
                  <packing>
                    <property name="left_attach">0</property>
                    <property name="top_attach">1</property>
                    <property name="width">1</property>
                    <property name="height">1</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkTextView" id="textview6">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="margin_top">4</property>
                    <property name="editable">False</property>
                    <property name="cursor_visible">False</property>
                  </object>
                  <packing>
                    <property name="left_attach">2</property>
                    <property name="top_attach">0</property>
                    <property name="width">1</property>
                    <property name="height">1</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkTextView" id="textview8">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="hexpand">True</property>
                    <property name="vexpand">True</property>
                    <property name="editable">False</property>
                    <property name="cursor_visible">False</property>
                  </object>
                  <packing>
                    <property name="left_attach">2</property>
                    <property name="top_attach">1</property>
                    <property name="width">1</property>
                    <property name="height">1</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkScrollbar" id="scrollbar1">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <property name="margin_top">5</property>
                    <property name="orientation">vertical</property>
                  </object>
                  <packing>
                    <property name="left_attach">1</property>
                    <property name="top_attach">0</property>
                    <property name="width">1</property>
                    <property name="height">1</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkScrollbar" id="scrollbar2">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <property name="orientation">vertical</property>
                  </object>
                  <packing>
                    <property name="left_attach">1</property>
                    <property name="top_attach">1</property>
                    <property name="width">1</property>
                    <property name="height">1</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkScrollbar" id="scrollbar3">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <property name="margin_right">4</property>
                    <property name="margin_top">4</property>
                    <property name="orientation">vertical</property>
                  </object>
                  <packing>
                    <property name="left_attach">3</property>
                    <property name="top_attach">0</property>
                    <property name="width">1</property>
                    <property name="height">1</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkScrollbar" id="scrollbar4">
                    <property name="visible">True</property>
                    <property name="can_focus">False</property>
                    <property name="margin_right">4</property>
                    <property name="orientation">vertical</property>
                  </object>
                  <packing>
                    <property name="left_attach">3</property>
                    <property name="top_attach">1</property>
                    <property name="width">1</property>
                    <property name="height">1</property>
                  </packing>
                </child>
              </object>
              <packing>
                <property name="resize">True</property>
                <property name="shrink">True</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="resize">False</property>
            <property name="shrink">True</property>
          </packing>
        </child>
        <child>
          <object class="GtkGrid" id="grid3">
            <property name="visible">True</property>
            <property name="sensitive">False</property>
            <property name="can_focus">False</property>
            <property name="hexpand">True</property>
            <property name="row_homogeneous">True</property>
            <child>
              <object class="GtkSpinner" id="spinner">
                <property name="width_request">25</property>
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="margin_left">67</property>
              </object>
              <packing>
                <property name="left_attach">0</property>
                <property name="top_attach">0</property>
                <property name="width">1</property>
                <property name="height">1</property>
              </packing>
            </child>
            <child>
              <object class="GtkStatusbar" id="statusbar1">
                <property name="visible">True</property>
                <property name="can_focus">False</property>
                <property name="hexpand">True</property>
                <property name="orientation">vertical</property>
                <property name="spacing">2</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="top_attach">0</property>
                <property name="width">1</property>
                <property name="height">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="resize">False</property>
            <property name="shrink">True</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
  <object class="GtkDialog" id="window4">
    <property name="can_focus">False</property>
    <property name="border_width">5</property>
    <property name="title" translatable="yes">About</property>
    <property name="window_position">center</property>
    <property name="type_hint">dialog</property>
    <child internal-child="vbox">
      <object class="GtkBox" id="dialog-vbox6">
        <property name="can_focus">False</property>
        <property name="orientation">vertical</property>
        <property name="spacing">2</property>
        <child internal-child="action_area">
          <object class="GtkButtonBox" id="dialog-action_area6">
            <property name="can_focus">False</property>
            <property name="layout_style">end</property>
            <child>
              <placeholder/>
            </child>
            <child>
              <object class="GtkButton" id="button4">
                <property name="label" translatable="yes">Quit</property>
                <property name="use_action_appearance">False</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="use_action_appearance">False</property>
                <signal name="clicked" handler="fct_btn_close" object="window4" swapped="no"/>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="fill">True</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="pack_type">end</property>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkLabel" id="lab_disclaimer2">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <property name="no_show_all">True</property>
            <property name="xalign">0.50999999046325684</property>
            <property name="yalign">0.46000000834465027</property>
            <property name="ypad">1</property>
            <property name="label" translatable="yes"> About</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="position">1</property>
          </packing>
        </child>
      </object>
    </child>
    <action-widgets>
      <action-widget response="0">button4</action-widget>
    </action-widgets>
  </object>
  <object class="GtkDialog" id="window5">
    <property name="can_focus">False</property>
    <property name="border_width">5</property>
    <property name="title" translatable="yes">Help</property>
    <property name="window_position">center</property>
    <property name="type_hint">dialog</property>
    <child internal-child="vbox">
      <object class="GtkBox" id="dialog-vbox3">
        <property name="can_focus">False</property>
        <property name="orientation">vertical</property>
        <property name="spacing">2</property>
        <child internal-child="action_area">
          <object class="GtkButtonBox" id="dialog-action_area3">
            <property name="can_focus">False</property>
            <property name="layout_style">end</property>
            <child>
              <placeholder/>
            </child>
            <child>
              <object class="GtkButton" id="button2">
                <property name="label" translatable="yes">Quit</property>
                <property name="use_action_appearance">False</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="use_action_appearance">False</property>
                <property name="xalign">0.5899999737739563</property>
                <property name="yalign">0.49000000953674316</property>
                <signal name="clicked" handler="fct_btn_close" object="window5" swapped="no"/>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="fill">True</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="pack_type">end</property>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkBox" id="box5">
            <property name="visible">True</property>
            <property name="can_focus">False</property>
            <property name="orientation">vertical</property>
            <child>
              <placeholder/>
            </child>
            <child>
              <object class="GtkLinkButton" id="linkbutton2">
                <property name="label" translatable="yes">Click here to read the manual</property>
                <property name="use_action_appearance">False</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="has_tooltip">True</property>
                <property name="use_action_appearance">False</property>
                <property name="yalign">0.49000000953674316</property>
                <signal name="activate-link" handler="fct_btn_link" swapped="no"/>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="fill">True</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="fill">True</property>
            <property name="position">1</property>
          </packing>
        </child>
      </object>
    </child>
    <action-widgets>
      <action-widget response="1">button2</action-widget>
    </action-widgets>
  </object>
</interface>


```

---


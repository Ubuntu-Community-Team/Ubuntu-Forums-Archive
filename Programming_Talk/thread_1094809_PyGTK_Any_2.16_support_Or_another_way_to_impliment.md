---
title: "PyGTK: Any 2.16 support? Or another way to impliment right click menu?"
date: 2009-03-13
forum: Programming Talk
---

### Post by smartboyathome on 2009-03-13
I need support for GtkBuilder 2.16, and Python doesn't seem to support it. Specifically, I want to make the GtkBuilder file below work. The reason I need GtkBuilder 2.16 is that it adds support for popup menus, which I need to use for a right click menu (unless there is another way???).

```
<!--
* Smartboy's Public License version 1.0
* Copyright (c) <year>, <copyright holder>
* All rights reserved.
*
* Redistribution and use in source and binary forms, with or without
* modification, are permitted provided that the following conditions are met:
*     * Redistributions of source code must be free of charge, and must
*       retain the above copyright notice, this list of conditions and the
*       following disclaimer.
*     * Redistributions in binary form must also provide the source code free
*       of charge, and must reproduce the above copyright notice, this list
*       of conditions and the following disclaimer in the documentation
*       and/or other materials provided with the distribution.
*     * Neither the name of <organization> nor the
*       names of its contributors may be used to endorse or promote products
*       derived from this software without specific prior written permission.
*
* THIS SOFTWARE IS PROVIDED BY <copyright holder> ''AS IS'' AND ANY
* EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
* WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
* DISCLAIMED. IN NO EVENT SHALL <copyright holder> BE LIABLE FOR ANY
* DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
* (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
* LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
* ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
* (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
* SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
-->
<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window">
    <property name="title">SmartStickies</property>
    <property name="default_width">250</property>
    <property name="default_height">250</property>
    <property name="decorated">False</property>
    <signal name="destroy" handler="on_window_destroy"/>
    <child>
      <object class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <object class="GtkScrolledWindow" id="scrolledwindow1">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="hscrollbar_policy">automatic</property>
            <property name="vscrollbar_policy">automatic</property>
            <child>
              <object class="GtkTextView" id="textview1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </object>
            </child>
          </object>
          <packing>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkStatusbar" id="statusbar1">
            <property name="visible">True</property>
            <property name="spacing">2</property>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="position">1</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
  <object class="GtkMenu" id="popup-menu">
    <property name="visible">True</property>
    <child>
      <object class="GtkMenuItem" id="menuitem-new">
        <property name="visible">True</property>
        <property name="has_tooltip">True</property>
        <property name="tooltip_text" translatable="yes">Create a new note.</property>
        <property name="label" translatable="yes">_New Note</property>
        <property name="use_underline">True</property>
      </object>
    </child>
    <child>
      <object class="GtkMenuItem" id="menuitem-open">
        <property name="visible">True</property>
        <property name="has_tooltip">True</property>
        <property name="tooltip_text" translatable="yes">Open a saved note.</property>
        <property name="label" translatable="yes">_Open Note</property>
        <property name="use_underline">True</property>
      </object>
    </child>
    <child>
      <object class="GtkMenuItem" id="menuitem-save">
        <property name="visible">True</property>
        <property name="has_tooltip">True</property>
        <property name="tooltip_text" translatable="yes">Save the current note.</property>
        <property name="label" translatable="yes">_Save Note</property>
        <property name="use_underline">True</property>
      </object>
    </child>
    <child>
      <object class="GtkMenuItem" id="menuitem-saveas">
        <property name="visible">True</property>
        <property name="has_tooltip">True</property>
        <property name="tooltip_text" translatable="yes">Save the current note under a different filename.</property>
        <property name="label" translatable="yes">Sa_ve Note As</property>
        <property name="use_underline">True</property>
      </object>
    </child>
    <child>
      <object class="GtkSeparatorMenuItem" id="seperator1">
        <property name="visible">True</property>
      </object>
    </child>
    <child>
      <object class="GtkMenuItem" id="menuitem-cut">
        <property name="visible">True</property>
        <property name="has_tooltip">True</property>
        <property name="tooltip_text" translatable="yes">Copy the highlighted text to the clipboard and delete the original text.</property>
        <property name="label" translatable="yes">Cut Te_xt</property>
        <property name="use_underline">True</property>
      </object>
    </child>
    <child>
      <object class="GtkMenuItem" id="menuitem-copy">
        <property name="visible">True</property>
        <property name="has_tooltip">True</property>
        <property name="tooltip_text" translatable="yes">Copy the selected text to the clipboard.</property>
        <property name="label" translatable="yes">_Copy Text</property>
        <property name="use_underline">True</property>
      </object>
    </child>
    <child>
      <object class="GtkMenuItem" id="menuitem-paste">
        <property name="visible">True</property>
        <property name="has_tooltip">True</property>
        <property name="tooltip_text" translatable="yes">Paste the text from the clipboard.</property>
        <property name="label" translatable="yes">_Paste Text</property>
        <property name="use_underline">True</property>
      </object>
    </child>
    <child>
      <object class="GtkSeparatorMenuItem" id="seperator2">
        <property name="visible">True</property>
      </object>
    </child>
    <child>
      <object class="GtkMenuItem" id="menuitem-about">
        <property name="visible">True</property>
        <property name="has_tooltip">True</property>
        <property name="tooltip_text" translatable="yes">About SmartStickies</property>
        <property name="label" translatable="yes">_About</property>
        <property name="use_underline">True</property>
      </object>
    </child>
    <child>
      <object class="GtkMenuItem" id="menuitem-quit">
        <property name="visible">True</property>
        <property name="has_tooltip">True</property>
        <property name="tooltip_text" translatable="yes">Quit SmartStickies.</property>
        <property name="label" translatable="yes">_Quit</property>
        <property name="use_underline">True</property>
      </object>
    </child>
  </object>
</interface>
```

Thanks,
Smartboy

---


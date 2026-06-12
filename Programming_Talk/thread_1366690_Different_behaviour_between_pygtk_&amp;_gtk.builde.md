---
title: "Different behaviour between pygtk &amp; gtk.builder"
date: 2009-12-28
forum: Programming Talk
---

### Post by alzaf on 2009-12-28
Hi

I am in the process of learning glade and gtk.builder. I am currently writing code for a treeview that uses a liststore. 

I have already written it using pygtk (included in attachment liststore3.py). The purpose of the program is to display a liststore and print location in console when you click it (using the cursor-change callback). I have managed to get it working using glade/gtk.builder (included in gtkb_liststore.py attachment) but it prints location when you move cursor as well as click on it instead of just clicking on it. 

I've checked the settings between the two programs and they look ok. Is there some setting I need to set?

For some reason, the glade file couldn't be uploaded, the detaiils of file called listStore.glade is here 

```
<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkListStore" id="liststore1">
    <columns>
      <!-- column-name gchararray1 -->
      <column type="gchararray"/>
    </columns>
    <data>
      <row>
        <col id="0" translatable="yes">part 1</col>
      </row>
      <row>
        <col id="0" translatable="yes">part 2</col>
      </row>
      <row>
        <col id="0" translatable="yes">part 3</col>
      </row>
    </data>
  </object>
  <object class="GtkWindow" id="window1">
    <property name="window_position">center</property>
    <child>
      <object class="GtkTreeView" id="treeview1">
        <property name="visible">True</property>
        <property name="can_focus">True</property>
        <property name="model">liststore1</property>
        <property name="headers_visible">False</property>
        <property name="search_column">0</property>
        <property name="hover_selection">True</property>
        <signal name="cursor_changed" handler="ls_cb"/>
        <child>
          <object class="GtkTreeViewColumn" id="treeviewcolumn1">
            <property name="title">column</property>
            <property name="expand">True</property>
            <signal name="clicked" handler="ls_cb"/>
            <child>
              <object class="GtkCellRendererText" id="cellrenderertext1"/>
              <attributes>
                <attribute name="text">0</attribute>
              </attributes>
            </child>
          </object>
        </child>
      </object>
    </child>
  </object>
</interface>
```

---

### Post by BenAshton24 on 2009-12-28
Use the changed signal instead [http://www.pygtk.org/docs/pygtk/class-gtktreeselection.html](http://www.pygtk.org/docs/pygtk/class-gtktreeselection.html)

Like this...
[PHP]selection = self.treeview.get_selection()
selection.connect('changed', self.selectTest1)[/PHP]

**Edit:** Oh, and you would need to change your selectTest1

[PHP]	def selectTest1(self, treeselection):
		#get data from highlighted selection
		(model, iter) = treeselection.get_selected()
		if iter != None :
			print "this is path of selected " 
			print model.get_path(iter)
		else:
			print "no selection made"[/PHP]

That should work...

**Edit2:** Just realised that I've been reading the wrong file (facepalm) but you get the idea of what signals to use, I'm sure that you can figure it out XD

---

### Post by alzaf on 2009-12-29
Thanks Ben for taking the time to look into this for me.

I found the solution. There is an option in the Treeview section of glade3 called Hover Selection which needs to set to No. This means that you can move the mouse over the row without it being selected. You can only select it by clicking on it which is the behaviour I want. 

For reference, here is the glade file:

```
<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkListStore" id="liststore1">
    <columns>
      <!-- column-name gchararray1 -->
      <column type="gchararray"/>
    </columns>
    <data>
      <row>
        <col id="0" translatable="yes">part 1</col>
      </row>
      <row>
        <col id="0" translatable="yes">part 2</col>
      </row>
      <row>
        <col id="0" translatable="yes">part 3</col>
      </row>
    </data>
  </object>
  <object class="GtkWindow" id="window1">
    <property name="window_position">center</property>
    <child>
      <object class="GtkTreeView" id="treeview1">
        <property name="visible">True</property>
        <property name="can_focus">True</property>
        <property name="model">liststore1</property>
        <property name="headers_visible">False</property>
        <signal name="cursor_changed" handler="ls_cb"/>
        <child>
          <object class="GtkTreeViewColumn" id="treeviewcolumn1">
            <property name="title">column</property>
            <property name="expand">True</property>
            <signal name="clicked" handler="ls_cb"/>
            <child>
              <object class="GtkCellRendererText" id="cellrenderertext1"/>
              <attributes>
                <attribute name="text">0</attribute>
              </attributes>
            </child>
          </object>
        </child>
      </object>
    </child>
  </object>
</interface>
```

---


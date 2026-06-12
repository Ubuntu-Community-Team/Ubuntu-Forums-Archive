---
title: "gtk-builder-convert crash"
date: 2008-05-14
forum: Programming Talk
---

### Post by azad on 2008-05-14
Hi, I am new to GTK programming and I've been following [this tutorial]("http://www.micahcarrick.com/12-27-2007/gtk-glade-tutorial-part-2.html") to get started with Glade.


I made a basic interface with Glade and saved it as .glade file. Then I had to convert the .glade file to GtkBuilder XML file. But when I run this command, it crashes:
gtk-builder-convert tutorial.glade tutorial.xml


Here's what it says in the terminal:
-------------------------------------------------------------------

Traceback (most recent call last):
  File "/usr/bin/gtk-builder-convert", line 745, in <module>
    sys.exit(main(sys.argv))
  File "/usr/bin/gtk-builder-convert", line 733, in main
    conv.parse_file(input_filename)
  File "/usr/bin/gtk-builder-convert", line 161, in parse_file
    self._parse()
  File "/usr/bin/gtk-builder-convert", line 259, in _parse
    self._convert(node.getAttribute("class"), node)
  File "/usr/bin/gtk-builder-convert", line 284, in _convert
    self._convert_menu(node)
  File "/usr/bin/gtk-builder-convert", line 342, in _convert_menu
    item = self._convert_menuitem(uimgr, obj_node)
  File "/usr/bin/gtk-builder-convert", line 378, in _convert_menuitem
    item = self._convert_menuitem(uimgr, obj_node)
  File "/usr/bin/gtk-builder-convert", line 374, in _convert_menuitem
    self._add_action_from_menuitem(uimgr, obj_node)
  File "/usr/bin/gtk-builder-convert", line 425, in _add_action_from_menuitem
    properties['stock_id'] = child
UnboundLocalError: local variable 'child' referenced before assignment
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_gtk-builder-convert.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/gtk-builder-convert", line 745, in <module>
    sys.exit(main(sys.argv))
  File "/usr/bin/gtk-builder-convert", line 733, in main
    conv.parse_file(input_filename)
  File "/usr/bin/gtk-builder-convert", line 161, in parse_file
    self._parse()
  File "/usr/bin/gtk-builder-convert", line 259, in _parse
    self._convert(node.getAttribute("class"), node)
  File "/usr/bin/gtk-builder-convert", line 284, in _convert
    self._convert_menu(node)
  File "/usr/bin/gtk-builder-convert", line 342, in _convert_menu
    item = self._convert_menuitem(uimgr, obj_node)
  File "/usr/bin/gtk-builder-convert", line 378, in _convert_menuitem
    item = self._convert_menuitem(uimgr, obj_node)
  File "/usr/bin/gtk-builder-convert", line 374, in _convert_menuitem
    self._add_action_from_menuitem(uimgr, obj_node)
  File "/usr/bin/gtk-builder-convert", line 425, in _add_action_from_menuitem
    properties['stock_id'] = child
UnboundLocalError: local variable 'child' referenced before assignment
-------------------------------------------------------------------

I submitted the crash report a few times.

Is libgtk2.0-dev buggy? What should I do?

Thanks in advance.

---

### Post by MicahCarrick on 2008-05-16
I'm working on getting this all sorted out (I'm the author of that tutorial).  The bug has to do with the way glade generates the XML representing the default menus and the way the GtkBuilder conversion script expects it to be generated. Being that GtkBuilder is relatively new (as a replacement for Libglade), there is a grace period in which these type of bugs will pop up.                                                                   

Here is an explanation and work around which will be fixed in that tutorial within a few days.

The crash is due to a property in the menu bar ("use_stock" property). The default Menubar looks like this in the menu editor:

[IMG]http://www.micahcarrick.com/mc_images/gtk-glade-tutorial/glade-menuedit-1.jpg[/IMG]

And that outputs this in the .glade file:

```

  <widget class="GtkImageMenuItem" id="new_menu_item">
    <property name="visible">True</property>
    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
    <property name="label" translatable="yes">_New</property>
    <property name="use_underline">True</property>
    <property name="use_stock">True</property>
    <signal name="activate" handler="on_new_menu_item_activate"/>
  </widget>
```

That line '<property name="use_stock">True</property>' is where the problem is. 

What you can do as a work around, is instead of using a stock menu item...

1. Open up the menu editor in Glade (right-click the GtkMenuBar and select 'Edit').
1. Click the menu item you need to change (for the tutorial, you'll have to do each one).
2. Change the 'Stock Item' under 'Properties' to 'None'.
3. Click onto another menu item and then back (I submitted a bug for this) and then you will see 'Internal Image Properties'. Choose the appropriate 'Stock Image' for that menu item.
4. Change the 'Label' under 'Properties' to the actual label you want for that menu item, using an underscore for mnemonics. (_New, _Open, _Save, Save _As, etc.).

The menu editor in glade would then look like this instead:

[IMG]http://www.micahcarrick.com/mc_images/gtk-glade-tutorial/glade-menuedit-2.jpg[/IMG]

And the output .glade file will instead contain:

```
  <widget class="GtkImageMenuItem" id="new_menu_item">
    <property name="visible">True</property>
    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
    <property name="label" translatable="yes">_New</property>
    <property name="use_underline">True</property>
    <signal name="activate" handler="on_new_menu_item_activate"/>
    <child internal-child="image">
      <widget class="GtkImage" id="menu-item-image1">
        <property name="stock">gtk-new</property>
      </widget>
    </child>
  </widget>
```

Then it should run through gtk-builder-convert just fine. 

In future versions of glade, this will no longer be a problem AND you will not need to run it through gtk-builder-convert anymore. They're working hard on it... we just need to be patient. :)

---

### Post by azad on 2008-05-17
Thanks for the help Micah. Really appreciate.

I cant wait for the next version of Glade. I hope those bugs are squashed and GtkBuilder works properly.

gtk-builder-convert works after making the changes. It produces the tutorial.xml

However, when I run tutorial.py .. it says "Failed to load UI XML file: tutorial.xml"
(Even though all the files are in the same folder)

I ran "python tutorial.py" in command line and I got this error:

Traceback (most recent call last):
  File "tutorial.py", line 349, in <module>
    editor = TutorialTextEditor()
  File "tutorial.py", line 334, in __init__
    self.text_view.modify_font(pango.FontDescription("monospace 10"))
AttributeError: 'NoneType' object has no attribute 'modify_font'

Any clues?

Thanks again for the help.

---

### Post by MicahCarrick on 2008-05-17
Yes, the "tutorial.ui" being a relative path has to be found releative to where you app is executing from. So, when you do:

```
python tutorial.py
```

It's actually being executed from where python lives and expects tutorial.ui to exist there (/usr/local/bin/ or something). Try giving it executable permissions and running it like an executable. Then it will be looking for tutorial.ui in the same directory that tutorial.py exists:

```
chmod a+x tutorial.py
./tutorial.py
```

---

### Post by MicahCarrick on 2008-05-17
By the way, that problem has been fixed and commited. Here's the bug: [http://bugzilla.gnome.org/show_bug.cgi?id=523932]("http://bugzilla.gnome.org/show_bug.cgi?id=523932")

---

### Post by azad on 2008-05-17
Hi thanks again.

I turned tutorial.py nto an executable and run it. When I click "Display", it goives me the same error "Failed to load UI XML file: tutorial.xml"

when I run it from the terminal , it shows the same error as before:
Traceback (most recent call last):
  File "tutorial.py", line 349, in <module>
    editor = TutorialTextEditor()
  File "tutorial.py", line 334, in __init__
    self.text_view.modify_font(pango.FontDescription("monospace 10"))
AttributeError: 'NoneType' object has no attribute 'modify_font'

Geez .. never thought getitng started will be so difficult.
Thanks for your help mate.

---

### Post by pohl9876 on 2008-08-31
Hi,

I followed the tutorial in this thread and get the following error messages when running "postpdf.py file.pdf" directly on the command line:

Traceback (most recent call last):
  File "/etc/cups/postpdf.py", line 52, in ?
    mipost = PostPdf()
  File "/etc/cups/postpdf.py", line 37, in __init__
    builder = gtk.Builder()
AttributeError: 'module' object has no attribute 'Builder'

Which python packages have to be installed to make the script work (other than python-gtk2 and python-glade2)? Does anybody know what the problem for those messages is? I have no experience in python and don't know where to start looking.

Alexander

---

### Post by AtticusTheGreat on 2009-07-03
To people that are contemplating this workaround (i.e. those who are probably still using Ubuntu 8.04 like me) should instead just download the latest gtk+ 2.12.x source archive and copy over the fixed gtk-builder-convert python script.

---

### Post by Darktrax on 2010-01-02
I know this is a older thread, and that Micah Carrick has done much work in making the use of glade in conjunction with gtk-builder-convert clear in the Part1 "Hello World" tutorial.

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

Unfortunately, beginners trying out their first steps in making the simple example window, with the glade and gtk+ tools as they default install in 9.10 Karmic will still generate exactly the same bug as, I understand has been fixed earlier.
```
:~/sandbox/glade$ gtk-builder-convert tutorial.glade tutorial.xml
Traceback (most recent call last):
  File "/usr/bin/gtk-builder-convert", line 772, in <module>
    sys.exit(main(sys.argv))
  File "/usr/bin/gtk-builder-convert", line 760, in main
    conv.parse_file(input_filename)
  File "/usr/bin/gtk-builder-convert", line 161, in parse_file
    self._parse()
  File "/usr/bin/gtk-builder-convert", line 233, in _parse
    assert glade_iface, ("Badly formed XML, there is "
AssertionError: Badly formed XML, there is no <glade-interface> tag.
:~/sandbox/glade$
```
We did not even get as far as the "Hello World" bit  :(
So maybe I have some very silly combination of packages/ libraries?

```
# pkg-config --modversion gtk+-2.0 glib-2.0 cairo pango
2.18.3
2.22.2
1.8.8
1.26.0
#
``` Micah almost certainly has a mound of emails, and won't appreciate going back to stuff that he already fixed, so I am asking if anyone else who has tried and understood this, can make clear, step by step, what works. Thanks..

---

### Post by ussndmac on 2010-09-12
I get the same "Badly formed XML, there is no <glade-interface> tag." error with Glade 3.6.7 under Ubuntu 10.04

Any ideas for trouble shooting or fixing?

---

### Post by e02jr on 2010-10-13
According to [http://www.gtkforums.com/about5852.html](http://www.gtkforums.com/about5852.html) you don't need to use  gtk-builder-convert, just rename the file and use it in code.

Tried and worked on 10.04 and glade 3.6.7

---

### Post by naga2raja on 2011-08-08
Open the .glade file in a text editor and rename the <interface></interface> tags to <glade-interface></glade-interface> tags.. and then run the command gtk-builder-convert file.glade file.xml... one thing to note is.. you have to change the <glade-interface> tags to its original state to do some changes in the glade interface designer

---


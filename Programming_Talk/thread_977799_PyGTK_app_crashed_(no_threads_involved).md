---
title: "PyGTK app crashed (no threads involved)"
date: 2008-11-10
forum: Programming Talk
---

### Post by Flimm on 2008-11-10
Development on [Epidermis](https://launchpad.net/epidermis) has halted, as I can't debug this crash.
Seems like only slight changes in the code cause my app coded in PyGTK to crash, outputting:
```
Segmentation fault
```
No traceback, no nothing. The only way I could think of to debug this problem is to comment out significant amounts of code and then reenable them step by step. As you can imagine, this is incredibally slow.
Once I found that the culprit was badly initialized SizeGroups, but that problem is fixed, and I still get this error.
I've wondered if it's got something to do with TextView.
It hasn't got anything to do with threads, since I don't use them here.

In general, how do you go about debugging segmentation faults for PyGTK? Any explanations on this would help me and the project a lot!
(Please bear in mind I don't know C - yet)

I've attached the code that crashes, all you have to do to cause a crash is run creator.py , change the type to another say "metacity", and then try to type in the description box. It would help me to know if this crash happens on other computers. Thanks.

---

### Post by nvteighen on 2008-11-10
Er... what attachment?

---

### Post by Flimm on 2008-11-11
> **nvteighen said:**
> Er... what attachment?
Sorry, I prepared the compressed archive and forgot to attach it. I've edited my first post now.

---

### Post by nvteighen on 2008-11-11
I can't generate the Segfault.

But, I'm using Python 2.5.2-2, PyGTK 2.12.1-6 @ Debian Testing "Lenny". It would be nice if people using Python 2.6 and various Ubuntu versions.

---

### Post by days_of_ruin on 2008-11-11
> **Flimm said:**
> Development on [Epidermis](https://launchpad.net/epidermis) has halted, as I can't debug this crash.
Seems like only slight changes in the code cause my app coded in PyGTK to crash, outputting:
```
Segmentation fault
```
No traceback, no nothing. The only way I could think of to debug this problem is to comment out significant amounts of code and then reenable them step by step. As you can imagine, this is incredibally slow.
Once I found that the culprit was badly initialized SizeGroups, but that problem is fixed, and I still get this error.
I've wondered if it's got something to do with TextView.
It hasn't got anything to do with threads, since I don't use them here.

In general, how do you go about debugging segmentation faults for PyGTK? Any explanations on this would help me and the project a lot!
(Please bear in mind I don't know C - yet)


I've attached the code that crashes, all you have to do to cause a crash is run creator.py , change the type to another say "metacity", and then try to type in the description box. It would help me to know if this crash happens on other computers. Thanks.

I can't get it to crash.I am using ubuntu 8.04 and python 2.5.2
What part of the code is supposed to crash it?

---

### Post by Zootropo on 2008-11-11
Why don't you run the interpreter using gdb and take a look at the backtrace?

---

### Post by Flimm on 2008-11-12
That's very strange, I consistantly get the segmentation fault.

I tried gdb, but I'm afraid I'm going to need help on this, I don't know C, C++ or Module-2 so this is first time I'm using it. It seems similar to pdb though.

Once I got the segmentation fault, I quit, I'll do some more digging in gdb's manual this evening though and see what I can do with the error.

```
david@david-laptop:~/Programming/(etc)/epidermis/send$ gdb --args python creator.py
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) run
Starting program: /usr/bin/python creator.py
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb7e4c8c0 (LWP 6909)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
using custom creator.glade
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb6b2db90 (LWP 6914)]
[New Thread 0xb61ffb90 (LWP 6915)]
(no debugging symbols found)
[Thread 0xb6b2db90 (LWP 6914) exited]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7e4c8c0 (LWP 6909)]
0xb744174d in ?? () from /usr/lib/libpango-1.0.so.0
(gdb) quit
The program is running.  Exit anyway? (y or n) y

```

---

### Post by unutbu on 2008-11-12
Type 
```

pdb creator.py
```

to run the python debugger. 

See [http://www.python.org/doc/2.5.2/lib/debugger-commands.html](http://www.python.org/doc/2.5.2/lib/debugger-commands.html)
for information on what commands you can use in pdb.

Generally what you do is type
```

b [linenumber]
```

to set a breakpoint. 
```

run
```Pdb will run through the program until it hits a breakpoint.

Type 's' to step into function calls,
Type 'n' to step over function calls.
Type 'print [expr]' to see the value of variables or expressions.

---

### Post by Flimm on 2008-11-12
Trouble with using pdb is that the error is not your standard python exception, it's a Segmentation Fault. I didn't realise you can pdb from the command line, I thought the only way to use it was by importing it in your python code, so thanks for that ;)
Oh, and you can't use 'run' in pdb, just```
r
```Here's an attempt at running pdb so that you see what I mean.
I set the breakpoint to line 619 which is where gtk.main() is, as there are no errors in the initialization, and I type 'r' then 's'.
```
david@david-laptop:~/Programming/trunk/epidermis/send$ pdb creator.py
> /home/david/Programming/(etc)/epidermis/send/creator.py(4)<module>()
-> """Epidermis creator is a GUI program for creating pigments"""
(Pdb) b 619
Breakpoint 1 at /home/david/Programming/trunk/epidermis/send/creator.py:619
(Pdb) r
using custom creator.glade
> /home/david/Programming/trunk/epidermis/send/creator.py(619)main()
-> gtk.main()
(Pdb) s
```
At this point, the window is open. I click on the type combobox and change 'skin' to 'metacity'. It's only when I click 'metacity' that the following happens, as expected, I type 'n' the first time and just press enter the following times to repeat 'n':
```
-Call--
> /home/david/Programming/trunk/epidermis/send/creator.py(534)comboboxPigmentType_callback()
-> def comboboxPigmentType_callback(self, widget, data=None):
(Pdb) n
> /home/david/Programming/trunk/epidermis/send/creator.py(535)comboboxPigmentType_callback()
-> pigmentType = const.PIGMENT_TYPES[self.comboboxPigmentType.get_active()]
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(538)comboboxPigmentType_callback()
-> widgets = {"skin":"tableSkin", "wallpaper":"tableWallpaper"}
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(541)comboboxPigmentType_callback()
-> if not widgets.has_key(pt):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(541)comboboxPigmentType_callback()
-> if not widgets.has_key(pt):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(541)comboboxPigmentType_callback()
-> if not widgets.has_key(pt):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(542)comboboxPigmentType_callback()
-> widgets[pt] = "lbl" + pt.capitalize()
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(541)comboboxPigmentType_callback()
-> if not widgets.has_key(pt):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(542)comboboxPigmentType_callback()
-> widgets[pt] = "lbl" + pt.capitalize()
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(541)comboboxPigmentType_callback()
-> if not widgets.has_key(pt):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(542)comboboxPigmentType_callback()
-> widgets[pt] = "lbl" + pt.capitalize()
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(541)comboboxPigmentType_callback()
-> if not widgets.has_key(pt):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(542)comboboxPigmentType_callback()
-> widgets[pt] = "lbl" + pt.capitalize()
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(541)comboboxPigmentType_callback()
-> if not widgets.has_key(pt):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(542)comboboxPigmentType_callback()
-> widgets[pt] = "lbl" + pt.capitalize()
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(541)comboboxPigmentType_callback()
-> if not widgets.has_key(pt):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(542)comboboxPigmentType_callback()
-> widgets[pt] = "lbl" + pt.capitalize()
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(541)comboboxPigmentType_callback()
-> if not widgets.has_key(pt):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(542)comboboxPigmentType_callback()
-> widgets[pt] = "lbl" + pt.capitalize()
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(541)comboboxPigmentType_callback()
-> if not widgets.has_key(pt):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(542)comboboxPigmentType_callback()
-> widgets[pt] = "lbl" + pt.capitalize()
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(540)comboboxPigmentType_callback()
-> for pt in const.PIGMENT_TYPES:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(544)comboboxPigmentType_callback()
-> notebook = self.wTree.get_widget("notebookOther")
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(545)comboboxPigmentType_callback()
-> if not self.currentFrameSpecificChild is None:
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(546)comboboxPigmentType_callback()
-> self.frameSpecific.remove(self.currentFrameSpecificChild)
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(547)comboboxPigmentType_callback()
-> notebook.add(self.currentFrameSpecificChild)
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(548)comboboxPigmentType_callback()
-> if self.wTree.get_widget(widgets[pigmentType]) is None:

(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(550)comboboxPigmentType_callback()
-> self.currentFrameSpecificChild = self.wTree.get_widget(widgets[pigmentType])
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(551)comboboxPigmentType_callback()
-> notebook.remove(self.currentFrameSpecificChild)
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(552)comboboxPigmentType_callback()
-> self.frameSpecific.add(self.currentFrameSpecificChild)
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(555)comboboxPigmentType_callback()
-> if pigmentType in ("wallpaper","gnomeSplash","grub","usplash"):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(560)comboboxPigmentType_callback()
-> elif pigmentType == "skin":
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(564)comboboxPigmentType_callback()
-> self.labelFile.set_label("Theme directory:")
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(565)comboboxPigmentType_callback()
-> self.filechooserbuttonFile.set_sensitive(True)
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(566)comboboxPigmentType_callback()
-> self.filechooserbuttonFile.set_action(gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER)
(Pdb) 

> /home/david/Programming/trunk/epidermis/send/creator.py(570)comboboxPigmentType_callback()
-> self.sizeGroup0 = gtk.SizeGroup(gtk.SIZE_GROUP_HORIZONTAL)
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(571)comboboxPigmentType_callback()
-> self.sizeGroup1 = gtk.SizeGroup(gtk.SIZE_GROUP_HORIZONTAL)
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(572)comboboxPigmentType_callback()
-> if isinstance(self.currentFrameSpecificChild, gtk.Table):
(Pdb) 
> /home/david/Programming/trunk/epidermis/send/creator.py(588)comboboxPigmentType_callback()
-> self.wTree.get_widget("vbox2222").check_resize()
(Pdb) 

--Return--
> /home/david/Programming/trunk/epidermis/send/creator.py(588)comboboxPigmentType_callback()->None
-> self.wTree.get_widget("vbox2222").check_resize()
(Pdb) 











```
I can tell the code is complete because I'm pressing enter for no reason, and the widgets on the window are responsive again. Everything has happend the way I expected them to, no problems so far.
I click on the description textbox, and type a letter, immediately the window disappears, and I get this:
```
Segmentation fault
```
That's why I can't use pdb, and I had to resort to commenting out lines of code manually to try and pinpoint the bad code. Each time I think I've eliminated the buggy code, the segmentation fault pops up at a different sequence of clicks in the window.

---

### Post by Zootropo on 2008-11-12
> **Flimm said:**
> That's very strange, I consistantly get the segmentation fault.

I tried gdb, but I'm afraid I'm going to need help on this, I don't know C, C++ or Module-2 so this is first time I'm using it. It seems similar to pdb though.

Once I got the segmentation fault, I quit, I'll do some more digging in gdb's manual this evening though and see what I can do with the error.

```
david@david-laptop:~/Programming/(etc)/epidermis/send$ gdb --args python creator.py
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) run
Starting program: /usr/bin/python creator.py
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb7e4c8c0 (LWP 6909)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
using custom creator.glade
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb6b2db90 (LWP 6914)]
[New Thread 0xb61ffb90 (LWP 6915)]
(no debugging symbols found)
[Thread 0xb6b2db90 (LWP 6914) exited]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7e4c8c0 (LWP 6909)]
0xb744174d in ?? () from /usr/lib/libpango-1.0.so.0
(gdb) quit
The program is running.  Exit anyway? (y or n) y

```

At least you now that the error seems to be because of pango, which is the library used to render the text. Are you using pango markup? you could try removing it if that's the case.

Run the "bt" command at gbd once the application crashes to see the backtrace.

This link might be useful, too:
[http://wiki.python.org/moin/DebuggingWithGdb](http://wiki.python.org/moin/DebuggingWithGdb)

---

### Post by Flimm on 2008-11-12
Only one line 561 of creator.py has pango markup:```
self.labelFile.set_label("<span strikethrough=\"true\">Theme file:</span>")
```
Disabling it has no effect.
Thanks for the link. I've now installed python2.5-dbg
Here's the output now (with line 561 enabled, like it is in the attachment, and with a backtrace):
```
david@david-laptop:~/Programming/trunk/epidermis/send$ gdb --args python creator.py
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(gdb) run
Starting program: /usr/bin/python creator.py
[Thread debugging using libthread_db enabled]
[New Thread 0xb7df78c0 (LWP 7223)]
using custom creator.glade
[New Thread 0xb6ad8b90 (LWP 7229)]
[New Thread 0xb60ffb90 (LWP 7230)]
[New Thread 0xb58feb90 (LWP 7231)]
[Thread 0xb58feb90 (LWP 7231) exited]
[Thread 0xb6ad8b90 (LWP 7229) exited]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7df78c0 (LWP 7223)]
0xb73ec74d in ?? () from /usr/lib/libpango-1.0.so.0
(gdb) bt
#0  0xb73ec74d in ?? () from /usr/lib/libpango-1.0.so.0
#1  0xb73eca47 in pango_language_get_scripts () from /usr/lib/libpango-1.0.so.0
#2  0xb73ecb32 in pango_language_includes_script ()
   from /usr/lib/libpango-1.0.so.0
#3  0xb73e7c33 in ?? () from /usr/lib/libpango-1.0.so.0
#4  0xb73e865f in pango_itemize_with_base_dir ()
   from /usr/lib/libpango-1.0.so.0
#5  0xb73f1289 in ?? () from /usr/lib/libpango-1.0.so.0
#6  0xb73f3d42 in pango_layout_get_iter () from /usr/lib/libpango-1.0.so.0
#7  0xb73f3e61 in pango_layout_get_cursor_pos ()
   from /usr/lib/libpango-1.0.so.0
#8  0xb77aec2d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#9  0xb77afa21 in gtk_text_layout_get_line_display ()
   from /usr/lib/libgtk-x11-2.0.so.0
#10 0xb77b0f3e in gtk_text_layout_get_cursor_locations ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb77be614 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb77be730 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb77c4b0e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#14 0xb7c85b9c in g_cclosure_marshal_VOID__STRING ()
   from /usr/lib/libgobject-2.0.so.0
#15 0xb7c78c4b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#16 0xb7c8f095 in ?? () from /usr/lib/libgobject-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#17 0xb7c907ac in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#18 0xb7c90acd in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#19 0xb76ed2fe in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#20 0xb7c85b9c in g_cclosure_marshal_VOID__STRING ()
   from /usr/lib/libgobject-2.0.so.0
#21 0xb7c78c4b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#22 0xb7c8f095 in ?? () from /usr/lib/libgobject-2.0.so.0
#23 0xb7c907ac in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#24 0xb7c90acd in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#25 0xb76ea888 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#26 0xb76eb60f in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#27 0xb76e9d00 in gtk_im_context_filter_keypress ()
   from /usr/lib/libgtk-x11-2.0.so.0
#28 0xb76e9d00 in gtk_im_context_filter_keypress ()
   from /usr/lib/libgtk-x11-2.0.so.0
#29 0xb77c7d84 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#30 0xb7707036 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#31 0xb7c773c9 in ?? () from /usr/lib/libgobject-2.0.so.0
#32 0xb7c78b78 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#33 0xb7c8ed3d in ?? () from /usr/lib/libgobject-2.0.so.0
#34 0xb7c9062b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#35 0xb7c90c26 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#36 0xb781c33e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#37 0xb782feff in gtk_window_propagate_key_event ()
   from /usr/lib/libgtk-x11-2.0.so.0
#38 0xb78331cc in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#39 0xb7707036 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#40 0xb7c773c9 in ?? () from /usr/lib/libgobject-2.0.so.0
#41 0xb7c78c4b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#42 0xb7c8ed3d in ?? () from /usr/lib/libgobject-2.0.so.0
#43 0xb7c9062b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#44 0xb7c90c26 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#45 0xb781c33e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#46 0xb76ffc11 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#47 0xb7700ef7 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#48 0xb759750a in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#49 0xb7bf06f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#50 0xb7bf3da3 in ?? () from /usr/lib/libglib-2.0.so.0
#51 0xb7bf42c2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#52 0xb77013a9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#53 0xb7ad7f1c in ?? ()
   from /var/lib/python-support/python2.5/gtk-2.0/gtk/_gtk.so
#54 0x080cede3 in PyEval_EvalFrameEx (f=0x9fea0d4, throwflag=0)
    at ../Python/ceval.c:3579
#55 0x080cfbf5 in PyEval_EvalFrameEx (f=0x9dba1b4, throwflag=0)
    at ../Python/ceval.c:3681
---Type <return> to continue, or q <return> to quit---
#56 0x080d0345 in PyEval_EvalCodeEx (co=0xb7d95458, globals=0xb7dd0acc, 
    locals=0xb7dd0acc, args=0x0, argcount=0, kws=0x0, kwcount=0, defs=0x0, 
    defcount=0, closure=0x0) at ../Python/ceval.c:2858
#57 0x080d0557 in PyEval_EvalCode (co=0xb7d95458, globals=0xb7dd0acc, 
    locals=0xb7dd0acc) at ../Python/ceval.c:514
#58 0x080edf8f in PyRun_FileExFlags (fp=0x9d62008, 
    filename=0xbfbcb701 "creator.py", start=257, globals=0xb7dd0acc, 
    locals=0xb7dd0acc, closeit=1, flags=0xbfbca098)
    at ../Python/pythonrun.c:1273
#59 0x080ee25a in PyRun_SimpleFileExFlags (fp=0x9d62008, 
    filename=0xbfbcb701 "creator.py", closeit=1, flags=0xbfbca098)
    at ../Python/pythonrun.c:879
#60 0x080595e7 in Py_Main (argc=1, argv=0xbfbca164) at ../Modules/main.c:532
#61 0x08058962 in main (argc=172118816, argv=0xa423640)
    at ../Modules/python.c:23
(gdb) quit
The program is running.  Exit anyway? (y or n) y

```

---

### Post by Flimm on 2008-11-12
Funnily enough, with the attached creator.glade file, I don't get the segmentation fault anymore. I don't remember changing anything significant, and a diff seems to show that some XML elements have simply been declared in a different order. This still doesn't explain why I got the error and other people didn't, or how to avoid it in future.
Does any know of a good diff program (preferably with a GUI) for XML files like glade? What exactly has changed between the old creator.glade and the new one?

---

### Post by Flimm on 2008-11-14
bump

---

### Post by loell on 2008-11-14
> **Flimm said:**
> 
Does any know of a good diff program (preferably with a GUI) for XML files like glade? What exactly has changed between the old creator.glade and the new one?

have you tried meld?

---

### Post by Flimm on 2008-11-19
Thanks, I have tried meld.

Well, seeing as no-one else was experiencing the bug, I went ahead and finished Epidermis Creator, it's now in [Epidermis 0.2](https://launchpad.net/epidermis/0.x/0.2).

---


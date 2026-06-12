---
title: "Ruby and Glade3"
date: 2007-06-09
forum: Programming Talk
---

### Post by apoth on 2007-06-09
ruby-glade-create-template doesn't appear to work with Glade3 files. Any ideas how I can make that happen? I much prefer it to Glade2.

Thanks

---

### Post by DeadEyes on 2007-06-09
Your not giving us much to go on, what exactly is happening?

---

### Post by apoth on 2007-06-09
Sorry, I don't get any GUI loaded when I run the .rb - I just get this console output:

```
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed

```

Then the application doesn't terminate, but I get no more output and no GUI.

---

### Post by DeadEyes on 2007-06-09
Ah, been there. Actually your program is working. The window's visible property is set to false. For the top level window in Glade go to common properties and set visible to Yes then try again.
Now as to the messages I don't know what they are or if they will have any major impact ,but they do look nasty. but I think its been fixed in CVS

---

### Post by apoth on 2007-06-09
Spot on, thanks a lot. The errors don't seem terminal so I won't worry about them for now.

---

### Post by avik on 2007-06-10
While those errors seem pretty bad, I've always seen them come up, so I don't think they have much of an effect.

---

### Post by jk.cheng on 2010-08-12
I am facing problem while converting my glade gui design into ruby
files. Here i paste the command and error:

Command:
```
ruby-glade-create-template example.glade > example.rb
```

Error Display:
```
/usr/bin/ruby-glade-create-template: line 58
   libglade-WARNING **:Expected <glade-interface>.  Got <interface>.
/usr/bin/ruby-glade-create-template: line 58
   libglade-WARNING **:did not finish in PARSER_FINISH state
/usr/bin/ruby-glade-create-template:58:in `initialize': could not load
glade file example.glade (IOError)
  from /usr/bin/ruby-glade-create-template:58:in `new'
  from /usr/bin/ruby-glade-create-template:58
```

Beside that, is there other ways to do?

---

### Post by waves2d on 2011-02-28
try changing the project file format in the preferences to Libglade.

---


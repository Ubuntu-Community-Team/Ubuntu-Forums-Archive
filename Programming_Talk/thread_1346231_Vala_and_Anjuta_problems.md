---
title: "Vala and Anjuta problems"
date: 2009-12-04
forum: Programming Talk
---

### Post by pt123 on 2009-12-04
I am trying to install the Vala plugin for Anjuta from here 
[http://bitbucket.org/abderrahim/anjuta-vala/wiki/Home](http://bitbucket.org/abderrahim/anjuta-vala/wiki/Home)

but running into a few problems

when I tried to make it gave me this error
```

plugin.vala:22.2-22.4: error: The symbol `Gee' could not be found
	Gee.Map<string,Vala.SourceFile> source_files;

```

So edited the make file to add Gee ( idea from [http://www.poppa.se/blog/tag/vala/](http://www.poppa.se/blog/tag/vala/))
```

valac -g -C --vapidir . --pkg libanjuta-1.0 --pkg gee-1.0 --pkg vala-1.0 $^

```

But now it is giving more errors
```

plugin.vala:268.27-268.47: error: The name `get_keys' does not exist in the context of `Gee.Map<string,Vala.SourceFile>'
			foreach(string file in source_files.get_keys())
			                       ^^^^^^^^^^^^^^^^^^^^^
plugin.vala:394.23-394.47: error: The name `get_using_directives' does not exist in the context of `Vala.SourceFile'
			foreach (var ns in file.get_using_directives ()) {

plugin.vala:211.44-211.54: error: The name `suggestions' does not exist in the context of `ValaPlugin.on_char_added'
				current_editor.suggest (to_string_list(suggestions), current_position, (int) prefix_length);
				                                       ^^^^^^^^^^^
plugin.vala:328.27-328.47: error: The name `get_keys' does not exist in the context of `Gee.Map<string,Vala.SourceFile>'
			foreach(string file in source_files.get_keys())



plugin.vala:491.28-491.60: warning: unhandled error `GLib.Error'
			source.file.filename == ((IAnjuta.File)editor).get_file().get_path()) {
			                        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
plugin.vala:496.21-496.70: warning: unhandled error `GLib.Error'
			var begin_iter = editor.get_line_begin_position (source.first_line);
			                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
plugin.vala:498.5-498.22: warning: unhandled error `GLib.Error'
				begin_iter.next ();
				^^^^^^^^^^^^^^^^^^
plugin.vala:499.19-499.67: warning: unhandled error `GLib.Error'
			var end_iter = editor.get_line_begin_position (source.last_line);
			               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

```


I am not sure what do next

I was hoping there would precompiled vala plugin for Anjuta for Ubuntu.
The fact there is none and author of the plugin doesn't seem to be supporting Anjuta 2.28 is very disheartening. 

Using Jaunty, Vala 0.78, Anjuta 2.26

---

### Post by pt123 on 2009-12-11
update:
there was a recent version of the plugin (which I missed because of the name), I managed to download it and compile it (produced a few warnings). 

But now in Anjuta it only appears as in the plugin in list when I uncheck "only show user activatatable plugins". So I cannot use it. 

In the preferences Menu Vala , is listed but not as an option for code complete
[[img]http://www.ubuntu-pics.de/thumb/34014/screenshot_001_g7Ryk6.png[/img]](http://www.ubuntu-pics.de/bild/34014/screenshot_001_g7Ryk6.png)


Is there away to find out why code completion is not an option?

---

### Post by brunogirin on 2010-08-14
I've got the same problem on Lucid. The author seems to be more interested in getting it included in Anjuta 3.0 by default. At the end of the day, Vala is a very new language so tools are still evolving. I reckon I'll stay with gEdit and the Valencia plugin for now then.

---

### Post by pt123 on 2010-08-14
I ended up giving up on Anjuta, and used gedit with the Valencia plugin.

Still the language is not that new, but the IDE support is horrible, and it is not difficult to fathom why new developers end up coding in Mono.

---

### Post by kahumba on 2010-08-14
No IDE with Vala support - pity, as a Java dev I wanted for years a solution as comfortable as Java/C# and as lite and snappy as C/C++.
So far I'm impressed with Vala: no additional runtime costs, fast as C but no C-like header headaches and no pointers, easy and friendly to program in. Hopefully I'll be able to get along without IDE support, using jEdit so far.

---

### Post by Queue29 on 2010-08-14
Vala's IDE support really is depressingly bad. Even [Vala IDE ]("http://valaide.org/")sucks...

---

### Post by PJSingh5000 on 2012-01-18
The version of Anjuta in Ubuntu Software Center seems pretty out dated; I couldn't get it to work with Vala.  The newer version on the web site ([http://www.anjuta.org/]("http://www.anjuta.org/")) seems to work with Vala.  However, compiling it is a pain because all of the dependancies are not very clear.

Here's what you need to do on Ubuntu 11.10 to compile Anjuta, including Vala support...

DOWNLOAD : anjuta-3.2.2.tar.xz
FROM URL : [http://www.anjuta.org/downloads.html]("http://www.anjuta.org/downloads.html")

```

$ cd [DOWNLOAD LOCATION]
$ tar xfv ./anjuta-*.tar.xz
$ cd ./anjuta-*/
$ sudo apt-get install flex bison byacc libxml2-dev libgdl-3-dev libgda-4.0-dev libvte-2.90-dev libgtksourceview-3.0-dev libvala-0.14-dev intltool gnome-doc-utils libsqlite3-dev libapr1-dev libaprutil1-dev libneon27-dev libsvn-dev libgladeui-dev libdevhelp-dev graphviz-dev
$ ./configure
$ make
$ sudo make install
$ sudo ldconfig
$ sudo apt-get install autogen

```

Create the Anjuta launcher for Unity.
```

$ sudo gedit /usr/share/applications/anjuta.desktop

```
Add the following, save, and exit gedit...
```

[Desktop Entry]
Name=Anjuta DevStudio
GenericName=GNOME Integrated Development Environment
Comment=Versatile software development studio
Exec=/usr/local/bin/anjuta
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=anjuta
Categories=GTK;Development;

```

For C++ Gtk 3 development, install...
```

$ sudo apt-get install libgtkmm-3.0-dev libtool

```
For Vala development, install...
```

$ sudo apt-get install libvala-0.12-dev

```

The glade plugin in Anjuta, which the above instructions will compile and install, lets you graphically create UIs for Vala.

I think Anjuta can be improved a little...
[LIST]
[*]I find the UI designer (glade plugin) to be slightly buggy when moving UI components/widgets.
[*]The way the IDEs different panels and buttons "flow" and shift arround when changing views or resizing the IDE window is annoying.  (I keep having to fight with the IDE to resize diffent panels (Palette View, Design View, and Widgets View) when I need to make a change or selection in one of the pannels).
[/LIST]

That said, Anjuta is probably better than other options for Vala.

---


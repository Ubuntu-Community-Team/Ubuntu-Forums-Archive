---
title: "Is it possible to to change the command with which a file type launches using bash?"
date: 2009-09-27
forum: Programming Talk
---

### Post by Levo on 2009-09-27
Is it possible to to change the command with which a file type launches using bash?

e.g.: ".asd" files when they are double clicked open with program A. I want to change this program using bash.

---

### Post by geirha on 2009-09-27
That information is stored in /usr/share/applications/mimeinfo.cache and ~/.local/share/applications/mimeapps.list . The former being global defaults, and the latter being overrides done by you.

I believe the xdg-mime command is meant to be used to query and alter this, though I've never used it myself. ```
man xdg-mime
```

EDIT: Oh, and note that it doesn't decide the filetype based on the extension, but rather the contents of the file. The file command will show you its mimetype
```
file somefile
file -i somefile

```

---

### Post by Levo on 2009-09-28
> **geirha said:**
> That information is stored in /usr/share/applications/mimeinfo.cache and ~/.local/share/applications/mimeapps.list . The former being global defaults, and the latter being overrides done by you.

I believe the xdg-mime command is meant to be used to query and alter this, though I've never used it myself. ```
man xdg-mime
```

EDIT: Oh, and note that it doesn't decide the filetype based on the extension, but rather the contents of the file. The file command will show you its mimetype
```
file somefile
file -i somefile

```

This program only allows me to change information of specific filetype. I want to change the command with it launches. I know the manual way (create manually the files required) but I prefer a command.

---

### Post by bigboy_pdb on 2009-09-28
If you only want to do it for a single program, you could just write a small bash script to do what you want.

```

#!/bin/bash

# Insert code here to run file. For example:
# 
# wine 'C:\Program Files\blizzard\starcraft'

```

If you need to open all programs of a given mime type or file extension a certain way, you could write a small program/script that opens the files the way you want them to be opened and you can affiliate that mime/file type with the script/program.

---

### Post by geirha on 2009-09-28
Then I'm not sure what you mean.

If I have a plain text file, it will open in gedit when I double click it:
```

$ file -i test.txt 
test.txt: text/plain charset=us-ascii
$ xdg-mime query default text/plain
gedit.desktop

```

With xdg-mime you can change that to openoffice writer for instance:
```

$ xdg-mime default openoffice.org-writer.desktop text/plain 

```

After this, double-clicking the same .txt-file, opens it in openoffice writer instead. It apparently creates/updates the file ~/.local/share/applications/defaults.list.
```
$ cat ~/.local/share/applications/defaults.list 
[Default Applications]
text/plain=openoffice.org-writer.desktop

```

---

### Post by Levo on 2009-09-28
> **bigboy_pdb said:**
> If you only want to do it for a single program, you could just write a small bash script to do what you want.

```

#!/bin/bash

# Insert code here to run file. For example:
# 
# wine 'C:\Program Files\blizzard\starcraft'

```

If you need to open all programs of a given mime type or file extension a certain way, you could write a small program/script that opens the files the way you want them to be opened and you can affiliate that mime/file type with the script/program.

I have that script you described. But this script is created by an "installer-script". I want the installer script to register a certain file type with the script it creates.

---

### Post by Levo on 2009-09-28
> **geirha said:**
> Then I'm not sure what you mean.

If I have a plain text file, it will open in gedit when I double click it:
```

$ file -i test.txt 
test.txt: text/plain charset=us-ascii
$ xdg-mime query default text/plain
gedit.desktop

```

With xdg-mime you can change that to openoffice writer for instance:
```

$ xdg-mime default openoffice.org-writer.desktop text/plain 

```

After this, double-clicking the same .txt-file, opens it in openoffice writer instead. It apparently creates/updates the file ~/.local/share/applications/defaults.list.
```
$ cat ~/.local/share/applications/defaults.list 
[Default Applications]
text/plain=openoffice.org-writer.desktop

```

I now understand what you mean and what xdg-mime does. You are right, I wasn't very clear. What you tell me changes the program with which it starts from a list of known/registered programs. What I want is register a new program and then select it.

---

### Post by geirha on 2009-09-28
> **Levo said:**
> I now understand what you mean and what xdg-mime does. You are right, I wasn't very clear. What you tell me changes the program with which it starts from a list of known/registered programs. What I want is register a new program and then select it.

Then what you need to do is to create a .desktop-file (menu-entry) for it and then use the command «xdg-desktop-menu» to install the .desktop file. The format of .desktop-files is explained in xdg-desktop-menu's manual page, so make sure to read it
```
man xdg-desktop-menu
```
For examples, open a few .desktop-files under /usr/share/applications/ in a regular text editor. The format is fairly simple.

---

### Post by bigboy_pdb on 2009-09-28
At first I thought that you were stating that you wanted to do more than open a file using a certain program. For example, you want Firefox to open an html file in a new window instead of a new tab. However, from reading more it seems that you only have a problem with which program opens the file.

One way that you can do this, which might be simpler than editing files having to do with mime-types or running commands for editing mime types, is to right click on the file and select "Properties". Next select the "Open With" tab. There is a list of programs that you can use to open the file. If the program that you want to open it with isn't listed, clicking the "Add" button lists more programs as options.

If the program isn't listed there, you can write a command that can be executed when the file is opened. Actually, I wasn't aware that a custom command could be executed for all files of a given type (because I hadn't noticed the option before).

---

### Post by Levo on 2009-09-29
> **bigboy_pdb said:**
> At first I thought that you were stating that you wanted to do more than open a file using a certain program. For example, you want Firefox to open an html file in a new window instead of a new tab. However, from reading more it seems that you only have a problem with which program opens the file.

One way that you can do this, which might be simpler than editing files having to do with mime-types or running commands for editing mime types, is to right click on the file and select "Properties". Next select the "Open With" tab. There is a list of programs that you can use to open the file. If the program that you want to open it with isn't listed, clicking the "Add" button lists more programs as options.

If the program isn't listed there, you can write a command that can be executed when the file is opened. Actually, I wasn't aware that a custom command could be executed for all files of a given type (because I hadn't noticed the option before).

I want to do exactly what you described, but using bash.

---

### Post by Levo on 2009-09-29
geirha you were right in your posts. After hours of searching the web, I found that these are the required utilities. But I still cannot configure it. Can you, or someone else, give a full example on how to do this? I mean create a new application registration from the beginning??

---

### Post by engla on 2009-09-29
Well you can use Python bindings for GLib to change this, just install a .desktop application description for the file, then run in python:

```
python -c 'import gio; gio.unix.DesktopAppInfo("nautilus-browser.desktop").set_as_default_for_extension(...)'
```

Now I don't know if calling python from bash was what you asked for. :-)

---

### Post by Levo on 2009-09-30
> **engla said:**
> Well you can use Python bindings for GLib to change this, just install a .desktop application description for the file, then run in python:

```
python -c 'import gio; gio.unix.DesktopAppInfo("nautilus-browser.desktop").set_as_default_for_extension(...)'
```

Now I don't know if calling python from bash was what you asked for. :-)


Well that's not exactly what I want (because I have to use python.... :( ), but if I don't find something better I'll definitely use it!! Thank you!

---

### Post by geirha on 2009-09-30
Right click on the desktop and choose «Create launcher», and fill in the fields as you want them, possibly setting an Icon. Once done, you'll have a file on your desktop, «Name of launcher.desktop». Open it in an editor and see where the data you filled in appears. You can easily create such a file with bash using something like:
```
#!/bin/bash

cat > MyEntry.desktop << EOF
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Name=My App
Exec=myapp
Comment=My awesome app
EOF

xdg-desktop-menu install MyEntry.desktop
xdg-mime default MyEntry.desktop text/html


```

In addition to those fields, you should add a MimeType that explains what type of files this application can open. E.g. if it can open plain text and html files:
```

MimeType=text/plain;text/html;

```

If you want it to appear in the menus, find a suitable category for it, then look at one of the entries in that category and copy its Categories= line.

These commands may help you a bit:
```

grep 'MimeType=' /usr/share/applications/*.desktop
grep 'Categories=' /usr/share/applications/*.desktop

```

See this for a full documentation on .desktop-files: [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html)

---

### Post by Levo on 2009-10-03
> **geirha said:**
> Right click on the desktop and choose «Create launcher», and fill in the fields as you want them, possibly setting an Icon. Once done, you'll have a file on your desktop, «Name of launcher.desktop». Open it in an editor and see where the data you filled in appears. You can easily create such a file with bash using something like:
```
#!/bin/bash

cat > MyEntry.desktop << EOF
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Name=My App
Exec=myapp
Comment=My awesome app
EOF

xdg-desktop-menu install MyEntry.desktop
xdg-mime default MyEntry.desktop text/html


```

In addition to those fields, you should add a MimeType that explains what type of files this application can open. E.g. if it can open plain text and html files:
```

MimeType=text/plain;text/html;

```

If you want it to appear in the menus, find a suitable category for it, then look at one of the entries in that category and copy its Categories= line.

These commands may help you a bit:
```

grep 'MimeType=' /usr/share/applications/*.desktop
grep 'Categories=' /usr/share/applications/*.desktop

```

See this for a full documentation on .desktop-files: [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html)

I had read the freedesktop documentation before, but it couldn't help. I tried what you described, the application is registered correctly, it appears in the appropriate menu, but it still doesn't become the default for the filetype, although it is correctly set in ~/.local/share/applications/defaults.list

---

### Post by geirha on 2009-10-04
Does it not open the file at all, or does it open it with the wrong app?

Is the output you get with the following commands what you expect?
```

xdg-mime query filetype *thefile.asd*
xdg-mime query default $(xdg-mime query filetype *thefile.asd*)
xdg-open *thefile.asd*

```

---

### Post by Levo on 2009-10-04
> **geirha said:**
> Does it not open the file at all, or does it open it with the wrong app?

Is the output you get with the following commands what you expect?
```

xdg-mime query filetype *thefile.asd*
xdg-mime query default $(xdg-mime query filetype *thefile.asd*)
xdg-open *thefile.asd*

```

The filetype already exists, I want to make it open with another application.

---


---
title: "Building Installer Wizards"
date: 2006-12-16
forum: Programming Talk
---

### Post by SuperMike on 2006-12-16
Has anyone ever built an attractive wizard interface in C/C++ and X API that can be called from Bash scripts to provide quick and dirty application wizard installers? I could then compile this with **makeself** into a single, executable file.

Okay, if that won't fly, has anyone ever built a Python/PyGTK wizard framework for building quick and dirty installers, and which doesn't have a huge learning curve?

If not, then here's my programmer wish for 2007. I'd like to see a C (GCC) based application that can draw simplistic wizard windows on X (hopefully GNOME-ish) that can be called from Bash scripts.

---

### Post by Wybiral on 2006-12-16
You might want to check out [glade]("http://glade.gnome.org/"). It is a GUI designer. Here is an article on using glade with python: [http://www.linuxjournal.com/article/7421](http://www.linuxjournal.com/article/7421)

---

### Post by Wybiral on 2006-12-16
OH, I almost forgot... Zenity is also a really nice GUI tool for shell. Here's an example. (It doesn't actually DO anything, just shows off some of zenity)

```

#!/bin/bash

if $(`zenity  --question --title "???"   --text  "Ok or cancel?"`); then
	zenity --info --text "You selected OK!"
else
	zenity --info --text "You selected Cancel!"
fi

file1=`ls |  zenity  --list  --title "Contents viewer" --text "Contents of directory" --column "Files"`

name=`zenity --title  "Name?" --entry --text "Whats your name?"`

file2=`zenity --title="Well $name, select a file!" --file-selection`

choice=`zenity  --list --title "$name, does this look right?" --checklist --text "" --column "Install" --column "File" TRUE $file1 TRUE $file2`

zenity --info --text "You selected: $choice"

```

---

### Post by SuperMike on 2006-12-17
> **Wybiral said:**
> You might want to check out [glade]("http://glade.gnome.org/"). 

Yeah, I wrote [**pgst**]("http://sourceforge.net/projects/pgst/") using Glade, Python, and PyGTK a few years ago.

For those wanting to build rich client GUIs on Linux, it's a thing to start with, although it's sometimes complex.

Here's another route to building Installer Wizards on Linux:

* Build a quick and dirty [**Mozilla XUL Chrome**]("http://www.nuxified.org/topic/more_on_firefox_rich_client_implementations") that you can tell Firefox to load. It can be nothing but a web browser shell with no buttons, menus, or toolbars -- just the web page you want to load and a titlebar.

* Connect it to thttpd, the thin, embeddable HTML server with CGI support on an exclusive local 127.0.0.1 port.

* Connect it to ngs-js for very thin CGI Javascript support with the ability to pipe a process out to Bash, or Perl CGI, or Python CGI, or PHP CGI, or Bash. The ngs-js or straight Bash is probably going to be your lightest option with the least amount of dependency downloads (or download size).

* If you need a database, use SQLite for a thin, embeddable database.

---

### Post by maddog39 on 2006-12-17
Hmmm... this is a good idea, I might make either a python or a C++ library built on GTK to make a really nice windows style GUI installer, then maybe post it on SourceForge. Anyone who's possibly interested in doing that project with me, feel free to shoot me a PM(Private Message for those of you who happen to not know what that means :P).

MSN: admin.maddog39 [at] gmail [dot] com        or MSN :)

---


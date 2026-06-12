---
title: "Question about package, library and tool"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by ruwan2 on 2014-01-05
Hi,
I am new to Linux. Below the dot line is from a software description. The second line says packages to build. The red line looks like to build the Gstreamer. What are the packages? The blue lines are tools I guess. Could you give me some explanation on these lines?

Thank,


............................
The following lists some of the software components and dependencies associated with the Sitara SDK.
Dependancies: Required packages to build Gstreamer on Ubuntu:
[COLOR=#800000]sudo apt-get install automake autoconf libtool docbook-xml docbook-xsl fop libxml2 gnome-doc-utils[/COLOR]
[COLOR=#000080]• build-essential
• libtool
• automake
• autoconf
• git-core
• svn
• liboil0.3-dev
• libxml2-dev
• libglib2.0-dev
• gettext
• corkscrew
• socket
• libfaad-dev
• libfaac-dev[/COLOR]

Software components for Sitara SDK Release:
•
•
•
•
•
•
•
glib
gstreamer
liboil
gst-plugins-good
gst-ffmpeg
gst-plugins-bad
gst-plugins-base

---

### Post by MG&amp;TL on 2014-01-05
I have no idea why they're separated and what the distinction is, but they're a mixture of libraries (e.g. *libxml*) and programs to build source code (*automake*). If the software package says to install them, I imagine the best thing to do would be to install them (via *apt-get* or whatever, not from source unless you need to) and then see if you can use the package correctly.

---

### Post by devine.steve on 2014-01-05
When you ask the package manager to install something it will check for dependencies and if it finds that the system needs additional software it asks your permission to install it. Or am I misunderstanding this? If it doesn't do this automatically you will need to install them by copying the line beginning with "sudo apt-get .."

---

### Post by ian-weisser on 2014-01-05
You are misunderstanding.
The package cache on your system includes a list of every package's immediate dependencies.
When the package manager (apt) installs a package, it consults the cache for those lists. It constructs from those lists a dependency tree of *all* dependencies needed, and then downloads and installs everything needed in the same session.

You can see the cache immediate dependencies and reverse-dependencies using the **apt-cache** command.
```
$ apt-cache depends hello
hello
  Depends: libc6
 |Depends: dpkg
  Depends: install-info

```

---


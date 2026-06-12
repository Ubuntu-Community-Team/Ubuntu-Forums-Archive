---
title: "-lwx_gtk2_xrc-2.4"
date: 2005-04-09
forum: Packaging and Compiling Programs
---

### Post by Quest-Master on 2005-04-09
I really need to compile this application (not available in apt repos.), and when being compiled with GCC it requires the -lwx_gtk2_xrc-2.4 extension. Now, I've scoured the repositories to find what package I need to enable this, but I'm still at a loss.

If anyone has any idea on which package(s) I should install, please point them out to me. I'd greatly appreciate it.

---

### Post by jobezone on 2005-04-09
[QUOTE=Quest-Master]I really need to compile this application (not available in apt repos.), and when being compiled with GCC it requires the -lwx_gtk2_xrc-2.4 extension. Now, I've scoured the repositories to find what package I need to enable this, but I'm still at a loss.

If anyone has any idea on which package(s) I should install, please point them out to me. I'd greatly appreciate it.[/QUOTE]

Install apt-file (in Universe):
"Unlike apt-cache, you can search in which package a file is included or 
list the contents of a package without instaling or fetching it."

---

### Post by Quest-Master on 2005-04-10
Still haven't found the needed package, even after doing that jobezone.

:(

---

### Post by jobezone on 2005-04-10
[QUOTE=Quest-Master]Still haven't found the needed package, even after doing that jobezone.

:([/QUOTE]
 Perhaps try searching the answer in the home page of the software you are trying to compile, like:
- Compilation instructions
- The Faq
- Ask in the mailing list

---


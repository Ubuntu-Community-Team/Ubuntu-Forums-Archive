---
title: "anjuta file associations"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by lucianct on 2008-09-20
i need to associate anjuta ide with c/cpp files, but i can't figure out the command line for anjuta. if i run "anjuta filename.c" i get the following error:

> ** (anjuta:6529): CRITICAL **: anjuta_document_load: assertion `anjuta_utils_is_valid_uri (uri)' failed

(anjuta:6529): libgnomevfs-CRITICAL **: gnome_vfs_uri_new_private: assertion `text_uri != NULL' failed

(anjuta:6529): libgnomevfs-CRITICAL **: gnome_vfs_uri_new_private: assertion `text_uri != NULL' failed

** (anjuta:6529): CRITICAL **: an_file_history_push: assertion `uri' failed


i searched the man pages for anjuta but i still can't find a solution...

---

### Post by Mornedhel on 2008-09-20
You can set file associations in Nautilus. Right-click on a C source file, select Properties, Open with, add Anjuta, select Anjuta in the list of associated editors. Repeat for C++ file sources, and C/C++ headers.

---

### Post by lucianct on 2008-09-20
i did so before posting here. it's not working as the command "anjuta filename.c" does not open the file filename.c, but instead it opens a new document.

---

### Post by Mornedhel on 2008-09-21
I just installed and tried it, and you're absolutely right. Perhaps Anjuta is more project-oriented, I don't know.

If you are only looking for C syntax highlighting and smart indentation, I recommend using either of Anjuta's edition backends, gedit (actually gtksourceview, but gedit is the simplest editor to make use of it) and SciTE (same deal with Scintilla).

---


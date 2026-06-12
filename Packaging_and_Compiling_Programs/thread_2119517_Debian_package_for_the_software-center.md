---
title: "Debian package for the software-center"
date: 2013-02-24
forum: Packaging and Compiling Programs
---

### Post by melfnt on 2013-02-24
Hi all, I'm Italian and I don't speak English very     well.
    I have a Debian package build on launchpad, in the "quantal" series.
    The Makefile installs its file in /usr/share and other folder.
    
    Now, I want to submit it for the software-center, so I have to make     a program that installs itself in /opt/extras.ubuntu.com/....     directory.
    I cannot create a new version of the package, because it will     override the older in launchpad.
    
    -Can I submit the current package, even if it doesn't put the file     in the "right" directory?
    -Should I make another package, with different name?
    -Or should I publish this one in any another series?
    
    Thank you for the reply
;)

---

### Post by melfnt on 2013-03-01
No answer?
Did someone ever submit an app for the software-center?

---

### Post by Malsasa on 2013-03-02
Hello, I am Indonesian. I don't understand too much but if you wanna your app available in the USC, you can follow this page: 

[http://developer.ubuntu.com/publish/](http://developer.ubuntu.com/publish/)

Hope this will be useful.

---

### Post by melfnt on 2013-03-02
Hi malsasa.

I had already read in that page:
> 
 							[h=3]Advanced users[/h] 							If you are already familiar with Debian packaging and would  like to submit your existing Debian source package for review, we will  be happy to accept it. Please create a tarball of the source package,  both 32 and 64 bit if you have it, and upload.

 						


But I also read:
> 
[h=3]echnical requirements[/h] In order for your application to be distributed in the Software Centre it must:
 
[LIST]
[*]Be in one, self-contained directory when installed
[*]Be able to be installed into the /opt/<package-name> directory (*)
[*]Be executable by all users from the /opt/<package-name> directory (**)
[*]Write all configuration settings to ~/.config/<package-name> (This can be one file or a directory containing multiple configuration files)
[/LIST]


So, should I make my program install in /opt, shouldn't I?
I tried to install an application from the software-center: it DOESN'T install itself in /opt.

For example geany:
```

lucio@computerLucio:~$ locate geany
/home/lucio/.cache/software-center/icons/chart-geany-full-1-icon-logo64_1.png
/home/lucio/.cache/software-center/icons/chart-geany-trial-1-icon-logo64_2.png
/home/lucio/.config/geany
/home/lucio/.config/geany/colorschemes
/home/lucio/.config/geany/filedefs
/home/lucio/.config/geany/geany.conf
/home/lucio/.config/geany/tags
/home/lucio/.config/geany/templates
/home/lucio/.config/geany/filedefs/filetypes.README
/home/lucio/.config/geany/filedefs/filetypes.c
/home/lucio/.config/geany/filedefs/filetypes.cpp
/home/lucio/.config/geany/filedefs/filetypes.html
/home/lucio/.config/geany/filedefs/filetypes.php
/home/lucio/.config/geany/templates/files
/home/lucio/.config/geany/templates/templates.README
/usr/bin/geany
/usr/include/geany
/usr/include/geany/document.h
/usr/include/geany/editor.h
/usr/include/geany/encodings.h
/usr/include/geany/filetypes.h
/usr/include/geany/geany.h
/usr/include/geany/geanyfunctions.h
/usr/include/geany/geanyplugin.h
/usr/include/geany/highlighting.h
/usr/include/geany/keybindings.h
/usr/include/geany/msgwindow.h
/usr/include/geany/plugindata.h
/usr/include/geany/prefs.h
/usr/include/geany/project.h
/usr/include/geany/scintilla
/usr/include/geany/search.h
/usr/include/geany/stash.h
/usr/include/geany/support.h
/usr/include/geany/tagmanager
/usr/include/geany/templates.h
/usr/include/geany/toolbar.h
/usr/include/geany/ui_utils.h
/usr/include/geany/utils.h
/usr/include/geany/scintilla/SciLexer.h
/usr/include/geany/scintilla/Scintilla.h
/usr/include/geany/scintilla/Scintilla.iface
/usr/include/geany/scintilla/ScintillaWidget.h
/usr/include/geany/tagmanager/tm_file_entry.h
/usr/include/geany/tagmanager/tm_project.h
/usr/include/geany/tagmanager/tm_source_file.h
/usr/include/geany/tagmanager/tm_symbol.h
/usr/include/geany/tagmanager/tm_tag.h
/usr/include/geany/tagmanager/tm_tagmanager.h
/usr/include/geany/tagmanager/tm_work_object.h
/usr/include/geany/tagmanager/tm_workspace.h
/usr/lib/x86_64-linux-gnu/geany
/usr/lib/x86_64-linux-gnu/geany/classbuilder.so
/usr/lib/x86_64-linux-gnu/geany/export.so
/usr/lib/x86_64-linux-gnu/geany/filebrowser.so
/usr/lib/x86_64-linux-gnu/geany/htmlchars.so
/usr/lib/x86_64-linux-gnu/geany/saveactions.so
/usr/lib/x86_64-linux-gnu/geany/splitwindow.so
/usr/lib/x86_64-linux-gnu/pkgconfig/geany.pc
/usr/share/geany
/usr/share/app-install/desktop/geany:geany.desktop
/usr/share/app-install/icons/geany.png
/usr/share/applications/geany.desktop
/usr/share/doc/geany
/usr/share/doc/geany-common
/usr/share/doc/geany/NEWS.Debian.gz
/usr/share/doc/geany/NEWS.gz
/usr/share/doc/geany/README
/usr/share/doc/geany/THANKS.gz
/usr/share/doc/geany/TODO
/usr/share/doc/geany/changelog.Debian.gz
/usr/share/doc/geany/copyright
/usr/share/doc/geany/html
/usr/share/doc/geany/manual.txt.gz
/usr/share/doc/geany/html/images
/usr/share/doc/geany/html/index.html
/usr/share/doc/geany/html/images/build_menu_commands_dialog.png
/usr/share/doc/geany/html/images/find_dialog.png
/usr/share/doc/geany/html/images/find_in_files_dialog.png
/usr/share/doc/geany/html/images/main_window.png
/usr/share/doc/geany/html/images/pref_dialog_edit_completions.png
/usr/share/doc/geany/html/images/pref_dialog_edit_display.png
/usr/share/doc/geany/html/images/pref_dialog_edit_features.png
/usr/share/doc/geany/html/images/pref_dialog_edit_indentation.png
/usr/share/doc/geany/html/images/pref_dialog_files.png
/usr/share/doc/geany/html/images/pref_dialog_gen_misc.png
/usr/share/doc/geany/html/images/pref_dialog_gen_startup.png
/usr/share/doc/geany/html/images/pref_dialog_interface_interface.png
/usr/share/doc/geany/html/images/pref_dialog_interface_notebook.png
/usr/share/doc/geany/html/images/pref_dialog_interface_toolbar.png
/usr/share/doc/geany/html/images/pref_dialog_keys.png
/usr/share/doc/geany/html/images/pref_dialog_printing.png
/usr/share/doc/geany/html/images/pref_dialog_templ.png
/usr/share/doc/geany/html/images/pref_dialog_tools.png
/usr/share/doc/geany/html/images/pref_dialog_various.png
/usr/share/doc/geany/html/images/pref_dialog_vte.png
/usr/share/doc/geany/html/images/replace_dialog.png
/usr/share/doc/geany-common/NEWS.Debian.gz
/usr/share/doc/geany-common/changelog.Debian.gz
/usr/share/doc/geany-common/copyright
/usr/share/doc-base/geany
/usr/share/geany/c99.tags
/usr/share/geany/colorschemes
/usr/share/geany/filetype_extensions.conf
/usr/share/geany/filetypes.Cython.conf
/usr/share/geany/filetypes.Genie.conf
/usr/share/geany/filetypes.Scala.conf
/usr/share/geany/filetypes.abc
/usr/share/geany/filetypes.actionscript
/usr/share/geany/filetypes.ada
/usr/share/geany/filetypes.asm
/usr/share/geany/filetypes.c
/usr/share/geany/filetypes.caml
/usr/share/geany/filetypes.cmake
/usr/share/geany/filetypes.cobol
/usr/share/geany/filetypes.common
/usr/share/geany/filetypes.conf
/usr/share/geany/filetypes.cpp
/usr/share/geany/filetypes.cs
/usr/share/geany/filetypes.css
/usr/share/geany/filetypes.d
/usr/share/geany/filetypes.diff
/usr/share/geany/filetypes.docbook
/usr/share/geany/filetypes.erlang
/usr/share/geany/filetypes.f77
/usr/share/geany/filetypes.ferite
/usr/share/geany/filetypes.forth
/usr/share/geany/filetypes.fortran
/usr/share/geany/filetypes.freebasic
/usr/share/geany/filetypes.glsl
/usr/share/geany/filetypes.haskell
/usr/share/geany/filetypes.haxe
/usr/share/geany/filetypes.html
/usr/share/geany/filetypes.java
/usr/share/geany/filetypes.javascript
/usr/share/geany/filetypes.latex
/usr/share/geany/filetypes.lisp
/usr/share/geany/filetypes.lua
/usr/share/geany/filetypes.makefile
/usr/share/geany/filetypes.markdown
/usr/share/geany/filetypes.matlab
/usr/share/geany/filetypes.nsis
/usr/share/geany/filetypes.pascal
/usr/share/geany/filetypes.perl
/usr/share/geany/filetypes.php
/usr/share/geany/filetypes.po
/usr/share/geany/filetypes.python
/usr/share/geany/filetypes.r
/usr/share/geany/filetypes.restructuredtext
/usr/share/geany/filetypes.ruby
/usr/share/geany/filetypes.sh
/usr/share/geany/filetypes.sql
/usr/share/geany/filetypes.tcl
/usr/share/geany/filetypes.txt2tags
/usr/share/geany/filetypes.vala
/usr/share/geany/filetypes.verilog
/usr/share/geany/filetypes.vhdl
/usr/share/geany/filetypes.xml
/usr/share/geany/filetypes.yaml
/usr/share/geany/html_entities.tags
/usr/share/geany/pascal.tags
/usr/share/geany/php.tags
/usr/share/geany/python.tags
/usr/share/geany/snippets.conf
/usr/share/geany/templates
/usr/share/geany/ui_toolbar.xml
/usr/share/geany/colorschemes/alt.conf
/usr/share/geany/templates/bsd
/usr/share/geany/templates/changelog
/usr/share/geany/templates/fileheader
/usr/share/geany/templates/files
/usr/share/geany/templates/function
/usr/share/geany/templates/gpl
/usr/share/geany/templates/files/file.html
/usr/share/geany/templates/files/file.php
/usr/share/geany/templates/files/file.rb
/usr/share/geany/templates/files/file.tex
/usr/share/geany/templates/files/main.c
/usr/share/geany/templates/files/main.cxx
/usr/share/geany/templates/files/main.d
/usr/share/geany/templates/files/main.java
/usr/share/geany/templates/files/main.py
/usr/share/geany/templates/files/main.vala
/usr/share/geany/templates/files/program.pas
/usr/share/icons/hicolor/16x16/apps/geany.png
/usr/share/icons/hicolor/48x48/apps/geany.png
/usr/share/icons/hicolor/scalable/apps/geany.svg
/usr/share/locale/ast/LC_MESSAGES/geany.mo
/usr/share/locale/be/LC_MESSAGES/geany.mo
/usr/share/locale/bg/LC_MESSAGES/geany.mo
/usr/share/locale/ca/LC_MESSAGES/geany.mo
/usr/share/locale/cs/LC_MESSAGES/geany.mo
/usr/share/locale/de/LC_MESSAGES/geany.mo
/usr/share/locale/el/LC_MESSAGES/geany.mo
/usr/share/locale/en_GB/LC_MESSAGES/geany.mo
/usr/share/locale/es/LC_MESSAGES/geany.mo
/usr/share/locale/fa/LC_MESSAGES/geany.mo
/usr/share/locale/fi/LC_MESSAGES/geany.mo
/usr/share/locale/fr/LC_MESSAGES/geany.mo
/usr/share/locale/gl/LC_MESSAGES/geany.mo
/usr/share/locale/hu/LC_MESSAGES/geany.mo
/usr/share/locale/it/LC_MESSAGES/geany.mo
/usr/share/locale/ja/LC_MESSAGES/geany.mo
/usr/share/locale/kk/LC_MESSAGES/geany.mo
/usr/share/locale/ko/LC_MESSAGES/geany.mo
/usr/share/locale/lb/LC_MESSAGES/geany.mo
/usr/share/locale/nl/LC_MESSAGES/geany.mo
/usr/share/locale/pl/LC_MESSAGES/geany.mo
/usr/share/locale/pt/LC_MESSAGES/geany.mo
/usr/share/locale/pt_BR/LC_MESSAGES/geany.mo
/usr/share/locale/ro/LC_MESSAGES/geany.mo
/usr/share/locale/ru/LC_MESSAGES/geany.mo
/usr/share/locale/sl/LC_MESSAGES/geany.mo
/usr/share/locale/sv/LC_MESSAGES/geany.mo
/usr/share/locale/tr/LC_MESSAGES/geany.mo
/usr/share/locale/uk/LC_MESSAGES/geany.mo
/usr/share/locale/vi/LC_MESSAGES/geany.mo
/usr/share/locale/zh_CN/LC_MESSAGES/geany.mo
/usr/share/locale/zh_TW/LC_MESSAGES/geany.mo
/usr/share/man/man1/geany.1.gz
/usr/share/menu/geany
/usr/share/pixmaps/geany.xpm
/var/lib/doc-base/documents/geany
/var/lib/doc-base/omf/geany
/var/lib/doc-base/omf/geany/geany-C.omf
/var/lib/dpkg/info/geany-common.list
/var/lib/dpkg/info/geany-common.md5sums
/var/lib/dpkg/info/geany.list
/var/lib/dpkg/info/geany.md5sums
/var/lib/dpkg/info/geany.postinst
/var/lib/dpkg/info/geany.postrm

```

/usr, /var, bot *NO* /opt
Can someone tell me why?

---

### Post by schragge on 2013-03-04
Because *geany* is part of the standard distribution. The /opt part is for  independent developers that want their apps to be distributed in Ubuntu's [extras repository]("http://askubuntu.com/questions/8570/what-is-http-extras-ubuntu-com-repository-for").

---

### Post by melfnt on 2013-03-05
Ok, that explained me a lot of things.

So, I must makes my program install itself in /opt
Or can I simply submit the current package as it is (and make it became part of the standard distribution, if it is possible...) ?

Thank you for the reply

---

### Post by melfnt on 2013-03-19
Solved:
I should use 2 different PPAs: one for the "extras" program (that installs itself in /opt) and the other for the "normal" version (that uses /usr/share).

Thank you a lot for helping me.

---


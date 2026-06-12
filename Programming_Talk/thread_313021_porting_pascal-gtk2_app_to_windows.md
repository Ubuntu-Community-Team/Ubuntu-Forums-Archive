---
title: "porting pascal-gtk2 app to windows"
date: 2006-12-05
forum: Programming Talk
---

### Post by Mr..Yeti on 2006-12-05
I've made an app using pascal and gtk2, it is very simple, 2 buttons and a label, on ubuntu this compiled fine after downloading the gtk-dev packages and the FPC-GTK2-units package. 
However, on windows I do not know which files to download. I've tried the gladewin32-dev files, which allowed me to use my pygtk apps, but this did not sort out the pascal problem.

Is it possible to use pascal and gtk2 on windows? Which packages do  need?

Ty

---

### Post by ansi on 2006-12-05
I think it is possible. See the following links:

[Freepascal GTK info]("http://freepascal.org/packages/gtk.html") 
[Freepascal::GTK]("ftp://ftp.freepascal.org/fpc/dist/source-2.0.4/separate/units-fpgtk.source.zip")

It may help you.


P.S. And don't forget to download compiled GTK libraries for Offtopic ;) from [official GTK's site]("http://www.gtk.org/").

---

### Post by Mr..Yeti on 2006-12-06
Thanks. That works. I got the full windows installer of FPC, which included the gtk2 part. I guess the problem was that i was using the FPCompiler that came with dev-pascal, instead of the full 'Official' Free Pascal Compiler.

Thanks alot.

---


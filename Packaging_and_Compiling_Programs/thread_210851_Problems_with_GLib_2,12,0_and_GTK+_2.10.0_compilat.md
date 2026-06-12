---
title: "Problems with GLib 2,12,0 and GTK+ 2.10.0 compilation problem"
date: 2006-07-07
forum: Packaging and Compiling Programs
---

### Post by tomcio on 2006-07-07
Hi!

So like in topic, I'm trying to install GTK+ 2.10 in my Ubuntu 6.06. Firstly I installed all stuff, which was required by GLib 2.12 and GTK+ 2.10 and I run GLib compilation. Generally it was compiling itself only for a few seconds :(  because of this 'make' error:
[INDENT]
Making all in gobject
make[2]: Wej&#347;cie do katalogu `/home/tomek/Programy/GTK+ 2.10/glib-2.12.0/gobject'
make glib-genmarshal
make[3]: Wej&#347;cie do katalogu `/home/tomek/Programy/GTK+ 2.10/glib-2.12.0/gobject'
make[3]: `glib-genmarshal' jest aktualne.
make[3]: Opuszczenie katalogu `/home/tomek/Programy/GTK+ 2.10/glib-2.12.0/gobject'
echo "#ifndef __G_MARSHAL_H__" > xgen-gmh \
        && echo "#define __G_MARSHAL_H__" >> xgen-gmh \
        && ./glib-genmarshal --nostdinc --prefix=g_cclosure_marshal ./gmarshal.list --header >> xgen-gmh \
        && echo "#endif /* __G_MARSHAL_H__ */" >> xgen-gmh \
        && (cmp -s xgen-gmh gmarshal.h 2>/dev/null || cp xgen-gmh gmarshal.h) \
        && rm -f xgen-gmh xgen-gmh~ \
        && echo timestamp > stamp-gmarshal.h
./glib-genmarshal: line 87: cd: /home/tomek/Programy/GTK+: Nie ma takiego pliku ani katalogu
gcc: 2.10/glib-2.12.0/gobject/.libs/4989-lt-glib-genmarshal: Nie ma takiego pliku ani katalogu
make[2]: *** [stamp-gmarshal.h] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/home/tomek/Programy/GTK+ 2.10/glib-2.12.0/gobject'
make[1]: *** [all-recursive] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/tomek/Programy/GTK+ 2.10/glib-2.12.0'
make: *** [all] B&#322;&#261;d 2
[/INDENT]


Any ideas how to solve this:?:

---


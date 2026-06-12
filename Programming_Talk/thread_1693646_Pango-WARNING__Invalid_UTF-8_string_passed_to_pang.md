---
title: "Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()"
date: 2011-02-23
forum: Programming Talk
---

### Post by dragos2 on 2011-02-23
I am having this error at run time after I type some text inside text boxes:

```

Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

```

The program was compiled with
```

/sunstudio/sunstudio12.1/bin/sunc99 cfileshere.c `pkg-config --libs --cflags gtk+-2.0`

```

and MALLOC_CHECK=0 is set

GTK libraries installed
```

ii  libgtk-vnc-1.0-0                      0.3.4-0ubuntu2                          A VNC viewer widget for GTK+ (runtime librar
ii  libgtk2-perl                          1:1.161-1                               Perl interface to the 2.x series of the Gimp
ii  libgtk2.0-0                           2.12.9-3ubuntu5                         The GTK+ graphical user interface library
ii  libgtk2.0-bin                         2.12.9-3ubuntu5                         The programs for the GTK+ graphical user int
ii  libgtk2.0-cil                         2.12.0-2ubuntu3                         CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                      2.12.9-3ubuntu5                         Common files for the GTK+ graphical user int
ii  libgtk2.0-dev                         2.12.9-3ubuntu5                         Development files for the GTK+ library
ii  libgtkhtml2-0                         2.11.1-1                                HTML rendering/editing library - runtime fil
ii  libgtkhtml3.14-19                     3.18.3-0ubuntu2                         HTML rendering/editing library - runtime fil
ii  libgtkhtml3.16-cil                    2.20.1-2ubuntu2                         CLI binding for GtkHTML 3.16
ii  libgtkmm-2.4-1c2a                     1:2.12.5-2                              C++ wrappers for GTK+ 2.4 (shared libraries)
ii  libgtksourceview-common               1.8.5-1                                 common files for the GTK+ syntax highlightin
ii  libgtksourceview1.0-0                 1.8.5-1                                 shared libraries for the GTK+ syntax highlig
ii  libgtksourceview2.0-0                 2.2.2-0ubuntu1                          shared libraries for the GTK+ syntax highlig
ii  libgtksourceview2.0-common            2.2.2-0ubuntu1                          common files for the GTK+ syntax highlightin
ii  libgtkspell0                          2.0.10-4                                a spell-checking addon for GTK's TextView wi

```

Any suggestions please ?

---

### Post by nvteighen on 2011-02-23
Ugh... please, send us the code that produces this error. We're not psychic. If too long, trim it to a snippet that produces the bug.

Very probably, you have failed to set the locale to UTF-8 or something like that. Or you're passing a UTF-8 static string which should be ASCII formatted.

---

### Post by dragos2 on 2011-02-24
> **nvteighen said:**
> Ugh... please, send us the code that produces this error. We're not psychic. If too long, trim it to a snippet that produces the bug.

Very probably, you have failed to set the locale to UTF-8 or something like that. Or you're passing a UTF-8 static string which should be ASCII formatted.

Thanks for interest. The program comes from a Solaris system with a C locale which I
also set here.

Here is a code snipped in which I suspect the error occurs:
```

 i = 0; str3 = gtk_editable_get_chars (GTK_EDITABLE (comm[j][i] ), 0, -1);
          for(k=0; k<20; k++) {ProjNo[k] = str3[k]; free(str3); }
          i = 1; str3 = gtk_editable_get_chars (GTK_EDITABLE (comm[j][i] ), 0, -1);
          for(k=0; k<20; k++) {Cust[k] = str3[k]; free(str3); }
          i = 2; str3 = gtk_editable_get_chars (GTK_EDITABLE (comm[j][i] ), 0, -1);
          for(k=0; k<10; k++) {User[k] = str3[k]; free(str3); }
          i = 4; str3 = gtk_editable_get_chars (GTK_EDITABLE (comm[j][i] ), 0, -1);
          for(k=0; k<15; k++) {aux1[k] = str3[k]; free(str3); }
          str3 = gtk_editable_get_chars (GTK_EDITABLE (comm[j][i+1] ), 0, -1);
          {if( atof(str3) < a_eps && atof(str3) > -a_eps) aux1kg = a_eps;
          else aux1kg = atof(str3); } free(str3);
          str3 = gtk_editable_get_chars (GTK_EDITABLE (comm[j][i+2] ), 0, -1);
          {if( atof(str3) < a_eps && atof(str3) > -a_eps) aux1kgCost = a_eps;
          else aux1kgCost = atof(str3)*EURorCZK; } free(str3);
          i = 7; str3 = gtk_editable_get_chars (GTK_EDITABLE (comm[j][i] ), 0, -1);
          for(k=0; k<15; k++) {aux2[k] = str3[k]; free(str3); }
....

```

---


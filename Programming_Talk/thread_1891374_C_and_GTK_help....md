---
title: "C and GTK help..."
date: 2011-12-05
forum: Programming Talk
---

### Post by etdsbastar on 2011-12-05
Hello friends,

I am making a simple GTK program using CodeBlocks. Here is the code:

```
int
main(int argc, char **argv)
{
    GladeXML *xml;
    gchar *filename;

    GnomeProgram *program;

    g_type_init();

    filename = gnome_program_locate_file(program, GNOME_FILE_DOMAIN_APP_DATADIR, "ptms.glade", TRUE, NULL);

    xml = glade_xml_new(filename, "window1", NULL);

    gtk_main();

    return 0;
}
```

This program is showing the following errors:

/package.projects/c/ptms/src/main.c|25|warning: variable ‘xml’ set but not used [-Wunused-but-set-variable]|
/package.projects/c/ptms/src/framework.h|21|warning: ‘pkginfo’ defined but not used [-Wunused-variable]|
/package.projects/c/ptms/src/main.c||In function ‘main’:|
/package.projects/c/ptms/src/main.c|32|warning: ‘program’ is used uninitialized in this function [-Wuninitialized]|
||=== Build finished: 0 errors, 3 warnings ===|

and if I am running the program via the terminal the error is :
SEGMENTATION FAULT

Please help.

---

### Post by SevenMachines on 2011-12-05
>  /package.projects/c/ptms/src/main.c|32|warning: ‘program’ is used uninitialized in this function [-Wuninitialized]| This is usually a sign something bad will happen, you need to have program point to some sort of valid GnomeProgram or replace it with NULL to the use current application.

---

### Post by Petrolea on 2011-12-05
Read warnings. They literally tell you what's wrong. 

Variable xml is set but never used. That's true, it is set, but you never use it.

Pkginfo is initialized, but never used. This means that variable is initialized, but never used.

Program is used, but uninitialized. You can't use something that doesn't even have a value. You must first initialize it. You pass an empty variable to a function - I guess this is where segfault comes from also.

---

### Post by etdsbastar on 2011-12-05
Thanks,

I changed the code little bit ... onto this:

```
int
main (int argc, char *argv[])
{
    GtkBuilder      *builder;
    GtkWidget       *window;

    gtk_init (&argc, &argv);

    builder = gtk_builder_new ();
    gtk_builder_add_from_file (builder, "ptms.glade", NULL);
    window = GTK_WIDGET (gtk_builder_get_object (builder, "window1"));
    gtk_builder_connect_signals (builder, NULL);

    g_object_unref (G_OBJECT (builder));

    gtk_widget_show (window);
    gtk_main ();

    return 0;
}
```

This is showing the error:
```
(ptms-2011:5159): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

```

---

### Post by Petrolea on 2011-12-05
> **etdsbastar said:**
> Thanks,

I changed the code little bit ... onto this:

```
int
main (int argc, char *argv[])
{
    GtkBuilder      *builder;
    GtkWidget       *window;

    gtk_init (&argc, &argv);

    builder = gtk_builder_new ();
    gtk_builder_add_from_file (builder, "ptms.glade", NULL);
    window = GTK_WIDGET (gtk_builder_get_object (builder, "window1"));
    gtk_builder_connect_signals (builder, NULL);

    g_object_unref (G_OBJECT (builder));

    gtk_widget_show (window);
    gtk_main ();

    return 0;
}
```

This is showing the error:
```
(ptms-2011:5159): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

```

It means that widget you put into gtk_widget_show function isn't recognised as widget. there's probably a wrong value in variable 'window'.

EDIT: I'm pretty sure that error occurs when you retrieve 'window' from glade file. Make sure that name in glade file is same as you pass it in you program.

---

### Post by etdsbastar on 2011-12-06
I couldn't get you what you are saying....

Please anyone can tell me the corrected code. It will be a great help to me...

Thanks.

---

### Post by Petrolea on 2011-12-06
> **etdsbastar said:**
> I couldn't get you what you are saying....

Please anyone can tell me the corrected code. It will be a great help to me...

Thanks.

Check if the name of window in Glade is the same as the one you name here: gtk_builder_get_object (builder, "window1")

---

### Post by etdsbastar on 2011-12-08
> **Petrolea said:**
> Check if the name of window in Glade is the same as the one you name here: gtk_builder_get_object (builder, "window1")


everything is ok. no success !!!

---

### Post by Petrolea on 2011-12-09
> **etdsbastar said:**
> everything is ok. no success !!!
There's an error with your .glade file. As far as I know, you must use a .xml file, which you can get by converting the .glade file or saving it as .xml (but you must use appropriate version and library).

---


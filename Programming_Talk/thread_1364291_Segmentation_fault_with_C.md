---
title: "Segmentation fault with C"
date: 2009-12-25
forum: Programming Talk
---

### Post by Seano911 on 2009-12-25
I'm a newbie to C (and programming as a whole really), and am trying to make a basic calculator using GTK+. I've stopped at one button and a textbox for now trying to make sure clicking the button adds the number to the textbox. However, everytime I click the button the program closes and the terminal window says:
```
Segmentation fault
```

There are no warnings when I compile it using:
```
gcc calctest.c -o calctest `pkg-config --libs --cflags gtk+-2.0`

```

Here's my code:
```
#include <gtk/gtk.h>
#include <string.h>


void buttonFunc(GtkWidget *widget, gpointer display) {
	const gchar *displayText = gtk_entry_get_text(GTK_ENTRY(display));
	
	const gchar *displayText2 = (gchar *)strcat((char *)displayText, "1");
	
	gtk_entry_set_text(GTK_ENTRY(display), displayText2);
}

int main(int argc, char *argv[]) {
	GtkWidget *window;
	GtkWidget *fixed;
	GtkWidget *display;
	GtkWidget *button;
	
	gtk_init(&argc, &argv);
	
	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_window_set_title(GTK_WINDOW(window), "gCalc");
	
	fixed = gtk_fixed_new();
	
	display = gtk_entry_new();
	gtk_fixed_put(GTK_FIXED(fixed), display, 5, 5);
	gtk_widget_set_size_request(display, 200, 25);
	
	button = gtk_button_new_with_label("1");
	gtk_fixed_put(GTK_FIXED(fixed), button, 25, 35);
	gtk_widget_set_size_request(button, 45, 45);
	
	
	gtk_container_add(GTK_CONTAINER(window), fixed);
	
	g_signal_connect_swapped(G_OBJECT(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);
	g_signal_connect(G_OBJECT(button), "clicked", G_CALLBACK(buttonFunc), G_OBJECT(display));
	
	gtk_widget_show_all(window);
	
	gtk_main();
	
	return 0;
}

```

Can anyone tell me what's wrong?

---

### Post by monkeyking on 2009-12-25
Try compiling with -Wall -ggdb (all warnings and debug symbols).

Then try starting your program from the commmandline doing

gdb ./a.out
run

The program should crash, and then type bt (thats backtrace),
and gdb will tell which line in your code that caused the fault.

That should help you hunt down the error

good luck

---

### Post by Seano911 on 2009-12-25
-wall and -ggdb are unkown options. Is there a specific package I need to install to use these?

---

### Post by monkeyking on 2009-12-25
the -Wall is with a capital W.
the -ggdb should be completely standard.

please post your entire commandline you use when you try to compile

---

### Post by ksa618 on 2009-12-25
Use a capitalized W (-Wall), -wall is unrecognized.

---

### Post by Seano911 on 2009-12-25
Here's the terminal:```
seano911@seano911-desktop:~/JustC$ gcc calctest.c -o calctest `pkg-config 
 --cflags -Wall -ggdb gtk+-2.0`
-Wall: unknown option
calctest.c:1:21: error: gtk/gtk.h: No such file or directory
calctest.c:5: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
calctest.c: In function &#8216;main&#8217;:
calctest.c:14: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
calctest.c:14: error: (Each undeclared identifier is reported only once
calctest.c:14: error: for each function it appears in.)
calctest.c:14: error: &#8216;window&#8217; undeclared (first use in this function)
calctest.c:15: error: &#8216;fixed&#8217; undeclared (first use in this function)
calctest.c:16: error: &#8216;display&#8217; undeclared (first use in this function)
calctest.c:17: error: &#8216;button&#8217; undeclared (first use in this function)
calctest.c:21: error: &#8216;GTK_WINDOW_TOPLEVEL&#8217; undeclared (first use in this 
on)
calctest.c:37: error: &#8216;gtk_main_quit&#8217; undeclared (first use in this functi
calctest.c:38: error: &#8216;buttonFunc&#8217; undeclared (first use in this function)

```

if I remove -Wall the same occurs but it says -ggdb is unknown.

---

### Post by monkeyking on 2009-12-25
Hi

I haven't installed any gtk stuff, so I cant check you specific case but try compiling like

```

gcc calctest.c -o calctest `pkg-config YOURPKG-CONFIG-ARGS` -ggdb -Wall

```

Such that the ggdb wall are arguments to gcc and not pkg-config
good luck

---

### Post by Zugzwang on 2009-12-25
> **Seano911 said:**
> if I remove -Wall the same occurs but it says -ggdb is unknown.

The option should be given outside of the quotes, e.g., after "calctest.c".

---

### Post by Seano911 on 2009-12-26
That compile worked thanks. But when I run gdb ./calctest I get this:
```
seano911@seano911-desktop:~/JustC$ gdb ./calctest
GNU gdb (GDB) 7.0-ubuntu
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/seano911/JustC/calctest...done.
(gdb) 
```

And it hangs there.

---

### Post by napsy on 2009-12-26
You can't modify the string, returned by gtk_entry_get_text(). Quote from Gtk+ API

> Returns: a pointer to the contents of the widget as a string. This string points to internally allocated storage in the widget and **must not be freed, modified or stored**.


So, create a copy of displayText and append the text to that string.

---

### Post by LKjell on 2009-12-26
What is wrong is from line 38 traced back to line 8.```
[COLOR="Red"]const gchar *displayText2 = (gchar *)strcat((char *)displayText, "1");[/COLOR]
```

---

### Post by Some Penguin on 2009-12-26
man gdb

It's waiting for your input, not hanging.

---

### Post by Seano911 on 2009-12-26
Thanks for the help guys. I fixed my problem using gtk_entry_append_test. :)

---

### Post by LKjell on 2009-12-26
> **Seano911 said:**
> Thanks for the help guys. I fixed my problem using gtk_entry_append_test. :)

You should use ```
void                gtk_editable_insert_text            (GtkEditable *editable,
                                                         const gchar *new_text,
                                                         gint new_text_length,
                                                         gint *position);
```

instead

---


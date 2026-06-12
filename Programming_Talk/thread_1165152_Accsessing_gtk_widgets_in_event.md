---
title: "Accsessing gtk widgets in event"
date: 2009-05-20
forum: Programming Talk
---

### Post by matmatmat on 2009-05-20
I have this code & I want to access an entry in the 'generate' function:
```

#include <gtk/gtk.h>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int len = 10;

void generate (GtkObject *object , gpointer user_data)
{
  gtk_entry_set_text(*entry*, "");
  unsigned int iseed = (unsigned int)time(NULL);
  srand (iseed);
  int i = 0;
  char c;
  int length = len;
  while (i <= length){
      int n = rand() % 26;
      char c = (char)(n + 65);
      gtk_entry_append_text(*entry*, c);
      printf("%c",c); 
      ++i;
  }
  printf("\n");
}


void num_changed (GtkObject *spin, gpointer user_data){
        len = gtk_spin_button_get_value_as_int (spin);
        len = len - 1;
}

void destroy_event (GtkObject *object, gpointer user_data)
{
    gtk_main_quit ();
}
 
int main (int argc, char *argv[])
{
GtkBuilder      *builder;
GtkWidget       *window;
GtkWidget       *number;
gtk_init (&argc, &argv);
builder =gtk_builder_new ();
gtk_builder_add_from_file (builder, "guipasswrdgenerator.xml", NULL);
window = GTK_WIDGET (gtk_builder_get_object (builder, "window1"));
gtk_builder_connect_signals (builder, NULL);
g_object_unref (G_OBJECT (builder));
        
    gtk_widget_show (window);                
    gtk_main ();
 
    return 0;
}

```
How do I do it?

---

### Post by crdlb on 2009-05-20
The last parameter to gtk_builder_connect_signals is user_data; pass a pointer to an allocated struct that will be passed to each signal callback as user_data. Also, you should probably change those GtkObject* to the object that has the signal. destroy is the only signal actually from GtkObject (though people usually just connect it directly to gtk_main_quit).

disclaimer: I haven't really used GtkBuilder yet, so I got that first bit from the docs. Normally, g_signal_connect is where you pass the user_data pointer.

---

### Post by matmatmat on 2009-05-21
Can't I just pass a pointer to the entry:
```

entry = GTK_WIDGET (gtk_builder_get_object(builder, "entry"));
gtk_builder_connect_signals (builder, &entry);

```
(when I tried this it didn't work)
Generate function:
```

void generate (GtkObject *object , gpointer user_data)
{
  gtk_entry_set_text(&user_data, "");
  unsigned int iseed = (unsigned int)time(NULL);
  srand (iseed);
  int i = 0;
  char c;
  int length = len;
  while (i <= length){
      int n = rand() % 26;
      char c = (char)(n + 65);
      gtk_entry_append_text(&user_data, c);
      printf("%c",c); 
      ++i;
  }
  printf("\n");
}

```

---

### Post by crdlb on 2009-05-21
Sure, but usually you have more than one thing you need access to. However, that code doesn't really make sense. The returned entry is already a GtkWidget*, so just pass that directly (don't take the address of it), then in the callback ```
GtkWidget *entry = user_data;

/* later ... */
gint pos = -1;
gtk_editable_insert_text (GTK_EDITABLE (entry), "some text", -1, &pos);
```

If you were going to dereference the pointer in your code, it would be * not &, but that most likely won't actually work since it's a pointer to a stack-allocated local variable that goes away when the function returns.

Also note that gtk_entry_append_text is deprecated, and even if it weren't, it still couldn't take a single char instead of a nul-terminated string. Since gtk_editable_insert_text has a length parameter, you might be able to pass &c for the string, and 1 for the length, but it's really better to build a string (possibly using a GString), then add it all to the entry at once.

---

### Post by matmatmat on 2009-05-21
Thanks for the reply, I now have this:
```

#include <gtk/gtk.h>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <glib.h>

int len = 10;
void generate (GtkObject *object , gpointer user_data)
{
  gtk_entry_set_text(user_data, "");
  unsigned int iseed = (unsigned int)time(NULL);
  srand (iseed);
  int i = 0;
  char c;
  int length = len;
  GString pass; 
  while (i <= length){
      int n = rand() % 26;
      char c = (char)(n + 65);
      GString pass = pass + c;
      ++i;
  }
  gint pos = -1;
  gtk_editable_insert_text (GTK_EDITABLE (user_data), pass, -1, &pos);

}


void num_changed (GtkObject *spin, gpointer user_data){
        len = gtk_spin_button_get_value_as_int (spin);
        len = len - 1;
}

void destroy_event (GtkObject *object, gpointer user_data)
{
    gtk_main_quit ();
}
 
int main (int argc, char *argv[])
{
GtkBuilder      *builder;
GtkWidget       *window;
GtkWidget       *number;
GtkWidget       *entry;
gtk_init (&argc, &argv);
builder =gtk_builder_new ();
gtk_builder_add_from_file (builder, "guipasswrdgenerator.xml", NULL);
window = GTK_WIDGET (gtk_builder_get_object (builder, "window1"));
entry = GTK_WIDGET (gtk_builder_get_object(builder, "entry"));
gtk_builder_connect_signals (builder, entry);
g_object_unref (G_OBJECT (builder));
        
    gtk_widget_show (window);                
    gtk_main ();
 
    return 0;
}

```
when I try to compile:
```

matio@matio-desktop:~/Documents/c$ gcc -Wall -g -o guipasswrdgenerator guipasswrdgenerator.c `pkg-config --cflags --libs gtk+-2.0` -export-dynamic
guipasswrdgenerator.c: In function ‘generate’:
guipasswrdgenerator.c:20: error: invalid operands to binary + (have ‘GString’ and ‘int’)
guipasswrdgenerator.c:24: error: incompatible type for argument 2 of ‘gtk_editable_insert_text’
guipasswrdgenerator.c:14: warning: unused variable ‘c’
guipasswrdgenerator.c: In function ‘num_changed’:
guipasswrdgenerator.c:30: warning: passing argument 1 of ‘gtk_spin_button_get_value_as_int’ from incompatible pointer type
guipasswrdgenerator.c: In function ‘main’:
guipasswrdgenerator.c:43: warning: unused variable ‘number’

```
which seems to mean that c isn't a char its a int (when printed it comes out as a letter) & that gtk_editable_insert_text won't take a GString? What do I need to do?

---

### Post by crdlb on 2009-05-21
This is C, not C++, so you can't expect magic like that to work. I think you should read some sort of C tutorial to get a refresher on pointers (and strings in particular).

A GString is used like this: ```

GString *textbuf = g_string_new (NULL); /* or g_string_sized_new */
g_string_append (textbuf, "ABC");
g_string_append_c (textbuf, 'D');
some_func_that_wants_a_char*_string (textbuf->str);
g_string_free (textbuf, TRUE);

```
A GString is similar to a StringBuilder in various higher-level languages.

Also, it's a very good idea to put ```
GtkWidget *entry = user_data;
``` as in my previous post for the type safety it provides if you use 'entry' from that point on (C will happily pass that gpointer (which is really a void*) as any pointer type).

---

### Post by matmatmat on 2009-05-22
Thanks, it works now!

---


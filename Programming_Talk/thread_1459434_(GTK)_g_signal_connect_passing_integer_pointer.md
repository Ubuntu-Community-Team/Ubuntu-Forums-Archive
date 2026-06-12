---
title: "(GTK) g_signal_connect: passing integer pointer"
date: 2010-04-21
forum: Programming Talk
---

### Post by agnes on 2010-04-21
How does one do that?

What I now have:

In main() :
```
int cs = 1;

g_signal_connect(case_sensitive, "clicked", G_CALLBACK(toggle_cs), (gpointer) cs);
```

and
```
void toggle_cs( GtkWidget *widget, gpointer cs) {
  
  if (gtk_toggle_button_get_active(GTK_TOGGLE_BUTTON(widget))) {
      g_print("Active\n");
      cs =(gint*) 1;	
  } else {
      g_print("Deactive\n");
      cs =(gint*) 0;
  }
  
  g_print("%s %d \n", "The value of cs is: ", (gint*)cs);

}

```

So cs is passed but I want the edited value of it to remain outside the scope of toggle_cs(..), so I want to make cs a pointer to an integer variable and then pass it. But I can't figure out how to do that in combination with the 'gpointer' cast.

---

### Post by MadCow108 on 2010-04-21
I have never used the C gtk signals but I guess it will work like this:

g_signal_connect(case_sensitive, "clicked", G_CALLBACK(toggle_cs), (gpointer) **&**cs);

inside the handler:
*cs = value;
if (*cs < 3435)
...

but you must make sure that the memory the pointer points to is always valid (maybe be doing a dynamic allocation with malloc)

---

### Post by agnes on 2010-04-21
Doesn't work... it says:
```
gtk2.c: In function 'toggle_cs':
gtk2.c:40: warning: dereferencing 'void *' pointer
gtk2.c:40: error: invalid use of void expression
```

I know gpointer is something like a void pointer... 
In g_signal_connect(..) I *must* pass a gpointer as a variable.
But don't know exactly what is gpointer and how to use it.

---

### Post by MadCow108 on 2010-04-21
you have to cast it to the correct type first
```

...(void * data) {
  gint* int_p = (gint *)data;
  // now you can dereference
  *int_p = 5;
}

```

gpointer will just be a typedef to a void or char pointer
you use void pointers in C to write generic functions by using a pointer with no type (=void)
like that you can write functions working on generic data when no or little information is needed on the type
the user is then supposed to recast the type to the pointer

a similar example for void pointer use is qsort which can work on any uniform continuous memory block, no matter what type of data is in it:
void qsort(void *base, size_t nmemb, size_t size, int(*compar)(const void *, const void *));
but in this case the algorithm needs some extra information, namely the size of one member in that memory block (so it can iterate over the elements by doing: base + nmemb * iterator)
in the compare function you again have to cast the pointers to proper type.

---

### Post by agnes on 2010-04-21
Got it :D

```
void toggle_cs( GtkWidget *widget, gpointer *cs) {
  
  if (gtk_toggle_button_get_active(GTK_TOGGLE_BUTTON(widget))) {
      g_print("Active\n");
      *cs = (gpointer)1;	
  } else {
      g_print("Deactive\n");
      *cs =  (gpointer)0;
  }
  
  g_print("%s %d \n", "The value of cs is: ", (int)*cs);

}
```

```
int cs = 1;
g_signal_connect(case_sensitive, "clicked", G_CALLBACK(toggle_cs), (gpointer) &cs);
```


Thanks for the push in the right direction.

edit: oh I didn't see your previous post when posting this. But yeah true, thnx again.

---

### Post by MadCow108 on 2010-04-21
you are doing the casts in the wrong direction.
do:
gint* i = (gint*)cs;
i = 1;
instead of
*cs = (gpointer)1;

your way only works with integers and may have portability issues

---

### Post by agnes on 2010-04-21
Ok.. yeah I edited it already looking at your earlier post.
Converting a character array to a gpointer first would probably indeed not work :)
but I guess you meant in your previous post
```
gint* i = (gint*)cs;
*i = 1;
```

---


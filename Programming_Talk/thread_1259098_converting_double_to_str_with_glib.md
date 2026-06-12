---
title: "converting double to str with glib"
date: 2009-09-05
forum: Programming Talk
---

### Post by swappo1 on 2009-09-05
Hello,
Here is the function I am having problems with.
```
static void counter(Widget *w)
{
	gchar *str = NULL;
	gint len = 100;
	static gdouble count = 1.0;
	
	g_ascii_dtostr(str, len, count);
	
	gtk_label_set_label(GTK_LABEL(w->label), str);
	g_free(str);
	count++;
	gtk_widget_show(w->label);
}
```
I can't get g_ascii_dtostr(str, len, count) to convert the count to a string so I can put the count in the label.  The program compiles fine.  Here is the output.
```
[hopchewer@hopchewer foundations_exercises]$ ./ex_6-2

(ex_6-2:10733): GLib-CRITICAL **: g_ascii_formatd: assertion `buffer != NULL' failed

(ex_6-2:10733): GLib-CRITICAL **: g_ascii_formatd: assertion `buffer != NULL' failed

(ex_6-2:10733): GLib-CRITICAL **: g_ascii_formatd: assertion `buffer != NULL' failed

(ex_6-2:10733): GLib-CRITICAL **: g_ascii_formatd: assertion `buffer != NULL' failed
[hopchewer@hopchewer foundations_exercises]$ 

```
Any ideas?

---

### Post by typedef on 2009-09-05
don't pass it a null buffer. it's not going to dynamically allocate it for you (it would likely take a gchar** and int* for length if it were going to do that anyway).

i.e., gchar *str = NULL; becomes gchar str[100];


P.S., don't free it either, unless you dynamically allocate it yourself.

---

### Post by swappo1 on 2009-09-05
If I change gchar *str = NULL; to gchar *str;, I get the following error.


```
ex_6-2.c: In function ‘counter’:
ex_6-2.c:67: warning: ‘str’ is used uninitialized in this function
make[1]: Leaving directory `/home/hopchewer/foundations_exercises'
[hopchewer@hopchewer foundations_exercises]$ 

```

---

### Post by PmDematagoda on 2009-09-06
> **swappo1 said:**
> If I change gchar *str = NULL; to gchar *str;, I get the following error.


```
ex_6-2.c: In function ‘counter’:
ex_6-2.c:67: warning: ‘str’ is used uninitialized in this function
make[1]: Leaving directory `/home/hopchewer/foundations_exercises'
[hopchewer@hopchewer foundations_exercises]$ 

```

Allocate some memory for it, you can't put data when a pointer isn't pointing at any allocated memory, you may get a segfault from that.

---

### Post by PmDematagoda on 2009-09-06
As a tip, use the documentation related to the functions, in your case for GLib, install the devhelp package and use that to refer the functions you use, that will let you know how to use the functions properly and more.

---

### Post by Linteg on 2009-09-06
It's also possible use g_strdup_printf or sprintf (with g_strdup... you won't have to allocate memory yourself).
```

double d = 1.0;
char *str = NULL;

str = g_strdup_printf("%f",d);
g_free(str);

```
Is there a reason why you are using a double in a counter? It will only ever have integer values so an (unsigned) integer would make more sense.

---


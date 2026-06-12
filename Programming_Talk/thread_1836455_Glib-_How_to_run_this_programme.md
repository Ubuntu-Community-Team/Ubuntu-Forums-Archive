---
title: "Glib- How to run this programme???"
date: 2011-08-31
forum: Programming Talk
---

### Post by Praveen30 on 2011-08-31
i am learning how to use glib with c language.And this is my first programme.i have installed libglib-dev from synaptic,it is under /usr/include/glib-2.0. but i don't know how to run it..?? help please!!

[PHP]
//compile.c
#include <glib.h>
int main(int argc, char** argv)
{
  GList* list=NULL;
  list = g_list_append(list,"Hello World!");
  printf("The first item is '%s'\n", g_list_first(list)->data);
  return 0;
}
[/PHP]

---

### Post by Smart Viking on 2011-08-31
Should include stdio.h.
```

//compile.c
#include <glib.h>
#include <stdio.h>
int main(int argc, char** argv)
{
  GList* list=NULL;
  list = g_list_append(list,"Hello World!");
  printf("The first item is %s\n", g_list_first(list)->data);
  return 0;
}


```
Compile with
```

$ gcc `pkg-config --cflags --libs glib-2.0` omg.c -o hello

```

---

### Post by Tony Flury on 2011-08-31
and run it with : 
```

./hello

```
Assuming you have not changed directory since you compiled it.

---

### Post by Praveen30 on 2011-08-31
> **Smart Viking said:**
> Should include stdio.h.
```

//compile.c
#include <glib.h>
#include <stdio.h>
int main(int argc, char** argv)
{
  GList* list=NULL;
  list = g_list_append(list,"Hello World!");
  printf("The first item is %s\n", g_list_first(list)->data);
  return 0;
}


```Compile with
```

$ gcc `pkg-config --cflags --libs glib-2.0` omg.c -o hello

```

I thought %s is fine here, but i am getting an error here-
compile.c: In function ‘main’:
compile.c:7: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘gpointer’
???

---

### Post by JupiterV2 on 2011-08-31
> **Praveen30 said:**
> I thought %s is fine here, but i am getting an error here-
compile.c: In function ‘main’:
compile.c:7: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘gpointer’
???

The warning is correct. Glib uses a generic pointer (void *) typedef'd as gpointer. This allows Glib containers like the g_list to contain any kind of data. You should always cast your store and your result to the proper pointer type to silence warnings. Glib also provides a set of macros to convert between basic types like: GINT_TO_POINTER and GPOINTER_TO_INT that cast the result for you. They may even implement simple tests to validate the data but I'm not sure on that.

---

### Post by Smart Viking on 2011-08-31
Are you doing exactly the same as me? It works fine for me.

If what you're doing it just a little different, that's obviously critical.

EDIT: Looks like JupiterV2 got the answers.

---

### Post by Bachstelze on 2011-08-31
> **Smart Viking said:**
> Are you doing exactly the same as me? It works fine for me.

If what you're doing it just a little different, that's obviously critical.

You never said which compiler/OS you were using. Don't assume everyone is running the same as you.

---

### Post by Smart Viking on 2011-08-31
> **Bachstelze said:**
> You never said which compiler/OS you were using. Don't assume everyone is running the same as you.
You're right, I shouln't. I'm probably using an older version of gcc, which doesn't have such a warning present. 
I'm using 64Bit gcc-4.4, on Debian.

---

### Post by Praveen30 on 2011-08-31
> **Bachstelze said:**
> You never said which compiler/OS you were using. Don't assume everyone is running the same as you.

Mine is gcc/Ubuntu-32bit.

---

### Post by Praveen30 on 2011-08-31
> **JupiterV2 said:**
> The warning is correct. Glib uses a generic pointer (void *) typedef'd as gpointer. This allows Glib containers like the g_list to contain any kind of data. You should always cast your store and your result to the proper pointer type to silence warnings. Glib also provides a set of macros to convert between basic types like: GINT_TO_POINTER and GPOINTER_TO_INT that cast the result for you. They may even implement simple tests to validate the data but I'm not sure on that.

thanks for your information but it is a little bit complex for me to understand right now..can you tell me how to cast it  so that i can run it properly???

---

### Post by JupiterV2 on 2011-08-31
Casts/Changes have been typed in bold.

```
#include <glib.h>
#include <stdio.h>
int main(int argc, char** argv)
{
  GList* list=NULL;
  list = g_list_append(list, **(gpointer)** "Hello World!");
  printf("The first item is %s\n", **(char *)** g_list_first(list)->data);
  return 0;
}
```

Also see: [glib-Type-Conversion-Macros]("http://developer.gnome.org/glib/2.28/glib-Type-Conversion-Macros.html")

---

### Post by Praveen30 on 2011-08-31
> **JupiterV2 said:**
> Casts/Changes have been typed in bold.

```
#include <glib.h>
#include <stdio.h>
int main(int argc, char** argv)
{
  GList* list=NULL;
  list = g_list_append(list, **(gpointer)** "Hello World!");
  printf("The first item is %s\n", **(char *)** g_list_first(list)->data);
  return 0;
}
```Also see: [glib-Type-Conversion-Macros]("http://developer.gnome.org/glib/2.28/glib-Type-Conversion-Macros.html")

thanks!!!

---


---
title: "C GTK+ Passing Data"
date: 2009-12-29
forum: Programming Talk
---

### Post by lewisforlife on 2009-12-29
I need help passing data in a GTK+ program with g_signal_connect.  Here is my example:
```

g_signal_connect (G_OBJECT (button), "clicked", G_CALLBACK (callback), (gpointer) "hello world");
```

Then I have the function callback:
```
static void callback( GtkWidget *widget,
                      gpointer   data )
{
    g_print ("%s", (gchar *) data);
}
```

This will print how "hello world" when the function callback is called.  Can I pass other types of data besides a string, such as numbers, arrays, etc...  I have tried passing other kinds of data, but get compilation errors when I pass anything else.  Are there any examples I can look at?

---

### Post by napsy on 2009-12-30
The data argument of your callback works as a generic pointer (gpointer is void *). So you can pass any type you wish. Just cast the pointer into the appropriate type before using it in the callback.

---

### Post by nvteighen on 2009-12-30
It's usually very good to use a data structure when you need to pass more than one thing. A (void **) array can be a mess to use if you want a generic array.

---

### Post by kahumba on 2009-12-30
I'm somewhat confused that your example works.
I think that the example wouldn't work if it was called inside a non-main function?
Because writing directly "hello world" would create it on the function's stack?

---

### Post by nvteighen on 2009-12-30
> **kahumba said:**
> I'm somewhat confused that your example works.
I think that the example wouldn't work if it was called inside a non-main function?
Because writing directly "hello world" would create it on the function's stack?

You're right. It wouldn't work.

---

### Post by lewisforlife on 2009-12-30
> **kahumba said:**
> I'm somewhat confused that your example works.
I think that the example wouldn't work if it was called inside a non-main function?
Because writing directly "hello world" would create it on the function's stack?

Actually, in my program on my computer, it is in the main function, I should have posted that, but I wanted to make my example as simple as possible.  I am wanting to pass an integer array, it is kind of working, but not all-the-way.  Here is what I have:

```
/* inside main function */
int iArray [2] = {2, 1}
g_signal_connect (G_OBJECT (eventbox_main, "button_press_event", G_CALLBACK (make_move), (gpointer) *iArray);
```

```
static void callback( GtkWidget *widget,
                      gpointer   data )
{
    g_print ("%d", (int) data);
}

```

This will output the number "2", How can I output the second slot in the array?  For instnance, if I try:

```
g_print ("%d", (int) data[1]);
```

I get: invalid use of void expression.

Thanks for your help.

---

### Post by nvteighen on 2009-12-30
> **lewisforlife said:**
> 
```
/* inside main function */
int iArray [2] = {2, 1};
g_signal_connect (G_OBJECT (eventbox_main, "button_press_event", G_CALLBACK (make_move), 
                  (gpointer) *iArray);
```

```
static void callback( GtkWidget *widget,
                      gpointer   data )
{
    g_print ("%d", (int) data);
}

```

This will output the number "2", How can I output the second slot in the array?  For instnance, if I try:

```
g_print ("%d", (int) data[1]);
```

I get: invalid use of void expression.


The issue is that your casting in wrong way. The following is the correct code:

```
/* inside main function */
int iArray [2] = {2, 1}
g_signal_connect (G_OBJECT (eventbox_main, "button_press_event", G_CALLBACK (make_move), 
                  **(gpointer) iArray**);
```

You don't need to cast to **(gpointer *)** because your dealing with a 1D array. gpointer is already a pointer, so it serves as (void *)... (gpointer *) = (void **)... i.e. a pointer-to-pointer.

Doing (int)data worked because of some pointer magic, but I'm sure (int)data[0] wouldn't have worked in your code as (int)data[1] didn't either.

---

### Post by lewisforlife on 2009-12-30
Ok, I think I figured it out, unless there is a better way of doing it.  But here is how I did it:

```
int iArray [2] = {2, 1}
g_signal_connect (G_OBJECT (eventbox_main, "button_press_event", G_CALLBACK (make_move), (gpointer) iArray);
```

After that, instead of trying g_print ("%d", data[number]) which didn't work, I created an int pointer like so:


```
static void callback( GtkWidget *widget,
                      gpointer   data )
{
   int *test = data;
   g_print ("%d, %d", test[0], test[1]);
}
```

---


---
title: "callbackfunction compiler warnings C++"
date: 2012-02-27
forum: Programming Talk
---

### Post by Hetepeperfan on 2012-02-27
I've got a callback function in my C++ program:

```
gboolean stopTask ( gpointer data )
{

    gtk_widget_destroy ( FullScreen );

    return FALSE;
}

```The compiler keeps warning me about the fact that I don't use the gpointer data variable. And I am don't see a reason to use it im my application. I know that FullScreen might not have been global and than it was wise to provide a pointer to Fullscreen, but this is not the case. I tried to keep the comiler quiet since I only want the warning in the following way but is this wise?

```
gboolean stopTask ( gpointer data )
{
    data = data; // we "used" data so no warning.
    gtk_widget_destroy ( FullScreen );

    return FALSE;
}

```any help is appreciated.

Maarten

---

### Post by nebukadnezzar on 2012-02-27
> **Hetepeperfan said:**
> 
```
gboolean stopTask ( gpointer data )
{
    data = data; // we "used" data so no warning.
    gtk_widget_destroy ( FullScreen );

    return FALSE;
}

```

You need to write it like this:

```
gboolean stopTask(gpointer data)
{
    (void)data;
    gtk_widget_destroy(FullScreen);
    return FALSE;
}

```

That approach *may* result in errors. But the sane, and frankly, most obvious way, is to simply not emit the variable name, when it's never used in this context:

```
gboolean stopTask(gpointer)
{
    gtk_widget_destroy(FullScreen);
    return FALSE;
}

```

---

### Post by Hetepeperfan on 2012-02-27
thanks nebukadnezza!

I'm going to try it tomorrow:-) I was going crazy about quite a few gtk callbacks where I just didn't see the point give the gpointer a name and the compiler kept "complaining" about unused variables. Which results in missing even more important warnings.

cheers!

---


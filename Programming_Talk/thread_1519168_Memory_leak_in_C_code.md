---
title: "Memory leak in C code"
date: 2010-06-27
forum: Programming Talk
---

### Post by geoffjay on 2010-06-27
My application uses the following function:

```

void
cld_ain_chan_add_raw_meas (AinChan *chan, gdouble value)
{
    GList *list = NULL;
    guint  conv;

    /* clip the input */
    value = (value <  0.0) ?  0.0 : value;
    value = (value > 10.0) ? 10.0 : value;
    /* convert to 16 bit int */
    conv = (guint)((value / 10.0) * 65535.0);

    chan->raw_meas_list = g_list_prepend (chan->raw_meas_list,
                                          GUINT_TO_POINTER (conv));
    /* keep the list size constant by removing the last element */
    if (g_list_length (chan->raw_meas_list) > chan->raw_meas_list_size)
    {
        list = g_list_last (chan->raw_meas_list);
        chan->raw_meas_list = g_list_remove_link (chan->raw_meas_list, list);
        g_list_free (list);
        list = NULL;
    }
}

```

In my program I'm using a GLib linked list to store data which is used to calculate a variable average based on user input. The purpose of this function is to maintain the size that the user has selected. This is possibly not the best way of achieving this and in the passed I have done so just using realloc but there's other parts of the application that made it better for me to keep things in a list.

Anyways, my app has a memory leak and I'm almost certain that this function is the culprit. Can anyone see something fundamentally incorrect about what I've done?

Output from Valgrind:

```

==6699== 2,640 (168 direct, 2,472 indirect) bytes in 7 blocks are definitely lost in loss record 9,696 of 9,837
==6699==    at 0x4C284A8: malloc (vg_replace_malloc.c:236)
==6699==    by 0x80E2214: g_malloc (in /lib/libglib-2.0.so.0.2509.0)
==6699==    by 0x80F7499: g_slice_alloc (in /lib/libglib-2.0.so.0.2509.0)
==6699==    by 0x80D6F8D: g_list_prepend (in /lib/libglib-2.0.so.0.2509.0)
==6699==    by 0x53CC12C: cld_ain_chan_add_raw_meas (cld.c:774)
==6699==    by 0x40DC52: ai_thread_func (threads.c:372)
==6699==    by 0x8102923: ??? (in /lib/libglib-2.0.so.0.2509.0)
==6699==    by 0x837F9C9: start_thread (pthread_create.c:300)
==6699==    by 0x867C6CC: clone (clone.S:112)

```

Thanks for any advice.

---

### Post by soltanis on 2010-06-27
I'm not really familiar with GLib linked lists. That being said, Valgrind is an excellent tool for detecting memory leaks, and I really suggest you install it and run your program under it.

---

### Post by geoffjay on 2010-06-27
Hello soltanis, thanks for the suggestion, you must have been typing that as I was editing my original post to include the valgrind output.

---

### Post by soltanis on 2010-06-27
g_list_prepend: adds something to the start of a linked list, I assume? What's the full documentation on this function? It sounds like what you're basically doing is forgetting a pointer, which causes memory never to be freed.

EDIT:
I looked up the documentation myself and here's what it says. Let me preface this by saying that I find nothing fundamentally wrong with your code logic so it might be something wrong with the way you're using the API.

> 
g_list_prepend ()
Adds a new element on to the start of the list.

Note

The return value is the new start of the list, which may have changed, so make sure you store the new value


I notice there is no clarification on what happens of the "new start of list" if it changes. It's quite possible that you need to hold on to the old value of the list, store the new value in a different variable, and then free the old list if it changes (that would be...very stupid). Otherwise, my other two guesses are 1. I missed some important detail in your code or 2. Glib has a memory leak (which would not surprise me).

---

### Post by slavik on 2010-06-27
I am wondering if that is how you are supposed to remove the last element.

---

### Post by geoffjay on 2010-06-28
slavik: I think you're right, I just had a look at the GList documentation and for g_list_delete_link it says

> 
Removes the node link_ from the list and frees it. Compare this to g_list_remove_link() which removes the node without freeing it.


I will try changing it and see if it helps.

soltanis: I agree, it would be strange to have to store the list as a temporary variable and copy back, especially since the examples frequently use the form *list = g_list_whatever (list)*. I know GLib has its own methods of dealing with memory that make it difficult to use valgrind, but hopefully memory leaks are not an issue as this is a pretty well defined library.

---

### Post by geoffjay on 2010-06-28
I gave *g_list_delete_link* a try and it crashes almost instantly, I also tried to free the reference returned by *g_list_remove_link* and that crashes just as fast. It looks like I might have to rewrite my program to use libgee as the LinkedList offered there has the function *gee_linked_list_poll_tail* that returns the tail of the list and removes it.

---

### Post by slavik on 2010-06-28
does it crash with a double free error?

---

### Post by geoffjay on 2010-06-28
I'm getting this back from gdb:

```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7fffebd3d710 (LWP 15797)]
0x00007ffff48ed0e4 in g_slice_alloc () from /lib/libglib-2.0.so.0
```

---

### Post by geoffjay on 2010-06-28
I got rid of the call to *g_list_free* after the delete and it stopped crashing but while I watch in htop the memory usage is still climbing so I'll have to run it in valgrind again to see if the same thing comes up as in the beginning.

---

### Post by vik_2010 on 2010-06-28
Instead of freeing the last node with Glib's functions, why don't you just use the usual functions provided by stdlib?

last = g_list_last(chan->raw_meas_list);
free(last);
last = g_list_last(chan->raw_meas_list);
last->next=null;



According to the documentation here:

[http://library.gnome.org/devel/glib/unstable/glib-Doubly-Linked-Lists.html#GList](http://library.gnome.org/devel/glib/unstable/glib-Doubly-Linked-Lists.html#GList)

every GList node has a pointer GList *next to the next element.

---

### Post by dwhitney67 on 2010-06-28
It seems that the following should work, but whether it does or not, I'll leave for you to investigate:
```

chan->raw_meas_list = g_list_delete_link(chan->raw_meas_list, g_list_last(chan->raw_meas_list));

```

---

### Post by geoffjay on 2010-06-29
dwhitney67: Is that any different than this?

```

list = g_list_last (chan->raw_meas_list);
if (list != NULL)
    chan->raw_meas_list = g_list_delete_link (chan->raw_meas_list, list);

```

The reason for me doing it that way is because g_list_last returns NULL if the list is empty, which is perhaps pointless because of the call to g_list_prepend right before it.

---

### Post by dwhitney67 on 2010-06-29
It is basically the same.  Who knows, maybe g_list_delete_link() checks internally if the given link is NULL, thus obviating the need for you to do it.

I've implemented (single and double) linked lists before; my code always checked to ensure the given data was sane; thus I can only assume Glib would do the same.  But you know what they say about "assume"...

---

### Post by geoffjay on 2010-06-30
I wrote a quick test using the changes that were suggested and it was leak free so I guess my problems are elsewhere. Thanks everyone for your help.

---

### Post by nvteighen on 2010-06-30
> **dwhitney67 said:**
> It is basically the same.  Who knows, maybe g_list_delete_link() checks internally if the given link is NULL, thus obviating the need for you to do it.

I've implemented (single and double) linked lists before; my code always checked to ensure the given data was sane; thus I can only assume Glib would do the same.  But you know what they say about "assume"...

I read the API docs... it's amazing how badly documented GList is...

---

### Post by geoffjay on 2010-06-30
Unfortunately I don't think anyone would need to look very hard to find out that that is the case with a lot of open source projects.

---

### Post by trent.josephsen on 2010-06-30
> **geoffjay said:**
> Unfortunately I don't think anyone would need to look very hard to find out that that is the case with a lot of open source projects.

It's true of many if not most proprietary projects as well.  In general, code is more prolific than documentation.

> Q:      How many hardware engineers does it take to change a light bulb?
A:      None.  We'll fix it in software.

Q:      How many system programmers does it take to change a light bulb?
A:      None.  The application can work around it.

Q:      How many software engineers does it take to change a light bulb?
A:      None.  We'll document it in the manual.

Q:      How many tech writers does it take to change a light bulb?
A:      None.  The user can figure it out.

---


---
title: "GtkWidget tutorial hunt."
date: 2005-08-16
forum: Programming Talk
---

### Post by TreeFrog on 2005-08-16
Hi,
I'm trying to use ajunta and my very rusty C knowledge to throw something together. 
I dont seem to be able to throw things together in C like in good old Delphi
I really never thought I would say this but I miss the whole Delphi thing. For simple RAD it was fun.

Now the widget I'm having fun  ](*,)  with is GtkTreeView. I want to use it as a list. very simple I'm sure.. 

Any Idea on where to find some more tutorials.. I have a collection of example code that just seems to make it worse for me!!

Thanks

Treefrog

---

### Post by André on 2005-08-17
Hi there,

what kind of list do you want excactly??

I programmed a bit here: [http://www.ubuntuforums.org/showthread.php?t=56953](http://www.ubuntuforums.org/showthread.php?t=56953)

It´s c# but i think you can configure it to your needs. 

And there is this google search thingy which gives me several tutorials ;-)

[http://liw.iki.fi/liw/texts/gtktreeview-tutorial.html](http://liw.iki.fi/liw/texts/gtktreeview-tutorial.html)

[http://scentric.net/tutorial/treeview-tutorial.html](http://scentric.net/tutorial/treeview-tutorial.html)

The second one is a very in depth view. Boh depend on C or C++ AFAIK (didn´t read through the first one right now).

Greetings and i hope it helps
André

---

### Post by André on 2005-08-17
Hi again,

for programming with gtk in a more visual way you should take a look at the nice glade which you can find here: [http://glade.gnome.org/](http://glade.gnome.org/)

Hope it helps
André

---

### Post by TreeFrog on 2005-08-17
Thanks Andre,  (sorry I cant find the accent for the "e" yet.)

That C# looks interesting. I will have to take a closer look sometime.

Other Links are the ones I have already looked at.. the first is in relation to Python and second is still too heavy for me. I cant see how to rewire the example code for my needs either.

To be clear of what I'm doing it is like this.
I have:
     [I]GtkWidget * entry = lookup_widget(GTK_WIDGET(button), "Data_entry");
     GtkWidget * list     = lookup_widget(GTK_WIDGET(button), "AppList_treeview");[/I]

I want to populate *AppList_treeview* with data from *Data_entry*.

Ultimatly I will find a way to parse data from a file and use that to populate *AppList_treeview*

The GUI tool I'm using is Glade with anjuta.

Treefrog.

---

### Post by André on 2005-08-17
Hi,

i think what you need is a File I/O tutorial like this one: [http://www.cpp-home.com/FileIO_tutorial.php](http://www.cpp-home.com/FileIO_tutorial.php)

creating a treeView should work like the stuff in my code

and finally you should add rows to this list like here: [http://scentric.net/tutorial/sec-treemodel-add-rows.html](http://scentric.net/tutorial/sec-treemodel-add-rows.html)

Yes, it's the scentric again but it's the most informative source for this one i think...

BTW, i am just starting with gtk also and i really would like to see your program when you finished. Could you post a message here and i give you my email adress per PM or could you upload your code when you are done?? I would be really interested.

Greetings
André

P.S.: If you still have questions and i am able to help with them i really like to. So please (!) ask ;-)

---

### Post by André on 2005-08-17
Me again ;-)

If you ever want to try Mono or C# let me know.

I think they are really nice and i have some links for it.

Greetings
André

---


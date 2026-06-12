---
title: "Gedit Style Creator Thing - My First C GUI prog"
date: 2008-04-07
forum: Programming Talk
---

### Post by mike_g on 2008-04-07
Heres my first creation with Gtk. Its nothing amazing, and its not completely finished yet, but College starts tomorrow and I got a load of other stuff to do so will have to put this on hold for a while.

Basically its a gui interface for creating gedit xml styles. You can colour configurations from the side panel, and pressing the save button writes it to a file called 'output.xml'. I want it to show the alteraions in the right panel (WYSIWYG style), but havent got around to it yet. The other buttos dont do anything either.

I attached the source files, its not big; about 300 lines in all. If anyone has suggestions o critisism on how it can be made better, or even wants to add somethng to it would be nice t hear from you.

To compile it  with gcc you will need the Gtk+ development libs. Then just type:
```
gcc Main.c `pkg-config gtk+-2.0 --cflags --libs` -Wall
```

Oh and I treid to make it so that it fits in nicely on my eeepc screen ;)
[Screenshot](http://i92.photobucket.com/albums/l15/mikegrundel/screendump.png)

---

### Post by tamoneya on 2008-04-07
The source files did not get correctly attached.  Seems pretty cool though I would like to test it out.

---

### Post by mike_g on 2008-04-07
Sorry, heres the files. Had to rename them as .txt o_O

---

### Post by lunisneko on 2008-09-14
I took a lot of inspiration for your style editor, so I made my own written in python. This little thing never would have been without your code as a starting point, not to mention replicating some of the great ideas you had. I also use libglade features to make it even a little easier. I would have added the functionality you were talking about in C, but I'm not so good at it, and I can't seem to stop using Python. So, thanks to you, I'd like to present PyGtkSourceViewStyleEdit, or pyStyleEdit for short.

[http://ubuntuforums.org/showthread.php?t=930369](http://ubuntuforums.org/showthread.php?t=930369)

---

### Post by mike_g on 2008-09-15
Cool, its nice to know hear that my code was of use to someone. I cant test your prog atm as I havent got a python interpreter on this machine, but I'll check it out later. Tbh I wanted to convert it to python myself, but havent got around to learning the language yet. If you havent already done so, you could adapt it to a gedit plugin: [http://live.gnome.org/Gedit/PythonPluginHowTo](http://live.gnome.org/Gedit/PythonPluginHowTo)

Cheers.

---

### Post by nvteighen on 2008-09-15
I get a compiler warning at Main.c:98. A mismatching pointer type.

But anyway, it's great!

---

### Post by 23dornot23d on 2012-02-27
Same .... as above

> 
keith@keith-Aspire-7730ZG:~/Downloads$ gcc Main.c `pkg-config gtk+-2.0 --cflags --libs` -Wall
Main.c: In function &#8216;setup_sample_text&#8217;:
Main.c:98:2: warning: passing argument 1 of &#8216;gtk_text_view_set_editable&#8217; from incompatible pointer type [enabled by default]
/usr/include/gtk-2.0/gtk/gtktextview.h:337:18: note: expected &#8216;struct GtkTextView *&#8217; but argument is of type &#8216;struct GtkWidget *&#8217;
Main.c: In function &#8216;main&#8217;:
Main.c:140:13: warning: &#8216;text_buffer&#8217; is used uninitialized in this function [-Wuninitialized]
keith@keith-Aspire-7730ZG:~/Downloads$ 



But created the editor ....

[IMG]http://img846.imageshack.us/img846/9486/editsp.jpg[/IMG]

---


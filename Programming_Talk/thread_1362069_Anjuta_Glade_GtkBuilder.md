---
title: "Anjuta Glade GtkBuilder"
date: 2009-12-22
forum: Programming Talk
---

### Post by Milliways on 2009-12-22
I have been trying to create a Glade project in Anjuta from Project/C/GTK+

The resultant project compiles, but when I Execute I get the following eror messages

(myworld:29180): libglade-WARNING **: could not find glade file 'src/myworld.glade'

Changing the following line fixes the problem.
#define GLADE_FILE "src/myworld.glade"

Now that I have some experience with glade I realise this would seem to be a bug in Anjuta.

My other attempts to use Glade (from makefile) used GtkBuilder.

Is there any way to get Anjuta to use GtkBuilder?

---


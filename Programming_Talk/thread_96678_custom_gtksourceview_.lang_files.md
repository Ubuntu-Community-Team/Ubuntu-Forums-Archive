---
title: "custom gtksourceview .lang files"
date: 2005-11-29
forum: Programming Talk
---

### Post by red_Marvin on 2005-11-29
Does anyone have any info on how to create and install gtksourceview files, so
they show up in the syntax coloring options in gedit?
Obviously saving a modified .lang file in /usr/share/gtksourceview-1.0 isn't enough
and I couldn't find any usable info on the gtksourceview's sourceforge homeage,
...but that doesn't mean the knowledge doesn't exist? *crossing fingers*

---

### Post by benletib on 2006-05-17
Up !

It interests me too :)
I'm tryinng to make an apache-conf lang file...

---

### Post by llonesmiz on 2006-05-17
I've slightly modified the file python.lang and saved it as mypython.lang and now I can select MyPython in gedit. I'm using gtksourceview 1.6 in dapper. The directory where I have saved the file is /usr/share/gtksourceview-1.0/language-specs/. When you modify the file, make sure that you change the line:

<language _name="Python" version="1.0" _section="Scripts" mimetypes="text/x-python;application/x-python">


to something like:

<language _name="MyPython" version="1.0" _section="Scripts" mimetypes="text/x-python;application/x-python">

It's possible that this won't work in breezy, I can't test it, I wish you good luck.

---

### Post by benletib on 2006-05-18
Thanks :)

But I found why it didn't work before. I made a mistake in my xml code so it wasn't valid and it wasn't displayed in the menu... :roll:

Finally, it isn't so hard to add a lang file !

---

### Post by red_Marvin on 2006-05-19
I managed to do that too.. anyone know how to write a *proper* file?
AFIK it's an xml file but I don't know xml (other than trial and error modifications)
Any resources/tutorials that a newbie can check?

---

### Post by vasdee on 2006-05-21
This is something i'm very interesting in as well. I'd like to edit the php.lang file to get rid of the annoying 'green' highlighting when you have embedded html within php.

One thing i've managed to find is that you can put custom lang files in
```
~/.gnome2/gtksourceview-1.0/language-specs/
```

and these will override the ones in /usr/share/....

---


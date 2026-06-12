---
title: "am I missing something here?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by GreenFire08 on 2008-06-25
Okay so in all my researching on how I can use "the shell," I constantly come across mention of things called "pipes." What these "pipes" can do would be very useful. However - how in the world does one get them? How do you enter a pipe into the shell itself? I know it's not an upper case I nor is is a lower case l. I seriously am beginning to think I'm retarded or something because I see no possible way for these "pipes" to exist, and nothing will tell me! Please help...I am so confused... :confused:

---

### Post by avtolle on 2008-06-25
On my keyboard, the pipe symbol, a vertical line, is the shifted \ key, located next to the ] key (to the right).

---

### Post by GreenFire08 on 2008-06-25
|

Now I do feel retarded...:lolflag:

Dude thanks so much I was starting to have a panic attack.

---

### Post by avtolle on 2008-06-25
No problem; we all started somewhere, right? :-) 

BTW, if you would kindly mark this thread "solved" using the thread tools, it will save others time. TIA.

---

### Post by ShodanjoDM on 2008-06-25
The "pipe" command is doing exactly like its name: piping the output of one command to the next. The "|" symbol (located right above enter button in my keyboard or shift+\ ) is pipe.

I'll give an example. Suppose I want to list the content of my Wallpapers folder but only want to limit the output of the files that has "me" in their names. This is how I do it:

```
ls | grep me
```

and the results:

```
# ls | grep me
co2metal-1160343866.jpg
Gnome
meiji_taisho_wallpaper_by_alxboss.jpg
metal-stripes-graphite.png
metal-stripes.png
metal-stripes-warm.png
metrotunnels_1280x960.jpg
overtime_1280x960.jpg
phenomenon_by_aiRaGe.jpg
```

---

### Post by Sinkingships7 on 2008-06-25
That damn pipe always made me mad, too. On the keyboard, it looks like a broken pipe, so I was never able to find it.

---


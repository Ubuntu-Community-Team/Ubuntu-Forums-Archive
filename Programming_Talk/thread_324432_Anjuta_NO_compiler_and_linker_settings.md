---
title: "Anjuta: NO compiler and linker settings"
date: 2006-12-23
forum: Programming Talk
---

### Post by Biased turkey on 2006-12-23
[SIZE="3"]In the settins menu, I don't have any submenu  "compiler and linker settings"
I need that options because I need to link to the SDL libraries.
Is it a bug with Anjuta ?
I didn't have that problem with Ubuntu 6.06 ? should I downgrade to Ubuntu 6.06 ?
Tia for any help

[/SIZE]

---

### Post by gannon on 2006-12-28
I just went to use it again after upgrading and noticed this too.

---

### Post by Wybiral on 2006-12-29
If you have to use the command line until you figure it out, just use "g++ program.cpp -lSDL"

You can also use -lSDL_image -lGLU -lGL depending on whether you need opengl or the image library.

I wish I could be of more  help with the IDE thing, I'm more of a command line guy... But, you can always use the command line until you figure it out.

---

### Post by badactress on 2006-12-29
hi,

You've just upgraded to 6.10 I guess? The Edgy developers made the insane decision to have Anjuta 2 in the Edgy repositories, which is pretty much un-usable for any kind of programming. It looks like it could be great in the future but at the moment it's lacking in nearly all the features you need.

This thread tells you how to install Anjuta 1.2.4a which is far more complete & usable.

[http://www.ubuntuforums.org/showthread.php?t=288480&highlight=anjuta+1+on+edgy]("http://www.ubuntuforums.org/showthread.php?t=288480&highlight=anjuta+1+on+edgy")

Hope this helps!
Norm

---


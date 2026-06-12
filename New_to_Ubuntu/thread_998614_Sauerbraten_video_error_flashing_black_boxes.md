---
title: "Sauerbraten video error: flashing black boxes"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by DavidVS on 2008-12-01
Hello!

I just installed Sauerbraten.  Something is funny.  The game runs, but the screen is interrupted by flashing boxes, mostly black rectangles.

What might I be doing wrong?

My computer is an Acer Extensa 4620Z laptop.

Thank you for any help.

---

### Post by NewJack on 2008-12-01
Let's start with:

What video card are you using?  
Have you had this problem with other games/programs?  
What are the game's video settings?  
Do you have a screensaver enabled? (This one got me once)

---

### Post by DavidVS on 2008-12-01
The laptop has an Intel GMA X3100 graphics card.

Google tells me this [should run 3d games, but poorly]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.notebookreview.com%2Fdefault.asp%3FnewsID%3D4154&ei=oYgzSY3UNZnMsAOmgrn9CA&usg=AFQjCNGSX9FE-iVMjXlQyEWsLx6yFCDY9g&sig2=gp76JkKR7M6qSJFm_nWmOQ") for modern games.

No screen saver.

Adjusting the video settings didn't help at all.

This was my first attempt at using an FPS.  To answer your other question, I downloaded OpenArena which loads but does not even display its menu screen properly.

I am fairly new to Ubuntu and have no idea how to ask the system to display my video card properties or test OpenGL.

Hm.  Wikipedia [tells me]("http://en.wikipedia.org/wiki/Intel_GMA") the graphics card has [no GLSL support]("http://en.wikipedia.org/wiki/GLSL").

Anything I can do?

---

### Post by NewJack on 2008-12-01
Do you have Compiz running?  You may have to turn that off when you want to play Sauerbraten.  Also, another workaround is to turn down the graphics of the game under Video Options.  If you are running the graphics on High, try turning it down to Medium or Low.

It appears that the card you have may be a bit underpowered.

---

### Post by DavidVS on 2008-12-01
I can try turning off Compiz.

The "System Monitor" lists three processes:
[LIST]
[*]compiz
[*]compiz-decorator
[*]compiz.real
[/LIST]

Are there any others that are related, which I should terminate before trying a 3D game?

---

### Post by NewJack on 2008-12-02
I apologize for not getting back to you sooner (Was stuck working overtime).  Anyway, I found this thread in the Gaming & Leisure Forum here:

[http://ubuntuforums.org/showthread.php?t=999506&highlight=compiz](http://ubuntuforums.org/showthread.php?t=999506&highlight=compiz)

Maybe you can contact the OP of that thread and see if he had any success with the script that was suggested to him.

I am fortunate that I haven't had issues like this yet so I can't recommend a script personally.

Hope this helped!

---

### Post by DavidVS on 2009-03-23
I'm still unable to do 3D games.

I've found and installed "CompizConfig Settings Manager" but cannot see where it allows me to turn of Compiz.  Does it?

What else can I do?

If I could play GuildWars I'd be happier.  :-)

---


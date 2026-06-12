---
title: "vlc doesn't show films"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by Germamon on 2014-01-24
Hi.

i've just installed lubuntu yesterday..so still quite new.

Well.. when i am going to play a film in gnomeM player or vlc i can not play the film, the screen freeze and i can only move the mouse, and nothing else..

Does anyone what happens?

cheers.

x

---

### Post by Bashing-om on 2014-01-24
Germamon: Hi ! My welcome to the forum.

When you installed, did you check the box (at the initial install stage) for installing 3rd party software ?

If not one can install the required codecs:
Terminal code:
```

sudo apt-get install lubuntu-restricted-extras

```

Install that package, try VLC, and advise on results.

Cheers;
[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by Germamon on 2014-01-24
Hi Bashing-On!

first of all, thanks for replying!

I didn't install lubuntu in my computer, a friend of mine did, so don't know if he installed the 3rd party software.

Anyway I installed the package as u said and I can not play VLC yet. It goes for three seconds and then I have to restart the computer... :S
more ideas?

---

### Post by Bashing-om on 2014-01-24
Germamon; Ummph,

That was the one shot I had, I do not use VLC, thus not able to relate.

Await others who have the experience with VLC to advise on what to do next.

[INDENT][INDENT]if I knew evertyhing
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Germamon on 2014-01-24
ok Bashing-on.

thanks for your help anyway!

i hope others will write something about it! :)

at least you know some tips about ubuntu!

---

### Post by sandyd on 2014-01-24
In VLC, try going to
Tools -> Preferences 

Set show settings to "All"

Under video, click on output modules.
Switch it to OpenGL, and see if it works.
If it doesn't try some of the other output modules

---

### Post by Germamon on 2014-01-24
nice one sandyd! 

it works perfect now! with OpenGL. :)

thanks a lot!

how can i write in  the forum that the problem is solved??

I mean, an icon in the threat

---

### Post by Germamon on 2014-01-24
ok, i have done it :)

---


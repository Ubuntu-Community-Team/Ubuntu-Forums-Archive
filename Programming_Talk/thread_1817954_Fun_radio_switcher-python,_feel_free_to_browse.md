---
title: "Fun radio switcher-python, feel free to browse"
date: 2011-08-04
forum: Programming Talk
---

### Post by flyingsliverfin on 2011-08-04
Hey all I just wanted to get opinions on a little python program i wrote. This is a category of programming that i really enjoy... making mundane tasks  simpler/more fun, automizing stuff etc.

Context: my family listens to online radios from around the world. We usually have french or german ones (we're from there). not too long ago my brother found one called 'NRJ' (nrj.fr), a french one, and it has about 30 of its own radio stations by type of music. I thought it would be cool to have an automatic switcher for them, and at the same time eliminate all the extra mouseclicks used to go to firefox -> radio. Thats how i got to this :)

Some things I kind of want to fix/add are the need to hit enter once before getting back to the improvised prompt.
Also later i looked it up and realized i could have used Popen and stuff but this works for me and i know how to use regular bash well.

NOTE: you need VLC for it to work

---

### Post by jerrrys on 2011-08-04
thanks; don't know when i get a chance to play with this, but sounds like a winner

---

### Post by flyingsliverfin on 2011-08-05
updated it a bit (attached)...
its interesting that cvlc returns its info on sterr not stout

also by sending the vlc info to /dev/null it fixed my need to hit enter to get back to the prompt. It looks a lot cleaner now :)
also fixed some errors

---

### Post by ziekfiguur on 2011-08-06
I haven't tried it yet, but from looking at the code i noticed a few things.
If you use [PHP]proc = subprocess.Popen(['cvlc', tmp], stderr=open('/dev/null'))[/PHP] instead of os.system, you don't need to spawn another shell between python an cvlc, and you can use proc.terminate() to stop cvlc (or proc.kill() which would be like kill -9)
[QUOTE=python library documentation 16.1 on os.system()]The subprocess module provides more powerful facilities for spawning new processes and retrieving their results; using that module is preferable to using this function.[/QUOTE]

Another thing, maybe it would be nice to import readline, and maybe use it make a command history, so it remembers what the user listened to last time.

---

### Post by mendhak on 2011-08-07
I think you should put this on github. :)

---

### Post by flyingsliverfin on 2011-08-07
thanks!
Ill think about it :)

Any1 know if this will run on OSX?
what about if i change it to use what ziekfiguur recommended? would it work on windows then as well?

---


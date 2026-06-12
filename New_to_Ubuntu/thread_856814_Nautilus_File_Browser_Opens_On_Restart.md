---
title: "Nautilus File Browser Opens On Restart"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by rainserpent on 2008-07-11
Hello fellow 'buntu users,

Does anyone know why my Nautilus Home folder opens up every time I restart the OS? I don't have anything checked in sessions manager as far as I know. It is kind of a minor irritation since I don't shut down my laptop that often, yet I don't remember it happening with Gutsy.

Check with you later,
Paul

---

### Post by drs305 on 2008-07-11
If you don't have nautilus listed in Sessions > StartUp, it could be that it is listed in ~/.gconfd/saved_state. This file remembers running apps and starts them again the next time the session starts if the user has requested it. It's not the easiest file to read but you could try renaming it and restarting to see if nautilus might be 'buried' in there.

Not likely, but you could also see if it ended up in the /etc/init.d folder by some chance. It it is there, try looking in the various rcX.d folders to see if it is being asked to run in one of those. It would have a title of SXXnautilus or something like that with the XX being a 2-digit number.

---

### Post by rainserpent on 2008-07-11
I am getting this error on restart:

Jul 11 21:01:11 Computer kernel: [  611.959128] nautilus[5530]: segfault at a6000020 eip b76ca2d6 esp bfd81070 error 4

Maybe this has something to do with it? I looked at the saved_state file and that thing is a nightmare. Nothing in /etc/init.d with any nautilus names.

---

### Post by drs305 on 2008-07-11
> **rainserpent said:**
> Maybe this has something to do with it? I looked at the saved_state file and that thing is a nightmare. 

That's why I suggested renaming it ;-)

As far as the seg fault, I can't offer anything but will look around.

---

### Post by rainserpent on 2008-07-16
Hey DRS,

I renamed that file, but it did not help.I'm sure I did something wrong in order for that thing to pop up. Please...make it stop!

Paul

---

### Post by rainserpent on 2009-07-31
I forgot how this was able to get fixed. Maybe it worked itself out.

---


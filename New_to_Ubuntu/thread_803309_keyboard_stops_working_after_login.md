---
title: "keyboard stops working after login"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by scarab on 2008-05-22
since two days ago, after my login, my keyboard simply stops working - even keys as NumLock do not have any effect.
this happens ONLY to my main user: I created a new user and keyboard works perfectly.....
did not alter any configuration ultimately, as far as I know... 

It works perfectly if I login after <ctrl>+<Alt>+F1, but only in the black screen....

how to begin to solve this problem? I am using Kubuntu 8.04

thanks in advance

---

### Post by shifty_powers on 2008-05-22
go into the new user, press alt-f2 and type gksudo nautilus and press enter.

navigate to the home folder of the orignal user and press control-h

find the ./comfig folder, **make a copy of it to the home folder of the user you are logged in as**, then delete it. (The copy is in case you need to restore it).

log out and then back in as the original user. it will regenerate your ./config and hopefully your keybaord will work ;)

---

### Post by scarab on 2008-05-22
could not do so: I am under KDE... tried to sudo konqueror and not possible (by some strange reason, my current user is not recognized by sudo).... tried via <ctrl>+<alt>+F1 and could not find a ./config folder in the main user home.... is there another name for that in kde?

thanks lots!

---

### Post by scarab on 2008-05-22
found a .config folder (not ./config) but could not copy it using cp: it was ommited.... another command to copy a folder?

cheers

---

### Post by shifty_powers on 2008-05-22
heh, assuming you are running 8.04, iirc the command would be:

```
gksudo dolphin
```

---

### Post by scarab on 2008-05-22
gksudo dolphin: "could not run the specified command"

tried sudo konqueror and nothing happens (nor the message)

---

### Post by scarab on 2008-05-22
did copy to another location, then removed .config

restarted the computer (had already tried restarting user...) and all is the same: no keyboard under my main user..... what more to try?

thanks in advance;

---

### Post by ethanay on 2008-05-24
hello,

perhaps you are suffering from [accessibility features](http://www.uluga.ubuntuforums.org/showpost.php?p=5030577&postcount=3) :)

i was :)  damn near had a heart-attack before i found out what it really was

go system > preferences > keyboard > accessibility
turn off "slow keys" function
turn off the ability to enable accessibility from the keyboard
breath a sigh of relief (hopefully!!)
click on the link to the bug report from the link above
tell developers to add better notification so we know when we've activated features such as this

---

### Post by scarab on 2008-05-24
Thanks lots!

I guess that was my problem.... however, I had a more radical solution (before reading you, of course) that worked too: just deleted the .kde folder... loosed all my user desktop configuration, but, in reality, there wasn't so many specific and important things there, and it worked!
cheers

---

### Post by philinux on 2008-05-24
> **scarab said:**
> gksudo dolphin: "could not run the specified command"

tried sudo konqueror and nothing happens (nor the message)

If you need that in future its kdsu not gksudo

---


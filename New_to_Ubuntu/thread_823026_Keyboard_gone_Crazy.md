---
title: "Keyboard gone Crazy?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by spe05081 on 2008-06-08
My keyboard mysteriously stopped working correctly.  I can login just fine, but once logged in, only some keys work and mostly do not correspond to their correct mapping.

I do not know what could have caused the problem (the last thing I remember doing was to change the repositories to the US ones because the Canadian repo were not working, after that I updated).

-Keyboard: Apple Aluminum Keyboard (wired) - works fine outside of Ubuntu, and works fine before logging in
-Keyboard Type: US layout
-Latest Ubuntu build

Thanks for any help!
P.S. Keep in mind I cannot type commands, or type my password to access places

---

### Post by jombeewoof on 2008-06-08
alright, this shouldn't be too hard.
Load up a livecd and mount your / or /home partition. Wherever your user account lives. Probably going to be automounted somewhere like /media/disk1.

whatever.
Do this

Change default language for the console: 
Edit /home/USERNAME/.bash_profile 
Add the line
```

 export LANG=en

```

this will allow you to login and it's probably something in xorg.conf setting your keyboard to a differnt country. I'm not really sure where that setting lives, but this will let you login to a console and figure it out.

when you can login and get a working keyboard map
run
```

sudo dpkg-reconfigure console-setup

```

---

### Post by spe05081 on 2008-06-08
Actually, I was just about to reinstall Ubuntu and found that this behaviour is 100% repeatable with an Apple aluminum keyboard.  Did some more searching  and found out it is a bug:
[http://ubuntuforums.org/showthread.php?t=815242&highlight=apple+aluminum+keyboard](http://ubuntuforums.org/showthread.php?t=815242&highlight=apple+aluminum+keyboard)

The trick is to press F6 twice.

---


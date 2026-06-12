---
title: "enable permission change"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by golgo13 on 2008-06-20
I want to do something really simple like change one of the icons but I am told - 
you are not the owner you cannot change these permissions  !?
how can I do this i.e. enable root

---

### Post by sharks on 2008-06-20
type in terminal sudo su and type the password and change the icon using root.

---

### Post by the_doc on 2008-06-20
From the command line:

```
sudo chmod [options] mode file1
```

will change permissions as root.

---

### Post by hyper_ch on 2008-06-20
have a read here about sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by argail1980 on 2008-06-20
open a terminal

(menu) Applications > Accesoires > Terminal
and type ```
sudo bash
```
then you have a root shell.

to open a file browser with root permissions type 
```
gksu nautilus
```

---

### Post by golgo13 on 2008-06-20
I don't understand it I followed the instructions and ran as SU
changed the icon image through the location and it still did not change in the place I wanted it too... :(

---

### Post by hyper_ch on 2008-06-20
what do you want to do?

---

### Post by argail1980 on 2008-06-23
Funny, after questions like "what do you want exactly?" and similar, you don't hear from most people anymore...

---

### Post by golgo13 on 2008-06-27
so you do hear back from me :)
I want to change one of my icons...
Oh dear I double posted anyway...
[http://ubuntuforums.org/showthread.php?t=842536](http://ubuntuforums.org/showthread.php?t=842536)
(slap on the wrist)
I love linux but I want to change icons etc easily
i.e. you can do this with windows with your eyes shut but when in linux you have to 2x post (yes thats me admin) and still its not sorted
BTW I am not a total noob as I have prob spent 50 plus hours on ubuntu just configuring etc but still don't get this ](*,)

---


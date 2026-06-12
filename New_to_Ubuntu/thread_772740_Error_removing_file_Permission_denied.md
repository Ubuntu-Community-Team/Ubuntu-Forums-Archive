---
title: "Error removing file: Permission denied"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by nutpants on 2008-04-28
Error removing file: Permission denied
in my trash can

i know what it is and im sure i sent it there as a user.

but i cant get it out and i cant delete it

and i cant find it as a super user. (sudo nautilus)

so how do i get rid of it>?

once again.. its in my TRASH CAN....
nutz

---

### Post by Michael.Godawski on 2008-04-28
If you want to delete files from your trash run this in terminal:
```

sudo rm -rf ~/.Trash/*
```

---

### Post by dokdoom on 2008-04-28
You were able to send it to the trash but you can't empty it now? Please explain further.

---

### Post by starcannon on 2008-04-28
If your using Ubuntu 8.04 Hardy Heron then the trash is located here:

/home/yourhome/.local/share/Trash

If your using Gutsy I believe your trash will be located here:

/home/yourhome/.Trash

if you use the terminal or sudo nautilus you should be able to rm items using super user.

GL.

---

### Post by nutpants on 2008-04-28
> **Michael.Godawski said:**
> If you want to delete files from your trash run this in terminal:
```

sudo rm -rf ~/.Trash/*
```

it is still there.
i think that deleted everything from the root users trash


> You were able to send it to the trash but you can't empty it now? Please explain further. 

i just did a fresh install of ubuntu 8.04
and had been messing with synce and quake 2  (separately)
and had a bunch of stuff in the directory i was untaring and make and building stuff in and i moved a bunch to my trash as i sorted what i had to keep and what i did not.

that was yesterday
today i noticed i still have a directory in trash called "synce-gnome-0.11" 
and the permissions all look fine on it
but i cant delete it out of my trash
i KNOW it was one of the directory i sorted INTO the trash yesterday

the main directory is in my user name the sub directory's are root

i get the error
Sorry, couldn't change the permissions of "synce-gnome-0.11": Operation not supported by backend
and i cant find it to delete it as super user

> If your using Ubuntu 8.04 Hardy Heron then the trash is located here:

/home/yourhome/.local/share/Trash

that worked thanks.

nutz

---


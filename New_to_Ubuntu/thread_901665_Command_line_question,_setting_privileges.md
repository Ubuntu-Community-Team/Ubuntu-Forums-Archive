---
title: "Command line question, setting privileges"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by burtzacarach on 2008-08-26
Hi, thanks for opening this thread. What I'm trying to do is move the contents of one folder to another, but I guess when you set up your first user account on ubuntu you aren't given administrator privileges so this can't be done using the file manager.
what command line input can i use to move files?
I know how to navigate between folders and make directories, but that's about the extent of it.
and/or how can i just set permissions for my user account so i can simply cut and paste?

---

### Post by ibuclaw on 2008-08-26
To move files or directories, use the "**mv**" command.

ie:
```
mv oldfile newfile
```
Moves oldfile to newfile.
You can specify directories also.
```
mv oldfile newfolder/newfile
```
etc.

What permissions are you wishing to set on your files?
Anyhow you use the "chmod" and "chown" commands.

You can look their usage up by using "**man**"
```
man chmod
```
```
man chown
```

Regards
Iain

---

### Post by halitech on 2008-08-26
> **burtzacarach said:**
> Hi, thanks for opening this thread. What I'm trying to do is move the contents of one folder to another, but I guess when you set up your first user account on ubuntu you aren't given administrator privileges so this can't be done using the file manager.
what command line input can i use to move files?
you do but you don't have admin rights. in order to do things outside your home folder you need to temporarily become root

> I know how to navigate between folders and make directories, but that's about the extent of it.
and/or how can i just set permissions for my user account so i can simply cut and paste?

you can open Nautilus as root
```
gksu nautilus
```
 or you can do it from the command line
to move it:

sudo mv /path/to/where/file/is /path/to/where/you/want/file

or to copy it:

sudo cp /path/to/where/file/is /path/to/where/you/want/file

---

### Post by -Zeus- on 2008-08-26
am i incorrect in thinking that "sudo nautilus" will be the same as "gksu nautilus"?

EDIT: oops now i realize the difference :)

---

### Post by halitech on 2008-08-26
> **-Zeus- said:**
> am i incorrect in thinking that "sudo nautilus" will be the same as "gksu nautilus"?

EDIT: oops now i realize the difference :)

they are basically the same but the way it was explained to me was, if you are working solely in the terminal, use sudo but if you want to open a graphical app, use gksu as using sudo can cause issues with X. I used sudo for the first while that I was using Ubuntu and didn't see any adverse affects but now I make sure I use the correct option :)

---


---
title: "[SOLVED] How to get to administrator login screen?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Tim Silver on 2008-07-11
Hi,

I'm using Ubuntu 8.04

I'm trying to delete a couple of directories. I've tried through a terminal. rmdir says I can't delete it 'cause there are files in it  and I can't cd to it as 'the file or directory doesn't exist'! - and this is as a super user.

OK, I thought I'll switch user, login as root and achieve this the GUI way (I know I've done it before) only to be told that 'The system administrator is not allowed to login from this screen'.

How do I get to the system administrator login screen?

---

### Post by forger on 2008-07-11
try: sudo rm -r folder-name/

---

### Post by dracayr on 2008-07-11
you can't login as root in ubuntu. use 

gksudo nautilus

dracayr

---

### Post by DGortze380 on 2008-07-11
> **Tim Silver said:**
> Hi,

I'm using Ubuntu 8.04

I'm trying to delete a couple of directories. I've tried through a terminal. rmdir says I can't delete it 'cause there are files in it  and I can't cd to it as 'the file or directory doesn't exist'! - and this is as a super user.

OK, I thought I'll switch user, login as root and achieve this the GUI way (I know I've done it before) only to be told that 'The system administrator is not allowed to login from this screen'.

How do I get to the system administrator login screen?

You need to remove it recursively (ie. remove the folder and all it's contents).

```

sudo rm -rf /directory

```

BE CAREFUL WITH THIS COMMAND AS IT WILL FORCE ANYTHING IN THAT DIRECTORY AND BELOW TO BE REMOVED WITHOUT ASKING FOR CONFIRMATION!

---

### Post by Tim Silver on 2008-07-11
Not working chaps!

I went to the terminal, changed to root and navigated to /opt - that's where the directory I want to delete is. Typed
```
rm -rf /google-earth
```
and pressed enter. Checked using 'ls' and it's still there! What now? What about rmdir?

---

### Post by Tim Silver on 2008-07-11
forger! I forgot your post! That did it, thanks

---

### Post by forger on 2008-07-11
mind you, /google-earth is not google-earth/ :)
/google-earth = look for folder or file "google-earth" in root "/" partition (mount point).

google-earth/ = look for folder in the current directory ;)

---


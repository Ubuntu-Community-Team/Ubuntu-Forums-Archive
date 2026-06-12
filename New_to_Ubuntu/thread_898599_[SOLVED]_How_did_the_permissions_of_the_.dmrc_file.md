---
title: "[SOLVED] How did the permissions of the .dmrc file change?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by bhadotia on 2008-08-23
I just copied the contents of my home folder (including the hidden files) to a read-only partition (which I make writable only when I want to do that) which I use as my back-up partition and restarted. At that login screen the first peculiar thing I find is that my login picture is not present.  And when I login I receive a message that the .dmrc file is ignored, this prevents my default session from being loaded and that it (the file) has to be owned by me and it should have 644 permissions. And then when I login I'm put into  xfce rather than gnome which is my default session (I have to manually select gnome to log into it).

What does this message mean, why does this happen (such things have happened earlier also), and how can I solve and avoid it?

Many thanks for any help.

---

### Post by jpkotta on 2008-08-23
Change the permissions with
```
chown $USER:$USER ~/.dmrc
chmod 644 ~/.dmrc
```

I don't know why the error occurs, but I've seen it before too.  I'll be there is a bug report for it and possibly an explanation.

Looking at mine right now, it's read only:
```
$ ls -l ~/.dmrc 
-rw------- 1 jpkotta jpkotta 27 2008-04-20 16:29 /home/jpkotta/.dmrc

```
I don't use gdm, I use kdm, so it doesn't affect me.

---

### Post by bhadotia on 2008-08-25
> **jpkotta said:**
> Change the permissions with
```
chown $USER:$USER ~/.dmrc
chmod 644 ~/.dmrc
```I don't know why the error occurs, but I've seen it before too.  I'll be there is a bug report for it and possibly an explanation.

Looking at mine right now, it's read only:
```
$ ls -l ~/.dmrc 
-rw------- 1 jpkotta jpkotta 27 2008-04-20 16:29 /home/jpkotta/.dmrc

```I don't use gdm, I use kdm, so it doesn't affect me.
This is still not working for me. I'm sill getting the same error and my login pic still does not show up at login screen. The output of the last command for me is:
```
-rw-r--r-- 1 abhishek abhishek 26 2008-08-23 21:44 /home/abhishek/.dmrc

```

Also, I forgot to mention above that the error message also says that my home directory should be owned by  and not writable by others.

---

### Post by bhadotia on 2008-08-25
I found the indication to the solution on this [site. ]("http://www.linuxquestions.org/questions/ubuntu-63/cant-log-in-users-home.dmrc-file-is-being-ignored....-478089/")
Particularly, this is the method I adopted (and that worked):
First, I backed up the contents of my .dmrc file and deleted it. Then, recreated that file and:
```
 chmod 644 /home/abhishek/.dmrc
```
and then:
```
chmod 755 /home/abhishek
```
where 'abhishek' is my username.
I ran that last command because the error also indicated that there might be some problems with the permissions of the home directory.

Now don't ask me which of the above (two permission changing)steps actually did the work because I did not log out and log back in to check :)

Well at-least the permissions of my .dmrc file are in place (they match with that of jpkotta):
```
abhishek@name-is-gnu:~$ ls -l /home/abhishek/.dmrc 
-rw------- 1 abhishek abhishek 26 2008-08-25 20:00 /home/abhishek/.dmrc
```

---


---
title: "Command to delete root-directory?"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Bubba3 on 2012-05-01
I need the command to delete a directory owned by root. I tried sudo rmdir, but it says: directory is not empty. I guess Linux is not as cruel as to make me delete every single file. Help pls :)

---

### Post by mcduck on 2012-05-01
> **Bubba3 said:**
> I need the command to delete a directory owned by root. I tried sudo rmdir, but it says: directory is not empty. I guess Linux is not as cruel as to make me delete every single file. Help pls :)

*rm -R* deletes directories recursively, and can be used to remove directories with files inside them. *rm* alone only works on empty directories.

---

### Post by dolphin194 on 2012-05-01
The *rmdir* command does not remove a directory with files inside it, only empty directories.

You need to use the *rm* command to delete the file, and you must provide the parameter *-rf*.
If you want to delete a folder along with all subfolders and files inside the directory, use the following command:
```
rm -rf [DIRECTORY]
```

---

### Post by r-senior on 2012-05-01
Note that for the rm command -R is the same as -r.

Always be careful with rm -r, especially when used in conjunction with sudo -- once they are gone, they are gone.

---

### Post by Bubba3 on 2012-05-01
Thanks for your quick help guys, worked :)

---

### Post by forrestcupp on 2012-05-01
What you are asking is extremely dangerous. You'd better make sure you know completely what you're doing before you delete any directory owned by root. There was a time when we were threatened to be banned for telling people how to do what you want to do.

---

### Post by anewguy on 2012-05-01
I would hesitate to do anything until you post back what you are deleting and where it is located.  When you start using remove tools, especially on something owned by root, it is very important to know what it is, what's under it, etc., before you do a tree delete.

So, going just by your bean count alone (which, if you saw mine and the questions I ask you'd know don't mean anything) I *assume* you are new to Ubuntu.  If so, it's even more important we know what you want to delete before you do so.  If you do this in an incorrect way, depending on the location in the file system, you can render your system unusable until a reinstall.

So, let's *first* find out what you want to delete and why, *then* move on to the tools.  If this weren't something owned by root it wouldn't matter as that would probably be things in a user folder.

Dave ;)

---

### Post by Cheesemill on 2012-05-01
> **anewguy said:**
> I would hesitate to do anything until you post back what you are deleting and where it is located.  When you start using remove tools, especially on something owned by root, it is very important to know what it is, what's under it, etc., before you do a tree delete.

So, going just by your bean count alone (which, if you saw mine and the questions I ask you'd know don't mean anything) I *assume* you are new to Ubuntu.  If so, it's even more important we know what you want to delete before you do so.  If you do this in an incorrect way, depending on the location in the file system, you can render your system unusable until a reinstall.

So, let's *first* find out what you want to delete and why, *then* move on to the tools.  If this weren't something owned by root it wouldn't matter as that would probably be things in a user folder.

Dave ;)

+1

There should be absolutely no need for you to delete anything owned by root, in fact doing so will probably break your system.

What exactly are your reasons for doing so?

---


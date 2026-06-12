---
title: "[SOLVED] terminal kills me"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by tonymoloney on 2008-09-15
I am trying to get into terminal on a Xubuntu system, but when I select terminal in the menu, I get logged out and the log-in screen comes up.
The reason I am trying to do this, is that I have just installed Puppy400 frugal on the system and I need to edit /boot/grub/menu.lst
If I try to edit menu.lst using a gui editor, I cannot save the file as I don't have superuser access so I need to go to terminal and sudo.
Shift/Ctrl/n doesn't help. It puts me to a cli prompt, asks for a user name and password and hangs.

---

### Post by tarps87 on 2008-09-15
I have had the problem with the terminal login me out, I don't know why it does but to solve it I install another shell. I don't remember which one tho.
Do you mean by Ctrl+Alt+F1?

---

### Post by t0p on 2008-09-15
Press **Alt+F2**, type 
```
gksudo thunar
```

into the Run box, and you can edit any file using mousepad.

**EDIT:** I *think* - I'm not running xubuntu right now so I can't check.  But I think it'll work...

---

### Post by tonymoloney on 2008-09-15
No. I tried Ctrl/Alt/F1 and nothing happened.

---

### Post by tonymoloney on 2008-09-15
tOp - your reply came whilst I was replying to the first one.
Question - If I can't get into terminal, how do I type gksudo thunar??

---

### Post by crazypenguin2008 on 2008-09-15
accidental post

---

### Post by t0p on 2008-09-15
> **tonymoloney said:**
> tOp - your reply came whilst I was replying to the first one.
Question - If I can't get into terminal, how do I type gksudo thunar??

What happens when you press Alt+F2?  Doesn't a Run box open?

---

### Post by tonymoloney on 2008-09-15
Whoa! Silly me!
Must learn to read all of the post before I make any comment.
Thanks tOp. Alt F2 did the trick.

---

### Post by t0p on 2008-09-15
You're welcome.

---


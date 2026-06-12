---
title: "How to remove desktop folder from desktop and the trash?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by aknisely on 2008-05-10
I accidentally put the desktop folder on my desktop. I sent it to the trash but I cant empty it. How do I get rid of both the folder on my desktop and in my trash?

---

### Post by redbob on 2008-05-10
Follow these steps. Open nautilus by gksu> gksu nautilus
So go to home folder and turn hidden items visible (Ctrl-h). When you open the trash, delete the file.

---

### Post by aknisely on 2008-05-10
I just tried that but when I navigate to the trash there is nothing in there.

---

### Post by aknisely on 2008-05-10
BTW, I do still have a desk top folder. What happened is I accidentally dragged the desktop folder to my desk top then tried to delete it. I also have one on by task bar I'd like to get rid of.

---

### Post by aknisely on 2008-05-10
Ok, I got the folder off the desk top but in the trash there are two desktop folders each with 506 desk top folders inside desktop folders. Sorry if this doesn't  make sense,

---

### Post by aknisely on 2008-05-10
anyone?

---

### Post by inportb on 2008-05-10
So you moved a folder into itself? (I'm not sure if that can be done.)

---

### Post by Ripfox on 2008-05-10
Ok lets try this from the beginning. It sounds like you just dragged and dropped a copy of your desktop folder out of your home folder to the desktop, then deleted it. Am I correct so far?

Edit: I just tried this and it wouldn't let me do it.

---

### Post by Ripfox on 2008-05-10
I know you are told never to rm -rf anything. But I will explain why I am telling you to do this. You seem not to have the proper permissions to empty the trash manually, I'm guessing b/c you are trying to delete a system folder. If I am wrong someone correct me. You CAN empty the trash from the terminal with this

> rm -rf ~/.Trash/*




Now, here is an article from Ubuntu Geek to back this up:

[http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html](http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html)

---

### Post by shifty_powers on 2008-05-10
gksudo nautilus

file system>home>user name>.local(might have to press control h here to show hidden files)>share>Trash>files

then highlight anything in there and move to deleted items folder.

click on deleted items in places on left hand side.

click on empty delete items and confirm.

hope that helps ;)

(sorted out an annoying problem with the trash for me :D)

---

### Post by aknisely on 2008-05-10
Thanks for your replies guys. I just went ahead and installed 8.04.:)

---

### Post by Ripfox on 2008-05-10
That'll work too :lolflag:

---


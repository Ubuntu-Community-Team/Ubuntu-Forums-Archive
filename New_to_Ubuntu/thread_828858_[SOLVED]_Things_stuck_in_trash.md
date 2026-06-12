---
title: "[SOLVED] Things stuck in trash"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by WonderStivi on 2008-06-14
Bear with me on this one.

I copied some folders from a CD to the desktop, as a temporary backup, and when I was done i put them in the trash like I always do. I discovered yesterday that they were still there, though I put them there a week ago. The folders aren't that big, but they sure do annoy me.

When I try to empy the trash, these folders just gets ignored, and no feedback is given to me as why they aren't removed. When I try to manually delete them from the trash, I get the message "Error removing file: Permission denied".

I tried to read up on how to removed them, and came over the command 'rm -rf ~/.Trash', but I don't think I've found the correct folder. I've also tried 'rm -rf /home/username/.Trash', only to discover that there's no folder by this name in my home directory.

I'd certainly appreciate some guidance on this problem. I've more or less given up on doing research because the search alternatives gives too many results.

In advance, thanks.

---

### Post by sdowney717 on 2008-06-14
try sudo in front
sudo rm -rf $HOME/.Trash

---

### Post by WonderStivi on 2008-06-14
Thanks for the quick reply.

I've tried that as well, with no change. Did the ctrl+alt+backspace after the command to refresh the desktop. Folders are still there (in the trash, that is).

---

### Post by sdowney717 on 2008-06-14
scott@scott-desktop:~$ sudo rm -rf /home/scott/.local/share/Trash/files

actually they are here
just sub your user name for scott

---

### Post by WonderStivi on 2008-06-14
Woot, thanks man :) Worked like a charm.

---

### Post by gandaran on 2008-06-14
don't use sudo rm -rf, it could be dangerous! just use **sudo rm** for a file removal or **sudo rm -r** for a folder removal.

---

### Post by T-Virus on 2008-06-14
Yeah, there is al ot of talk here about force removing but people still do that.

---

### Post by WonderStivi on 2008-06-14
Duly noted. However, I'm glad it worked. I have read some about not using -rf, and checked with several sources before doing it. Hopefully, I won't be using these commands at all.

---

### Post by jmap82 on 2008-06-14
I've had this problem a couple times too.  What works for me, and its a nice gui way to do things, is to delete them in a su-nautilus session.

In the terminal type:

```
sudo nautilus
```

This will open a super-user file browser just like the one you are used to in regular browsing.  It will start you in the "home" folder for the "root" user.  Select "Show Hidden Files" from the "View" menu in the "Menu Bar".  Now just navigate to the location sdowney717 mentioned "/home/USER/.local/share/Trash/files" and that should show you the contents of your "Trash Can".  From there just select and delete.

"sudo nautilus", while dangerous, has helped me take care of things a number of times as "Beginner", because the "rm -rf" command is still a bit scary for me, and I like the visual feedback :).

Hope that helps!

---

### Post by sdowney717 on 2008-06-14
The sudo is for terminal commands, use gksudo when opening a gui interface. This is usually not an issue, but might be.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by davidshere on 2008-07-23
Thanks for the "~/.local/share/Trash/files" tip.   Question: Why is my trash there instead of in "~/.Trash"?

Yet another question: why didn't I find this directory when I typed "locate Trash"?

---


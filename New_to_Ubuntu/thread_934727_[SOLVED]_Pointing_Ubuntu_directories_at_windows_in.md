---
title: "[SOLVED] Pointing Ubuntu directories at windows install"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by dinostabOMG on 2008-09-30
So, I'm dual booting, and I want to share most of my files between OS installs. I have a My Documents folder in my Windows XP install, and I can already get at it by going to /media/disk/Documents and Settings/Administrator/My Documents/ . That's kind of a hassle. What I would really like to do is have ~/Documents point at /disk/Documents and Settings/Administrator/My Documents/ because right now, the Ubuntu Documents folder is going unused, and the Windows one is a pain to get to. The same goes for pointing ~/Videos to the Windows My Videos folder, and music, downloads, etc.

I have created a launcher on my Ubuntu desktop to the Windows desktop folder, but this is not an adequate solution in most cases. For example, when I go to upload an image through firefox that happens to be in my windows install - you would think that in the "open file" dialogue, double clicking on the launcher would navigate to the appropriate folder, but no! Instead it tries to open the launcher file itself, which is a pretty useless behavior.

Is there a way to link one director to another, in an inextricable symbolic way - like how when you type ~ in terminal and press tab it will show the home folder? I'd like this kind of thing to happen with certain directories to point to my WinXP folders.

---

### Post by karlr42 on 2008-09-30
I think it's the ln command, have a read of  man ln

---

### Post by dinostabOMG on 2008-09-30
Perfect. Here's example code for the terminal:

```
ln "/media/disk/Documents and Settings/Administrator/My Documents/My Pictures" Pictures --symbolic 

```

You might have to delete the Pictures directory from the home folder in this case. You can move the files over to the windows one first.

---

### Post by karlr42 on 2008-09-30
Thanks for the example, will be useful for others coming across this thread.
Glad you achieved what you wanted!

---


---
title: "[SOLVED] Places shortcuts"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Polish Rifle on 2008-07-26
Here's the story:

I backed up all my files on an external hard drive and I installed Ubuntu.  Now I would like to put my files back on in an organized manner.  But when I tried to seperate my files amongst the places sub-folders, they don't have enough space.  

I tried to edit the places folders but I have no idea how to make shortcuts on a different partition for music/pictures/videos.  Simple question probably, but I'm having problems with it.  

What I would like:

When I hit the places menu for the music folder to come down and contain all my music in it.  Same for pictures, videos, and documents.

---

### Post by AndyCooll on 2008-07-26
Well I've created shortcuts in my home folder using the following command:
```
ln -s /mnt/share/music music
```
Previously I've created a mount point for my "share" folder, and mounte it. My "share" folder is on a server.

So now when I click on the "music" shortcut in my Home folder it displays my music folder which is on the server.

:cool:

---

### Post by Polish Rifle on 2008-07-26
I don't see that showing up in my places menu.  I would like the short cut under the pull down bar in places.

---

### Post by ktrnka on 2008-07-26
Open your "Home" folder and drag and drop the item or folder to the left side.

Here is a [screenshot]("http://unix.scs.wsu.edu/~ktrnka/Screenshot.gif").

---

### Post by Polish Rifle on 2008-07-26
That didn't work.  I took the music folder and dragged it into a new partition but it kept the same shortcut underneath the Places menu.

---

### Post by ktrnka on 2008-07-26
I'm not quite sure what exactly you're asking then. Could you please clarify?

---

### Post by ktrnka on 2008-07-26
Open "Home" and right-click remove that music link on the left side. Then open the new location of your music folder. Drag and drop the folder onto the left side. That should work.

---

### Post by Polish Rifle on 2008-07-28
> **ktrnka said:**
> Open "Home" and right-click remove that music link on the left side. Then open the new location of your music folder. Drag and drop the folder onto the left side. That should work.

Thanks, that was exactly what I was looking for.

---

### Post by ktrnka on 2008-07-28
Please mark this thread as "Solved"

Thanks

---


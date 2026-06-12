---
title: "ipod problems"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by cwrann on 2008-05-22
When I plug a new 160 gb ipod into my computer I can see the existing tracks and add tracks to it. I can even play tracks off of it, but when I eject the ipod it came out blank, no music, nothing on it. I can then replug it into the computer and see all the tracks again.

---

### Post by superprash2003 on 2008-05-22
which software are you using to add tracks?

---

### Post by cwrann on 2008-05-22
Rythymbox.

(thanks for the response)

---

### Post by bvanaerde on 2008-05-23
This thread might help you.
[Adding songs to an iPod with rhythmbox]("http://ubuntuforums.org/showthread.php?t=768201")

---

### Post by sayakb on 2008-05-23
Use Banshee. It has a similar interface to rhythmbox, but works flawlessly (so does Rhythmbox, methinks)..

---

### Post by BandD on 2008-05-23
The problem is that newer ipods have a 'protected' database.  Basically the ipod expects to see a certain hash key when it looks at the database.  The problem with 3rd party apps (anything other than itunes) is that they don't know about this new special hash, and so they don't re-create it after adding songs.  Then when you start up the ipod, it looks for the hash, doesn't find it, thinks it has cooties and refuses to touch the music that is indeed on the ipod and perfectly playable.

Apple says that this is supposed to make ipods more 'stable' or some such.

I think there are some tools out there for newer ipods.  You might have to update some libraries or use a different tool, like gtkpod.  Try googling "6th gen ipods and linux" or something similar, you should be able to find some info.

EDIT:

found a link with all the info you need  [http://www.downloadsquad.com/2008/03/18/enable-support-for-7th-gen-ipods-in-ubuntu/]("http://www.downloadsquad.com/2008/03/18/enable-support-for-7th-gen-ipods-in-ubuntu/")

---


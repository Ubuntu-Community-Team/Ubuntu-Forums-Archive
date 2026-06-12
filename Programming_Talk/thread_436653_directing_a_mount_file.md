---
title: "directing a mount file"
date: 2007-05-08
forum: Programming Talk
---

### Post by Sugi on 2007-05-08
This is probably really easy and in the wrong topic.  Sorry for both, if im correct.
I need to write an script or something to direct an mount file to a directory.

IE: "/home/funsack/mountrom0/" (mount iso, dur >.<) needs to mount to the directory of 
"/home/funsack/.wine/drive_c/Program Files/Diablo II-tweaked/Diablo II.exe", but instead it mounts to the directory of "/home/funsack/.wine/drive_c/Program Files/Diablo II-normal/Diablo II.exe"

soooo, i got two installed directories, it wants to boot to the normal one, but i want it to boot to the tweaked one.  i think it sounds easy enough.
I also have a little script going right now, i have diablo II booting in windows mode.
wine "/blah/blah/Diablo II.exe" -w

What should I do?

thanks in advance. ^_,^

---

### Post by kidders on 2007-05-09
Hi there,

Your post is a little tough to understand. Are you trying to mount a file (eg an ISO image), or maybe trying to bind a mounted filesystem to a second location?

Can you explain what you'd like to do one more time?

---

### Post by Sugi on 2007-05-10
I have "fun.iso" mounted to point "mountfolder/".  this is the oh kay part.  When I go into the mountfolder/ and click play fun.exe with wine.  It runs from folder by default "/.wine/drive_c/Program Files/Fun/fun.exe" but I want it to run from folder /.wine/drive_c/Program Files/Fun2/fun.exe"

List of files and such,
fun.iso
/mountfolder/
/Fun/
/Fun2/

Hope this better describes it.  Sorry for the confusion.

---

### Post by kidders on 2007-05-10
Hmm... so am I right in thinking you have symlinked mountfolder/ to /.wine/drive_c/Program Files/Fun/ ? If so, you could just create another symlink.

---

### Post by Sugi on 2007-05-10
how do i make symlink?  like the launcher file thingy???

---

### Post by kidders on 2007-05-11
The most convenient way is to use **ln**. For the link to be symbolic, you need to use **ln -s** (see **ln**'s man page).

---


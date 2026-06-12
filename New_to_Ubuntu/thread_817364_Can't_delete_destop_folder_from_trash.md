---
title: "Can't delete destop folder from trash"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Drakkor on 2008-06-03
Yeah, somehow, through my finger clicking too fast , I accidently deleted the desktop folder, I guess, even though I still have the icon in "Places",
anyways, there is one item ,the desktop folder in the trash and I can't empty the trash folder, I have moved other objects to the trash and they can get deleted,but not the desktop folder,  I get this box:

---

### Post by dracayr on 2008-06-03
for hardy, do:

cd ~/.local/share/Trash/files
rm -r Desktop

else

cd ~/.Trash

dracayr

---

### Post by forestpixie on 2008-06-03
Sure I read a thread a while back where this wasn't such a good idea - although I could be wrong.

Might be better to make sure you can get back in before you delete it or put it back in home

Edit - > I don't remember what I did, but things have changed since I booted the system some two minutes ago. My Trash is empty, thankfully, but a new problem has arrived.

Ubuntu is for some reason, detecting my home/username folder as the Desktop folder and all its contents are splashed across my desktop.  Also, the "username" folder entry you have in Nautilus' explorer pane is missing, and clicking on the desktop folder takes me there.
[http://ubuntuforums.org/showthread.php?t=581498](http://ubuntuforums.org/showthread.php?t=581498)

---

### Post by Drakkor on 2008-06-03
Hey, thanks dracayr , that did the trick, command line magic that I have to learn sometime, lol  :)

---


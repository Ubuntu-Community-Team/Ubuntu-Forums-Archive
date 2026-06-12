---
title: "gnome-xcf-thumbnailer does not generate thumbs in Nautilus"
date: 2015-01-23
forum: New to Ubuntu
---

### Post by jeroen9 on 2015-01-23
Hi,

I followed your instructions [in thread [http://ubuntuforums.org/showthread.php?t=2099853]](http://ubuntuforums.org/showthread.php?t=2099853]) but it does not work in Nemo. I get the following error if I call the script manually.

sudo xcf-thumb -s 48 /home/SomeFile.xcf /home/SomeFileT.png

composite composite: Unable to open file (() [No such file or directory].
convert failed

Can you pls help me?

---

### Post by oldos2er on 2015-01-23
I've moved your post to its own thread, where it's much more likely to be seen.

Please give us some info such as your Ubuntu version, and hardware specs.

Re:  **sudo xcf-thumb -s 48 /home/SomeFile.xcf /home/SomeFileT.png** "SomeFile" will need to be replaced with the actual file name; did you do that? Also "sudo" is unnecessary when working inside one's home folder. And the user account name, /home/user/, is missing.

---


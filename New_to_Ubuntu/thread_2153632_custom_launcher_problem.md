---
title: "custom launcher problem"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by amarumayo on 2013-06-11
Hi all.

Noob question.

I am trying to create a custom launcher that runs grive (Google Drive Syncer) inside a folder.  In the terminal I just switch to ~/google_drive then I run grive as 2 different steps. 

How can I get this to work with a launcher? ~/google_drive/grive doesn't work probably because it thinks I am referring to a file.  The error it gives is:

Failed to execute child process "~/google_drive/grive" (No such file or directory)

Any help would be greatly appreciated.

---

### Post by ajgreeny on 2013-06-11
If grive is the executable that is to be run in a terminal you can either do the launch with a shell script and point to that in the launcher, or you could try a custom complex command in the launcher of ```
gnome-terminal -x google_drive/grive
``` I'm not totally sure about that command but it's worth a try.

Come back again if no joy.

---


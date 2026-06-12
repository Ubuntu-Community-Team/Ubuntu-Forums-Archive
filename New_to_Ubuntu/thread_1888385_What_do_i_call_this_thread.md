---
title: "What do i call this thread??"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by James.A.Parnell on 2011-11-29
How can i change the location of this link (from where it is to /hdd#2/music)
* see attachment

---

### Post by Paqman on 2011-11-29
You'll need to copy all the files to the new location. The you could symlink /home/shroomy/Music to your new music folder. To do this click on the folder > Ctrl-Shift and drag to the other location (Opening two panes by hitting F3 can be handy for this).

Or if you want, you can just copy the files to the new location, and then bookmark that with Ctrl-D and it'll show up in the list on the left.

---

### Post by ajgreeny on 2011-11-29
You can, if you prefer, manually edit the hidden file in your home called **.gtk-bookmarks**, a plain text file with all your nautilus bookmarks and their paths listed.

---

### Post by Morbius1 on 2011-11-29
And yet a 3rd option is to "bind" one location to the other. For example, to do this temporarily:
```
sudo mount --bind /hdd#2/music /home/Music
```**NOTE: To undo the bind and restore the current contents of /home/Music:**
```
sudo umount /home/Music
```If you want this to happen permanently you would have to:

* Make sure /hdd#2 mounts automatically at boot by adding an appropriate line in /etc/fstab.
* Move everything you have in /home/Music to /hdd#2/music first.
* Then create an upstart job that will mount this automatically at boot: [http://ubuntuforums.org/showthread.php?p=10899012#post10899012](http://ubuntuforums.org/showthread.php?p=10899012#post10899012)


A bind has an advantage over a symlink if you ever contemplate sharing this directory with others using Samba. Samba cannot follow symlinks unless you do something that Samba considers a security issue but it has no problem with a bind.

---


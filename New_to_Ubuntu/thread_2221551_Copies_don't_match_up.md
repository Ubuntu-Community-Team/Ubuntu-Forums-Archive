---
title: "Copies don't match up"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by matthew31 on 2014-05-02
I've been backing up the contents of my home folder to an ext4 formatted external drive. Every time I copy my files they're usually larger on the local drive and sometimes they'll even have a small number of files and folders than the original unless I copy again and say to skip all duplicate file names.

Why is this? I seem mostly have this issue in KDE but it's happened in XFCE before as well.

---

### Post by ajgreeny on 2014-05-02
How are you backing up?  Which application or utility?  It sounds as if rsync or grsync would be worth trying if that is not already what you are using.

---

### Post by matthew31 on 2014-05-02
I'm just copying my files manually in Dolphin or Nemo.

I don't care about things like system preferences, just my pictures, movies, music and documents and things like that so I never bothered with anything fancy. I just wanna make sure my files aren't being damaged.

---

### Post by ajgreeny on 2014-05-03
Definitely a situation that would be better using rsync, or for a gui grsync.  It will speed up the backups and automatically only copy any files that have changed in any way, or new ones added since last backup.  If you have edited any files and try to back up your way by just copying them, those edits will not be copied across unless you choose to replace in the dialogue box that appears.

I have no idea why you are seeing fewer files in the backup than the source unless my above comment is implicated in some way, but then I have never simply copied files, other than just a very few when rsync is a bit over-complicated, so I don't really have any experience by which to judge.

---


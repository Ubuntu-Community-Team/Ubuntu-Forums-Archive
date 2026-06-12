---
title: "File management"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by jbcohen on 2013-07-17
I have just read a tutorial on how to use the file manager in Ubuntu and I have one additional question.  I have a kindle that I connect to the PC via a USB port I saw the icon for it appear in the navigation pane on the left side of the screen.  What has thrown me is two issues: first, how to navigate the folder structure in Ubuntu, I am used to thinking of the file structure as a tree from top down with the top level being the drive, how does Ubuntu do this?  When the kindle appears on the left pane of the file manager how then do I get into the kindle, I clicked on the kindle and got an odd array of folders, none of them from the kindle.  I bet  Iam thinking about this wrong.

---

### Post by mastablasta on 2013-07-17
"drives" are mount points in ubuntu. Ubuntu also handles it like so. if you installed just default you will have 

/ - (root) which is main partition
/home - kind of like my documents in windows and main user's folder
various other folder in root.

external removable devices get mounted under /media and it gets shown in file manager as separate drive/media

the files and folders you see are probably from kindle operating system.

Have you tried calibre that is ment for book management? unfortunatelly it's not in the repositories but i think there is a PPA for it. they also have binary isntall (you need to copy and paste command into temrinal): 
[http://calibre-ebook.com/](http://calibre-ebook.com/)

i also think kindle has it's own interface for book management. you could also use that to access files (if it has a linux version)

---

### Post by Cheesehead on 2013-07-17
> **jbcohen said:**
> When the kindle appears on the left pane of the file manager how then do I get into the kindle, I clicked on the kindle and got an odd array of folders, none of them from the kindle.  I bet  Iam thinking about this wrong.

Strange. I get the file tree that is on the Kindle.
What are some of these strange folders named?

---


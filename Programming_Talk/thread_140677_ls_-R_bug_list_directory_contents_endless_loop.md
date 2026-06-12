---
title: "ls -R bug? list directory contents endless loop"
date: 2006-03-06
forum: Programming Talk
---

### Post by zootreeves on 2006-03-06
I'm trying to index an ftp site, but when I use ls -R it produces an endless loop of directories, i think due to symlinking. You can try it:

#ftp ftp.brighton.ac.uk
#anonymous
#anon
#ls -R

Is there anyway to overcome this, is there anyway to only list real directories not symlinks?

---

### Post by hod139 on 2006-03-06
Who creates a symlink that points back to the current dir!!  I wouldn't consider this an ls -R bug, but a problem with the directory structure.  As far as I know, you can't  tell ls to ignore symlinks or give ls any sort of recursive depth info, it is all or none.

---

### Post by zootreeves on 2006-03-06
Well this is the only site i have ever seen where this happens, but i'm just wondering for the future, if there are other sites like this, because my ftp crawler gets bogged down for weeks trying to crawl it. So there is nothing i can do with ls to stop it showing symlinks?

---

### Post by hod139 on 2006-03-06
I know of no way to have ls recursively search while not following symlinks. I wonder if ftp.brighton.ac.uk set up that recursive symlink as a deterrent to crawlers ;)

---

### Post by engla on 2006-03-06
I think you need a smarter crawler.. since you crawl you should keep track of visited urls anyway..

As a sidenote, if you symlink /usr/share/X11/fonts/fonts to /usr/share/X11/fonts, funny stuff happens! (No, actually nothing fun happens. No error is given anywhere, but gnome apps take 25 secs extra to start)

---


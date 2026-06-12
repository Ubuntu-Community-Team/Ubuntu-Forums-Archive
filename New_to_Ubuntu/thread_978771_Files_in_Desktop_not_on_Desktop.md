---
title: "Files in /Desktop not on Desktop"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by scribbles on 2008-11-11
Firefox default downloads files to ~/Desktop and while the files are indeed in that folder they do not reside on my Desktop....what's that about?

Also along those lines, I'm tired of Firefox requiring me to download a PDF first then view it in Okular. Sometimes I just want to view it! When I went to Associations in Preferences I couldn't find an entry for PDF. What can I do to change this and where does Okular reside?

Thanks!

---

### Post by taurus on 2008-11-11
What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by B34ST1Y on 2008-11-11
that almost looks like you're redirecting downloads to ~/Downloads, which would essentially be /root/Downloads. 


Try ```
/home/(your username)/Desktop
```and see if it doesnt resolve your issue

---

### Post by skintythe1andonly on 2008-11-11
I was caught out by this before. Are you using KDE4? if so the files do not appear and the desktop by default. You have to add a Desktop folder viewer widget. I ended up switching back to Ubuntu in the end as this feature wasnt for me, but is handy if you keep track of multiple folders

See my old thread at

[http://ubuntuforums.org/showthread.php?t=895724]("http://ubuntuforums.org/showthread.php?t=895724")

---

### Post by shoot2kill on 2008-11-11
~/Desktop
is the same as 
/home/$USER/Desktop
isnt it ????

but yeah, whats the output of the above command that taurus did ?

---

### Post by scribbles on 2008-11-11
Skinty, yea that was it. Thanks!

---

### Post by Keen101 on 2008-11-11
If you really want to view pdf's in your browser, you can download adobe reader.

---


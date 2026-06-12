---
title: "Unknown undeletable folder"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by pumadeneruda on 2013-12-12
Hi!
A few days ago I found a strange folder in my users directory, file type inode, name lW3gIekR 3. Every time I tried to open it, my system jammed and I was forced to manually switch the computer off. I managed to move it to the trash bin but now every time I try to delete it or empty the trash my system gets stuck. :confused:
I am very new to Ubuntu, had it installed it on my laptop (a Lenovo G550) just a month ago after many frustrating years as a MS user! :evil:
I would appreciate it if someone out there could help me. :D:D
 Luigi

---

### Post by Impavidus on 2013-12-12
An inode is any object represented in the file system, normal files, directories, symlinks, even your hard disk. Most detailed information we can get from the terminal. Try running```
stat "filename"
```in the directory where it is located and post the results. It may tell us what kind of thing we're looking at.

By the way, the thing we usually try before hitting the power button when the system freezes is typing [alt+SysRq+REISUB](http://en.wikipedia.org/wiki/REISUB).

---

### Post by pumadeneruda on 2013-12-14
hi impavidus, first of all many thanks for showing me how to reboot system safely! :D
abt my unknown folder, i followed your instructions but the answer i get is: "cannot stat &#8216;lW3glekR 3&#8217;: No such file or directory". perhaps it's because i moved file to the trash (but cannot deleted nor restore it)?

---

### Post by whitesmith on 2013-12-14
If your system works with the file in the trash bin it patently can't be needed. The following works in Gnome; can't vouch for other DEs. In a terminal (Ctrl+Alt+T) enter this without the comment (#). Replace "login" with your own login name-```
# assume you don't own everything, since the symptoms are screwy
chown [login].[login] -R /home/[login]/.local/share/Trash
cd files
rm 'lW3gIekR 3'

```Let me know if this works on your system. BTW it would help to give us full system details.

---

### Post by Impavidus on 2013-12-14
Thank you @whitesmith, I had to look that one up.

Files you sent to trash can be found in the directory ~/.local/share/Trash/files/

---


---
title: "ls -la"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by jsshere on 2008-11-09
when you type ls -la in the terminal some of the files that are printed are

drwxr-xr-x  2 user user 4096 2008-10-28 19:26 Music
drwxr-xr-x  3 user user 4096 2008-11-07 13:15 .nautilus
drwxr-xr-x  2 user user 4096 2008-10-28 19:26 Pictures
-rw-r--r--  1 user user  586 2008-10-28 19:00 .profile
drwxr-xr-x  2 user user 4096 2008-10-28 19:26 Public
drwxr-xr-x  2 user user 4096 2008-10-28 19:27 .pulse
-rw-------  1 user user  256 2008-10-28 19:26 .pulse-cookie
-rw-r--r--  1 user user  218 2008-11-07 13:15 .recently-used.xbel
drwx------  2 user user 4096 2008-10-28 19:26 .ssh
drwxr-xr-x  2 user user 4096 2008-10-28 19:26 Templates
drwxr-xr-x  2 user user 4096 2008-10-28 19:26 Videos

what does the numbers 2,3,2,1,2 mean?

---

### Post by spiderbatdad on 2008-11-09
the number of links to the directory: [http://en.wikipedia.org/wiki/Ls](http://en.wikipedia.org/wiki/Ls)

---

### Post by malspa on 2008-11-09
[http://www.computerhope.com/unix/uls.htm](http://www.computerhope.com/unix/uls.htm)

"The amount of links or directories within the directory. The default amount of directories is going to always be 2 because of the . and .. directories."

And the default number for files must be "1."

---


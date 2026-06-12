---
title: "can't find directory: home/$USER/.local"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by prattman2 on 2012-08-31
Hi,

I'm trying to save a menu entry as instructed by this link: [http://www.kaibader.de/running-eagle-cad-6-2-on-ubuntu-12-04/#comment-200](http://www.kaibader.de/running-eagle-cad-6-2-on-ubuntu-12-04/#comment-200) (see bottom of post) to /home/$USER/.local/share/applications but I cannot find the directory. I can't even see as far as /.local. I'm running ubuntu 12.04.

I tried to mkdir in terminal which seemed to be accepted, but /.local still doesn't show up in the folder viewer.

Can anyone advise me on why this would not be showing up? I am also worried that my attempts to create the folders in terminal may have had a detrimental effect! I am very new to ubuntu/linux and don't really know what I'm doing...

Any help greatly appreciated!

---

### Post by steeldriver on 2012-08-31
Most GUI file managers hide dot files by default - try hitting Ctrl-h to unhide

Or use 
```
ls -a
```in the terminal

---

### Post by micahpage on 2012-08-31
.FILES are hidden files.
while in the directory hit:
Ctrl-h 
and it will display hidden files

EDIT: oh i didnt see he already answered it, lol I just saw the terminal code

---

### Post by prattman2 on 2012-08-31
Thanks to you both for that - I can now see the directories and have put the .desktop file in there.
Unfortunately when I go to Applications in Dash Home, it's still not showing up..!

Any ideas?

Edit: Just restarted computer and it is now showing in the Applications in Dash Home, but won't run!
I'll have a re-check the code I put in...

---

### Post by prattman2 on 2012-08-31
Found the problem - one of the file in the process I was following should have been made executable and it wasn't. Changed it to executable and is now working.

Thanks very much once again to micahpage and steel driver for your help.

---


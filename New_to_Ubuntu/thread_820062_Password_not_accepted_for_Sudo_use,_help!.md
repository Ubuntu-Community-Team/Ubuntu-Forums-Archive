---
title: "Password not accepted for Sudo use, help!"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by hypnos0630 on 2008-06-05
SOLVED  THANK U ALL!

I'm very new to ubuntu and linux, but I've opened terminals and attempted to edit my xorg.conf (/etc/X11/xorg.conf).
I am unable to do ANYTHING because when I attempt any command it asks me for my password, the one I use to login after booting ubuntu doesn't work.
I even looked up how to change the password going through booting in recovery mode and have tried both passwords, nothing is working.

I'm using ubuntu as installed through wubi, if that helps.  And my main desire is to do THIS; ([http://ubuntuforums.org/archive/index.php/t-679457.html](http://ubuntuforums.org/archive/index.php/t-679457.html))

I need to change my driver/video card so that it has an Option "monitor-TV" "TVOutput" since it doesn't by default.  All this so I can play movies on the television screen from my laptop...

Please help!  I'm very new to this, but I can follow directions well, I mostly need to find a way to change/locate my password to unlock the sudo function.

THANKS!!!

---

### Post by tamoneya on 2008-06-05
check to make sure you are in the admin group by typing in terminal:```
groups
```

---

### Post by lisati on 2008-06-05
Just a thought: when using sudo, the password isn't displayed while you're typing, but will be accepted if you are careful to type the correct one.

---

### Post by hypnos0630 on 2008-06-05
i just did what you said and it replied that i am in the admin group.
while experimenting since my post was put up i found how to change the password using sudo password root and tried it though it wasn't recommended, that worked.
i have a new password that is working, but it said UNIX password...does this put my pc in any danger from outside sources or did it simply change my password as intended.  and if so, does that mean i have to use the new password to log in to my ubuntu now?

thanks for the reply!

---

### Post by tamoneya on 2008-06-06
if you just did ```
sudo passwd root
```then your login password will be the same.  I am also going to agree with the statement about not being recommended.  You should almost never need to login as root.  EVerything hsould be done via sudo if possible.

---


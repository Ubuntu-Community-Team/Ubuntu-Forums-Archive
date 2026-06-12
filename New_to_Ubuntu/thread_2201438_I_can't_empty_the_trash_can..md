---
title: "I can't empty the trash can."
date: 2014-01-24
forum: New to Ubuntu
---

### Post by rasti2 on 2014-01-24
I noticed my disk space getting lower so I wanted to empty the trash but I got the error message : Error while getting peer-to-peer dbus connection: The name :1.79 was not provided by any .service files. The free disk space still stays the same after that. Is there a solution to this?

---

### Post by whitesmith on 2014-01-24
Try this```
cd ~/.local/share/Trash/files
ls -l
```If something is there, delete what you no longer need with the rm command. Note the** .** before local and the initial cap on **T**rash. My carbon-based RAM gives a 404 on the source of your error.

---

### Post by rasti2 on 2014-01-24
Thank you I will try that but just wanted to let you know that I used a Backtrack LiveDVD I had and it deleted it with no problems (I navigated to the Trash directory and deleted from there).

---

### Post by monkeybrain20122 on 2014-01-24
I can see absolutely no point for the trash can. It has to be the most useless and annoying feature of any desktop environment. If I want to delete something, I want it gone, not to be moved to another folder. It is probably a crappy design inherited from Windows' recycle bin.

If you are using Ubuntu or Ubuntu-gnome, open Nautilus, go to edit > Preferences > behaviour and check "include a command of permanently delete" or something like that so next time when you right click and delete things really get deleted. There is a popup warning when you delete so you don't have to worry about deleting stuffs by mistake (There are similar options in other DEs like lxde and kde if you use lubuntu or kubuntu)

---


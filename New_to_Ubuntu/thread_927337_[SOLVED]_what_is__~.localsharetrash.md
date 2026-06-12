---
title: "[SOLVED] what is  ~/.local/share/trash ?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-09-22
is this the actual trash?

the reason i want to know is because i was running a virus scan with clamav and i got this
```

tj@tj-laptop:~$ sudo clamscan -i -r /
//root/.local/share/Trash/files/games/quake4/q4base/pak004.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games/quake4/q4base/pak005.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games/quake4/q4base/pak012.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games/quake4/q4base/pak003.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games/quake4/q4base/pak007.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games/quake4/q4base/pak019.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games/quake4/q4base/pak011.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games/quake4/q4base/pak008.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games/quake4/q4base/pak006.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games.2/quake4/q4base/pak004.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games.2/quake4/q4base/pak005.pk4: Oversized.Zip FOUND
//root/.local/share/Trash/files/games.2/quake4/q4base/pak012.pk4: Oversized.Zip FOUND

```

now first off i thought i uninstalled Quake4 a long time ago because it woudn't run on my computer

secondly i thought this was the trash folder but my trash says its empty

and third why is this in root's trash directory but not in /home/tj/.local/share/trash ?

---

### Post by diablo75 on 2008-09-22
That is a seperate trash folder.  It is where things go when you delete stuff as the root user using the sudo command.

I would run:

```
sudo nautilus
```

in a terminal window, browse to that folder, and then empty it.  Use CTRL-H to reveal hidden folders so you can be sure to get it all out.  Just make sure you don't delete something important by accident.

---

### Post by aysiu on 2008-09-22
It should be ```
gksudo nautilus
``` not *sudo nautilus*

---

### Post by tjwoosta on 2008-09-22
ok awesome


just out of curiosity, how do i get to a root terminal?

i know i have done it before but i forget the command

---

### Post by tjwoosta on 2008-09-22
nevermind i figured it out


sudo -s

thanks for the help guys

---

### Post by aysiu on 2008-09-22
> **tjwoosta said:**
> nevermind i figured it out


sudo -s

thanks for the help guys
It actually should be ```
sudo -i
``` and not *sudo -s*

*sudo -i* gives you a root login with root's environment and *sudo -s* gives you a root login with a user environment.

Same problem with *sudo nautilus*. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---


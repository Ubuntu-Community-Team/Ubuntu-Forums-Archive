---
title: "grsync help"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by night116 on 2013-05-11
i am trying to backup my home directory to my 4tb usb hard drive using grsync and gnome-schedule.
i have made a session called backup in grsync to run as superuser and when i manually run the program it asks for the password and all works fine.
but i am trying to automate it with gnome-schedule, i have set it as recurrent on 23 45 each day, and in the command i have set it as
grsync -e backup
but nothing ever happens.
i also tried to set it up in crontab, but it didnt work either.
45 23 * * * sudo grsync -e backup
can some one please help.

---


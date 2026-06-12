---
title: "root commands in a script"
date: 2010-10-16
forum: Programming Talk
---

### Post by Jonny87 on 2010-10-16
Is there a way to get a script to run a graphical prompt for the sudo password when executing sudo level commands, so that a basic user can just double click the script and select run with out having to run it in a terminal?

I've tried putting gksu at the start of the command but unless I'm missing something, it doesn't seem to work with all commands.

---

### Post by cinohpa on 2010-10-17
Wait. What exactly are you trying to do? If the user has the root password, why should they have to type it in at all? Are people besides yourself going to use this script? Is it going to be in a location accessible to other people?

The reason why I am asking because I wonder if you should just have a cron job or a put it in a startup script or if this is a nice "button" you want to keep around in a central place for users who have the permission to run it but prevent users who shouldn't run it from doing so.

---

### Post by spjackson on 2010-10-17
> **Jonny87 said:**
> Is there a way to get a script to run a graphical prompt for the sudo password when executing sudo level commands, so that a basic user can just double click the script and select run with out having to run it in a terminal?

I've tried putting gksu at the start of the command but unless I'm missing something, it doesn't seem to work with all commands.
Does this recent thread help? [http://ubuntuforums.org/showthread.php?t=1596949](http://ubuntuforums.org/showthread.php?t=1596949)

Although it is about, python, the principles are similar.

---


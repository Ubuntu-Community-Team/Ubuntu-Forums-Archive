---
title: "Script to backup from XP to Ubuntu"
date: 2011-05-09
forum: Programming Talk
---

### Post by Jonny87 on 2011-05-09
My is running XP on her laptop and I'm trying to come up with a script that will copy the files of her laptop her own profile on my ubuntu desktop. Kinda as a backup. 

I'm thinking about using the likes of rsync to do the copying. What I need help with is the fact that she doesn't always have her laptop on while my desktop is on and I want to cron the script to run on a regular basis. I want to be sure that it won't have any unexpected issues if her laptop isn't on when it runs. 

Is any one able give me an example how i could do it?

I'm thinking bout maybe some sort of "if" during the mounting of her shared dir to be backed up. i.e if unable to mount don't continue etc...

---

### Post by Jonny87 on 2011-05-10
*Bump*
Can any on help me with this?

---

### Post by Jonny87 on 2011-05-11
Let me clarify a bit more.
I need help with an if statement in the script. I have the mounting of the XP share sorted all I need is for the script to first detect that her laptop is mounted in /media/share (incase the laptop isn't on to mount) and if its not mounted then to discontinue the script. otherwise if it is mounted to continue with the rsync command.

---


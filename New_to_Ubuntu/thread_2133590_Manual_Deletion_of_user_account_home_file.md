---
title: "Manual Deletion of user account home file"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by Gannas on 2013-04-08
Hi again all! Well since I'm very new at this I've made a blunder. I added then deleted a account to my server, but of course the /home directory for that user is still listed. How do I go about removing that /home directory for that deleted user.

Thank you!

---

### Post by mikewhatever on 2013-04-08
Use 'sudo delluser --remove-home username', or even 'sudo deluser --remove-all-files username'.

---

### Post by bab1 on 2013-04-08
To remove the directory you simply do this at the terminal prompt```

sudo rm -f /home/<directory_name_you_are_deleting>

```

This can be dangerous if you select the wrong directory to delete so be careful.   To see all the directories in /home you can use this command from the terminal```
ls -l /home
```

---

### Post by Gannas on 2013-04-09
Thank you for the response gang! But it doesn't seem to have worked. I think I should also say this is a fresh install of 12.04 and I'm using a ssh. Here's what I got when I put those commands.

gannas1@HS1920ESGW:~$ ls -l /home
total 12
drwxr-xr-x 2 eric    eric    4096 Apr  8 14:41 eric
drwxr-xr-x 4 gannas1 gannas1 4096 Apr  8 15:15 gannas1
drwxr-xr-x 2 eric    eric    4096 Apr  8 14:40 username
gannas1@HS1920ESGW:~$ sudo deluser --remove-home username
[sudo] password for gannas1:
/usr/sbin/deluser: The user `username' does not exist.
gannas1@HS1920ESGW:~$ sudo deluser --remove-all-files username
/usr/sbin/deluser: The user `username' does not exist.
gannas1@HS1920ESGW:~$ sudo re -f /home/username
sudo: re: command not found
gannas1@HS1920ESGW:~$


Yes, since I'm new to Ubuntu, I was playing around when I made the user "username". So what should I do now? Thank you again for the help.

---

### Post by Impavidus on 2013-04-09
Clearly, user "username" doesn't exist. His home directory, /home/username, still exists but is owned by user eric (at least, that's the name belonging to it. There might be a mix-up of usernames and usedIDs) But if you're positive you don't want to keep eny files in /home/username, try```
sudo rm -rf /home/username
```(You used sudo r[COLOR=#ff0000]e[/COLOR] -f. This gave your error)
(Careful: sudo rm-rf is a very dangerous command. It can easely destroy your system)

---

### Post by Gannas on 2013-04-09
Thank you! That did the trick. Here's the proof!

gannas1@HS1920ESGW:~$ sudo rm -rf /home/username
[sudo] password for gannas1:
gannas1@HS1920ESGW:~$ ls -l /home
total 8
drwxr-xr-x 2 eric    eric    4096 Apr  8 14:41 eric
drwxr-xr-x 4 gannas1 gannas1 4096 Apr  8 15:15 gannas1
gannas1@HS1920ESGW:~$

---


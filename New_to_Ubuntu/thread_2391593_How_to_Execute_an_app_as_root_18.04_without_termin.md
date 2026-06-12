---
title: "How to Execute an app as root 18.04 without terminal"
date: 2018-05-11
forum: New to Ubuntu
---

### Post by arnoldo2 on 2018-05-11
Morning, 

I have a problem i need to execute a program as root in ubuntu 18.04 with out a terminal opened,

i used to add the following  "gksudo -k -u root /appName" in the Exec tag in the launcher but in this new version gksu was deleted so.

does anybody knows a way to execute my program with root rights?

---

### Post by adelpozoman-f on 2018-05-11
have you tried installing gksudo?

---

### Post by deadflowr on 2018-05-11
> **adelpozoman-f said:**
> have you tried installing gksudo?

Does not exist on 18.04.

You need to use or setup pkexec.
You'll probably need to create a rule/action.
Older discussion here:
[https://ubuntuforums.org/showthread.php?t=2225832]("https://ubuntuforums.org/showthread.php?t=2225832")

More recent discussion on new method for opening files and directories here:
[https://ubuntuforums.org/showthread.php?t=2377380]("https://ubuntuforums.org/showthread.php?t=2377380")

---


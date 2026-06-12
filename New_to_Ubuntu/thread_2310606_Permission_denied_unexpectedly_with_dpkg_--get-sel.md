---
title: "Permission denied unexpectedly with dpkg --get-selections"
date: 2016-01-20
forum: New to Ubuntu
---

### Post by Kim_Holder on 2016-01-20
I am trying to follow directions [here]("http://askubuntu.com/a/99171/364597") to back up my installed package list and settings before installing Windows and then reinstalling Ubuntu 14.04 into a dual boot setup. The second step is to create a file with a list of all installed packages.
```

briligg@briligg-MS-7917:~$ dpkg --get-selections > ~/backup/installed_packages.log
bash: /home/briligg/backup/installed_packages.log: Permission denied

```

The instructions don't mention this requiring root access. So i am wondering if there is some issue i should do something about, and how to handle this.

---

### Post by yetimon_64 on 2016-01-20
When you make a folder in your home directory you DON'T use sudo before the command as per the linked instructions, that is their mistake not yours. Delete the backup directory and recreate it without "sudo". When I did it here as the user not root, your command works. Good luck.

Edit: just confirmed a permissions error when I used the command as per the link and got the same error you got.

Edit2: seems the instructions are mixing permissions, another way this could work is to use sudo on every command as **some** may need to be run as root. They may have just accidentally missed the one sudo command on that particular dpkg command. It does seem to work here without it though. The other commands do need to be run as root. I would suggest you wait further advice to check this out.

---

### Post by Kim_Holder on 2016-01-20
Thanks :)

---


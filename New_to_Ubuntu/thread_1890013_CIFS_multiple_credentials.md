---
title: "CIFS multiple credentials"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by Guruprasad on 2011-12-02
I have three users on a single computer.
I need to mount a shared folder using CIFS in fstab. But it should mounted with the username of the currently logged in user.

Thanks in advance.

---

### Post by Morbius1 on 2011-12-02
I don't know how you do that in fstab. You can mount it so it's available to every user on the system or to every member of a given group but I don't know how you mount it with the owner of the mount changing depending on who is logged in at the moment. And you can't change the credentials depending on who is logged on at the moment.

But Nautilus does that by default you know. When you mount it through Nautilus or "Connect to Server" you mount it so that you are the owner of the mount point and you pass only your credentials. If you want to automate that process so that it happens at login then I would suggest Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Every user would have to set up Gigolo on their own account and every time they login they will auto mount the remote share with their own credentials.

---

### Post by Guruprasad on 2011-12-04
Thank you very much... It solved by problem...

---


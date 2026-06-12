---
title: "Permission Change"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by dunbrokin on 2011-10-07
I am moving my .thuderbird account from one profile to another. I used sudo natuilus to copy and move the folder. When I  try to change the permission of the folder and contents by clicking on the folder and changing the permissions, it will work for the top folder....but, despite pressing "apply to all files/folders" it does not carry through. All of the files still carry root privilege. What am I doing wrong?

---

### Post by dniMretsaM on 2011-10-07
```
sudo chmod [desired privileges] /path/to/folder/ -R
```

That will change the permission of the folder. The -R option tells it to apply the permissions recursively (to all subfolders/files).

---

### Post by dunbrokin on 2011-10-07
Thanks for that....I had tried it already....but the permissions of many of the files still stay as root even after sudo chmod 666 /xxxxx/Desktop/.thunderbird -R

---

### Post by dniMretsaM on 2011-10-07
> **dunbrokin said:**
> Thanks for that....I had tried it already....but the permissions of many of the files still stay as root even after sudo chmod 666 /xxxxx/Desktop/.thunderbird -R

Is it possible that you're trying to change the owner?

---

### Post by dunbrokin on 2011-10-07
Yes, I am trying to change the owner as I am swapping it from one profile to a new one.

---

### Post by mibart on 2011-10-07
After You copy thunderbird config folder from one account to another, type in terminal:
```

$ chown -R dunbrokin:dunbrokin ~/.thunderbird
$ chmod -R u+rw ~/.thunderbird

```The first command will change owner of directory and it's content to You (replace dunbrokin with desired username). The second one gives you permission to write into that directory. After that, type in terminal:
```

$ man chown

```and then:
```

$ man chmod

```

---

### Post by dunbrokin on 2011-10-07
Thanks, much obliged...I will give that a try later when I have some more time to spend on this...


Yep, that worked perfectly for me.....thank you for your help/

---

### Post by dniMretsaM on 2011-10-07
> **dunbrokin said:**
> Yes, I am trying to change the owner as I am swapping it from one profile to a new one.

Ok, that explains it. The [FONT="Courier New"]chown[/FONT] command is used for changing the owner.

---


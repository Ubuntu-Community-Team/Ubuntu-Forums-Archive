---
title: "How to use X config backup file"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by SandyM on 2008-08-07
I have certain problems in my Nvidia drivers as ubuntu is not recognizing mycard I have done everything I could do. Now I want to use Xconfig back up files to revert to earlier display settings when everything was doing fine.

PLEASE TELL ME HOW TO USE THESE BACK UP FILES

---

### Post by ace007 on 2008-08-07
You just need to replace the current text file with the backup

So, to restore your backup...
```

sudo mv <backup file> /etc/X11/xorg.conf

```

---

### Post by SandyM on 2008-08-07
> **ace007 said:**
> You just need to replace the current text file with the backup

So, to restore your backup...
```

sudo mv <backup file> /etc/X11/xorg.conf

```
But where can I see these saved X config files so that I can see their name to restore them

---

### Post by unutbu on 2008-08-07
Using the gui:

```
gksu nautilus
```
Navigate to /etc/X11
The backups should all be called xorg.conf-something.

Using the command line:

```

ls -l /etc/X11                             # List all the files in /etc/X11
sudo mv <backup file> /etc/X11/xorg.conf   # ace007's command

```

---


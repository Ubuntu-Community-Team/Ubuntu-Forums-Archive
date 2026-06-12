---
title: "Permission denied in ubuntu"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by Arlyajt on 2012-10-15
I paste the theme on themes folder but it say permission denied i use chown and -m but isn't work. anyone help me about that.

---

### Post by Wim Sturkenboom on 2012-10-15
Where is that themes folder? /usr/share/themes? It's bad habit to change ownership of system directories!

What is the -m option? For which command?

And the solution for modifying root owned directories and files is to use sudo (or gksudo in case of the graphical environment).

```

gksudo nautilus

```

---

### Post by aabed91 on 2012-10-15
in some action you need to take administrator permission.

the permission takes using command:

```

sudo 

```

then it request the password

---

### Post by cortman on 2012-10-15
As Wim says, DON'T mess with ownership/permissions of system directories!
You can either use sudo cp in the terminal:

```
sudo cp my_file /usr/share/themes
```

Or open the file manager as root (run this from the terminal):

```
gksu nautilus
```

You'll be able to copy/paste in there, but don't use it with root permissions for normal use.

---

### Post by audiomick on 2012-10-15
> **aabed91 said:**
> in some action you need to take administrator permission.

the permission takes using command:

```

sudo 

```

then it request the password

This is true, but I think the post from Wim Sturkenboom preivous to that post is more to the point.

---


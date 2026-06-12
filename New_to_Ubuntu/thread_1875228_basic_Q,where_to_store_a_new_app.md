---
title: "basic Q,where to store a new app"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by And_ on 2011-11-04
I have down loaded Python3 and I have a very basic question. Should I store my applications like Python in the /opt directory? Or in my own directory /home/my..?

I am defined as an administrator in the system (only user).
I go in the file system,select opt and  when I try to create a new Dir in opt I get the message "permission denied" (Error creating directory: Permission denied). 
Who is allowed to manipulate the opt directory???

---

### Post by Lars Noodén on 2011-11-04
You can store them under your home directory, /home/me/bin
and add that directory to your path.  Or you, if you have system permissions, you can add it to [/usr/local/bin](http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html)

---

### Post by dFlyer on 2011-11-04
you need admin sudo to create a directory in /opt

---

### Post by And_ on 2011-11-04
> **Lars Noodén said:**
> You can store them under your home directory, /home/me/bin
and add that directory to your path.  Or you, if you have system permissions, you can add it to [/usr/local/bin]("http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html")

Thanks Lars

I am defined as an administrator but I am not allowed to store the files in usr/local/bin.  Shouldn't I have the required permissions.?
How do I get all the permission?

---

### Post by Lars Noodén on 2011-11-04
You have to use [sudo](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html):
```

sudo cp /home/me/bin/myscript /usr/local/bin/.

```

---


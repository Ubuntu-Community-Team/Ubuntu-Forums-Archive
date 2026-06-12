---
title: "open gl"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by msvf on 2008-06-22
How do i install opengl python?

---

### Post by fahadsadah on 2008-06-22
```
sudo aptitude install python-opengl
```

---

### Post by msvf on 2008-06-22
I dont think it worked, it said " Couldn't find any package whose name or description matched "python-opengl"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used."

---

### Post by fahadsadah on 2008-06-22
You need to add the Universe/Multiverse repos:

```
echo "deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse\ndeb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse\ndeb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse\ndeb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse" > /etc/apt/sources.list
```

Once you have done that, try again

I am assuming you use Ubuntu 8.04; if not, post here and I will give you a different command

---

### Post by ad_267 on 2008-06-22
> **fahadsadah said:**
> You need to add the Universe/Multiverse repos:

```
echo "deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse\ndeb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse\ndeb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse\ndeb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse" > /etc/apt/sources.list
```

Once you have done that, try again

I am assuming you use Ubuntu 8.04; if not, post here and I will give you a different command

Won't that replace the entire /etc/apt/sources.list?

Shouldn't it be:
```
sudo echo "deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse\ndeb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse\ndeb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse\ndeb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse" >> /etc/apt/sources.list
```

(Use >> not > and sudo is required)

---

### Post by msvf on 2008-06-22
ahh no iv got 7.10, and when i put the command in it says "bash: /etc/apt/sources.list: Permission denied"

---

### Post by ad_267 on 2008-06-22
Do this instead:

Just go to system - administration - synaptic package manager.
Go to Settings - Repositories and tick next to Universe, Restricted, Multiverse and hit close then apply.

You could also run "sudo gedit /etc/apt/sources.list" And delete the # in front of the lines that say universe, restricted and multiverse.

---


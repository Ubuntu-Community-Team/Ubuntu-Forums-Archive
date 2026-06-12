---
title: "[SOLVED] $HOME is pointing to wrong folder"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Java Geek on 2008-07-27
I am an xubuntu noob and it was working correctly last night. I booted up this morning and i recieve this maessage. I went into the terminal and typed

```
cd $HOME
```

This put me into the system directory "/" when it is supposed to be at "/home/username" any help on how to change $HOME back to where it is supposed to be would be very helpful

---

### Post by Java Geek on 2008-07-27
SOLVED! The command that is placed into the failsafe terminal is

```
sudo usermod -d /path/to/home username
```

This code changes the location of the $HOME variable, allowing you to change it an log in

---


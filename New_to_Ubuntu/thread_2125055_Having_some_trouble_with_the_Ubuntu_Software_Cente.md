---
title: "Having some trouble with the Ubuntu Software Center"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by fabrivera99 on 2013-03-12
When I try to open the Ubuntu Software Center the program just freezes there, only with a white screen in it. The problem started a day I was updating some software but my PC shutdown suddenly and the Software Updater and the Software Center never open again.

Note: I already tried to use the install and uninstall command on the terminal.

PD:
Sorry for my bad English is just that I am not use to write in this language.

---

### Post by tejpatel98 on 2013-03-12
Have you tried installing updates again after the first one was interrupted?

---

### Post by ibjsb4 on 2013-03-12
Try update in terminal

```
sudo apt-get update
```

Any errors?

---

### Post by fabrivera99 on 2013-03-13
I already tried that. The terminal sends me this error.


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

---

### Post by fabrivera99 on 2013-03-13
Yes. But I can only update things from the Terminal.
The Software Updater crashes every time I open it.

---

### Post by ibjsb4 on 2013-03-13
You need to uncheck CDrom in your sources list.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by fabrivera99 on 2013-03-13
[ATTACH=CONFIG]240146[/ATTACH]
I dont know how to uncheck it.

---

### Post by ibjsb4 on 2013-03-13
Wow, guess that link is outdated. sorry

Please post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by tejpatel98 on 2013-03-13
So then your Update Manager is crashing as well?

---

### Post by fabrivera99 on 2013-03-15
Yes sir, it is.

---

### Post by fabrivera99 on 2013-03-17
I already solve it by re installing Ubuntu.

---


---
title: "Crossover help"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Coolride on 2008-10-29
Hey all, i've downloaded the install-crossover-games-7.1.2.sh file on my desktop, but can't get this thing to install, what's the command ? I tried every variation of sh install I could think of.:)

---

### Post by SunnyRabbiera on 2008-10-29
did you try sudo?
and did you check if its been made executable?

---

### Post by cariboo on 2008-10-29
I just installed it this morning, its pretty simple. On a Applications-->Accessories--Terminal and type:

```
cd ~/Desktop
```

This changes the directory to /home/user/Desktop, next in the same terminal type:

```
chmod +x install*
```

The will make the file executeable. Now just close the terminal and double-click on the file on your desktop.

Jim

---

### Post by Coolride on 2008-10-29
Thanks Guys, problem solved. making it executable was the ticket!

---


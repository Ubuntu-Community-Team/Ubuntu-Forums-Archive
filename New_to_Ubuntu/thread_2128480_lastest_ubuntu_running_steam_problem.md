---
title: "lastest ubuntu running steam problem"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by codeacer101 on 2013-03-23
ok so i installed steam though ubuntu software centre.but my problem is once up and running is when i go to install games asin download them a message comes up (black ops is not available on your current platform ) this happens with all my games i try install not just black ops im running 64bit..please help

---

### Post by SMOKE14 on 2013-03-23
Haven't used Steam for Ubuntu in a while, but I'm pretty sure that I saw that Call of Duty was **not** being ported to Linux.

EDIT: Just checked the Steam website, the game is not on Linux currently.

---

### Post by El Tito on 2013-03-23
Do you have ia32-libs installed?
```
sudo dpkg -s ia32-libs
```
which is your version of ubuntu?

---

### Post by El Tito on 2013-03-23
@SMOKE14 is right, no Black Ops for linux. Also, I have a lot of humble bundle linux games,
but not all are available on steam. Have you managed to install something, or you can't install any games?

---

### Post by codeacer101 on 2013-03-24
thats ashame as i got black ops 1 and mw 2 :(..left 4 dead dont even work but thanks 4 checking it up 4 me!

---

### Post by codeacer101 on 2013-03-24
im not sure witch it is 32 or 64 as i installed it by ubuntu software centre so i be guessing it would put right one on?

---

### Post by codeacer101 on 2013-03-24
so it looking like i have stick with windows alittle bit longer then ??..and thanks guys for replys!

---

### Post by El Tito on 2013-03-25
> **codeacer101 said:**
> im not sure witch it is 32 or 64 as i installed it by ubuntu software centre so i be guessing it would put right one on?

In theory Steam is 32bits, but Ubuntu has multiarchitecture enabled, so you shouldn't have any problems installing.

---


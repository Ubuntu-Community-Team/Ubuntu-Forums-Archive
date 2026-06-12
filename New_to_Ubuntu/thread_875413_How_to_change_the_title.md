---
title: "How to change the title?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by sharks on 2008-07-30
How to change the title in terminal?

> arvind@arvind-desktop:~$ 

---

### Post by knightcoder on 2008-07-30
[http://www.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www.ibm.com/developerworks/linux/library/l-tip-prompt/)

---

### Post by steveneddy on 2008-07-30
> **sharks said:**
> How to change the title in terminal?

user name or computer name?

---

### Post by sharks on 2008-07-30
computer name> arvind-desktop

---

### Post by Diabolis on 2008-07-30
How to: [http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

Colors guide: [http://www.pixelbeat.org/docs/terminal_colours/](http://www.pixelbeat.org/docs/terminal_colours/)

Mine:
[PHP]PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u\[\033[01;35m\]@\[\033[01;32m\]\h\[\033[00m\]:\[\033[01;35m\]\w/\[\033[01;33m\]\$ \e[0m';;esac[/PHP]

Its called "command prompt", not "title".

---


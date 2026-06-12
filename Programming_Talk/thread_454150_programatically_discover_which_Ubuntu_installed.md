---
title: "programatically discover which Ubuntu installed?"
date: 2007-05-25
forum: Programming Talk
---

### Post by kornelix on 2007-05-25
Is there a way to find out, programatically, which version of Ubuntu (or any other Linux) is installed? This is for the purpose of making alternate code paths or messages.

Kernel version can be found with bash command  # uname -srm

---

### Post by WW on 2007-05-25
Try **lsb_release**, e.g.
```

~$ lsb_release -h
usage: lsb_release [options]

options:
  -h, --help         show this help message and exit
  -v, --version      show LSB modules this system supports
  -i, --id           show distributor ID
  -d, --description  show description of this distribution
  -r, --release      show release number of this distribution
  -c, --codename     show code name of this distribution
  -a, --all          show all of the above information
  -s, --short        show all of the above information in short format
~$ lsb_release -irc
Distributor ID: Ubuntu
Release:        6.06
Codename:       dapper
~$

```
However, I don't think you can count on this command being installed in all Linux distributions. I tried it on a debian computer (running sarge, the "old stable" debian), and the command was not found.

---

### Post by EndPerform on 2007-05-25
Just check /etc/issue:

```

fubar@grim:~$ cat /etc/issue
Ubuntu 7.04 \n \l

```

---

### Post by WW on 2007-05-25
That works in debian, too.

**Ubuntu**
```

~$ cat /etc/issue
Ubuntu 6.06.1 LTS \n \l

~$

```

**Debian** (sarge, "old stable")
```

~$ cat /etc/issue
Debian GNU/Linux 3.1 \n \l

~$

```

---

### Post by amo-ej1 on 2007-05-25
/etc/issue is way unreliable ... it can be modified extremely easy.

 lsb_release would imo be the way to go ... but again it's only linux proof, not bsd proof

---

### Post by EndPerform on 2007-05-30
> **amo-ej1 said:**
> /etc/issue is way unreliable ... it can be modified extremely easy.

 lsb_release would imo be the way to go ... but again it's only linux proof, not bsd proof

While that may be true, you can't count on lsb_release being installed, but you can count on /etc/issue being there, so it's pretty much 50/50.  I don't ever remember a case where /etc/issue had been toyed with.

---

### Post by Ramses de Norre on 2007-05-30
> **amo-ej1 said:**
> /etc/issue is way unreliable ... it can be modified extremely easy.

 lsb_release would imo be the way to go ... but again it's only linux proof, not bsd proof

Not even linux proof, I'm on Arch and haven't got that command. /etc/issue is here though.

---

### Post by Nikron on 2007-05-30
> **Ramses de Norre said:**
> Not even linux proof, I'm on Arch and haven't got that command. /etc/issue is here though.

Same, but my /etc/issue is different since I changed it.

---


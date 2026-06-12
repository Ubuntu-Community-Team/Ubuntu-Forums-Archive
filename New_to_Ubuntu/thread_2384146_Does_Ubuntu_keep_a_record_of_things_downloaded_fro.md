---
title: "Does Ubuntu keep a record of things downloaded from &quot;Ubuntu Software Center&quot;"
date: 2018-02-02
forum: New to Ubuntu
---

### Post by elvis6 on 2018-02-02
Is there somewhere I can go, to access and view everything that has been downloaded via the "Ubuntu Software Center" ?

---

### Post by SeijiSensei on 2018-02-02
There should be a copy of every package you updated in /var/cache/apt/archives.

You can generate an alphabetical list with
```

cd /var/cache/apt/archives
ls *.deb | sort > /home/username/pkglist

```
That creates a list of the updated packages in a file called "pkglist" in "username's" home directory.

You can also generate a complete inventory of installed packages with the command

```
cd ~; sudo dpkg --get-selections > bigpkglist 
```

---

### Post by elvis6 on 2018-02-02
Thanks, appreciate it

---

### Post by mc4man on 2018-02-02
The bigpkglist command is very useful, thanks.
As far as the archives the default now for apt is to not save. Whether ubuntu-software  uses that don't know as use synaptic.
Synaptic has advantage of saving every apt action in an easy to navigate &  read history, this includes installs, updates & removals. Plus the origin tab is useful.
(- synaptic doesn't do snaps, only ubuntu-software or cli for those. Probably never will..

---

### Post by SeijiSensei on 2018-02-03
> **mc4man said:**
> The bigpkglist command is very useful, thanks.

You're welcome!  A slightly improved version that deletes the "install" text at the end of each line:

```
sudo dpkg --get-selections | sed 's/[[:space:]+]install//g' > bigpkglist
```

---


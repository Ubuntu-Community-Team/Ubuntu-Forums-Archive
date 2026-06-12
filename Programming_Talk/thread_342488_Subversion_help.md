---
title: "Subversion help"
date: 2007-01-20
forum: Programming Talk
---

### Post by rand0m3r on 2007-01-20
hi, i decided to learn how to use svn. in the manual, it gave a command to start off. but i already get an error. do you know what's wrong?

:~$ svnadmin create /path/to/repos
svnadmin: Repository creation failed
svnadmin: Could not create top-level directory
svnadmin: Can't create directory '/path/to/repos': No such file or directory


thanks.

---

### Post by rai4shu2 on 2007-01-20
You have to mkdir first, although I doubt you actually want to mkdir /path/to/repos (I think whenever something says /path/to they just mean something like /var/www/repos or wherever it is you store stuff).

---

### Post by supirman on 2007-01-20
You should enter a valid directory path, not literally "/path/to/repos".  For example, if you wanted to store it in your home directory, it'd be

```

cd
mkdir repos
svnadmin create ~/repos

```

This will put you in your home directory, make a repos directory, then create the repo in that directory.

---


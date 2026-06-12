---
title: "MySQL Server Directory Structure?"
date: 2007-01-18
forum: Programming Talk
---

### Post by pak33m on 2007-01-18
Hello,

I am just into the intro to the MySQL Press MySQL Tutorial book & installed MySQL Server (& deps) via apt-get, but I don't find the directory structure that they refer to in the book, i.e the bin, data, scripts, etc. folders.

I install MySQL on Windows, Red Hat & Suse at work & have always worked in the folders that seem missing from my install.

The only difference that I see is that the book refers to 4.0 & 4.1 & this is what I install at work even, but  my install via apt-get was 5.0.

Could anybody at least share some knowledge with me?

---

### Post by phossal on 2007-01-18
/var/lib/mysql? Read the my.cnf file in /etc/mysql, too. It should give you some clue.

---

### Post by pak33m on 2007-01-18
I copied all of the mysql files, less the bin, data, scripts,etc. folders, to from /var/lib/mysql to /usr/local/mysql & changed the path in the my.cnf to reflect this change.  Even at /var/lib/mysql the folders were not found?

---


---
title: "Am I backing up SVN correctly?"
date: 2010-01-06
forum: Programming Talk
---

### Post by Eugene_Bondarenko on 2010-01-06
Hi,

I am running Ubuntu 9.10 and I've set SVN server on my comp. I've installed one of the programs (sbackup) from software center and set it to run incremental backups for many places including my svn server (located in /home/svn/). However I am not fully aware of how SVN server works so I am not sure whether I am making backups correctly. Does it store everything in filesystem? So if I backup its directory (/home/svn/), do I get everything related to my repositories backed up? It doesn't store any data in some kind of DB or in some other directories, right?

---

### Post by iharrold on 2010-01-06
Backup:

```

$ svnadmin dump /Path/To/Repository/Repo > /Store/Backup/Here/MyRepobackup.dump

```

Restore:

```

$ sudo svnadmin load /Path/To/Repository/Repo < /Store/Backup/Here/MyRepobackup.dump

```

The dump can be tar.gz or bz2'd to compress it for size aswell.
Compress:
```

$ tar -cvzf /Store/Backup/Here/MyRepobackup.tar.gz /Store/Backup/Here/MyRepobackup.dump

```

UnCompress:
```

$ tar -xvzf /Store/Backup/Here/MyRepobackup.tar.gz -c /Store/Backup/Here/
```

The repository is really a DB on the server. The Dump copies out the repository(with history) to an archived raw file.

---

### Post by not_a_phd on 2010-01-08
I have copied svn repository directories from a server to another machine, and have been able to access them by the:

```
svn checkout svn://pathtorepo/reponame 
```

command. 

The svnadmin backup method is probably both more efficient and safer though.

---

### Post by Eugene_Bondarenko on 2010-01-10
Thanks, that helped!

---


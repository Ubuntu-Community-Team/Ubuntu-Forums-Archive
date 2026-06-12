---
title: "Bash: Is this directory newer than the other?"
date: 2011-03-23
forum: Programming Talk
---

### Post by barisurum on 2011-03-23
Hell000;

For a script I work on, i need to understand whether directory X is newer (contents more recently modified) than directory Y. I understand that I can't do this by:

```
if [ $X -nt $Y ]
then...
```

The question is: how can I do that? :D Thanks !NULL times!

---

### Post by Arndt on 2011-03-23
> **barisurum said:**
> Hell000;

For a script I work on, i need to understand whether directory X is newer (contents more recently modified) than directory Y. I understand that I can't do this by:

```
if [ $X -nt $Y ]
then...
```

The question is: how can I do that? :D Thanks !NULL times!

You need to look at the modification dates of all files and directories (recursively) inside the two directories.

You can do that in the shell script itself, or with awk or perl, for example, with a little loop logic.

---

### Post by SeijiSensei on 2011-03-23
The command **find** can be used to list files/directories newer or older than another file/directory.  Take a look at the "-anewer file" option in the [find man page]("http://linuxcommand.org/man_pages/find1.html").  Something like "find /dir1 -anewer /dir2" might wprk.  find is immensely powerful, and its syntax can be daunting, so it usually takes me a few tries before I find the right specification of options.

Once you have the output from find, you can test to see if it returned any files like this:

```

if [ "$(find /dir1 -anewer /dir2)" != "/dir1" ] then

```

find will return just /dir1 if there are no more recent files.

By the way, if you writing this as part of a backup script, you might find [rsync]("http://rsync.samba.org/") to be a better solution.  It will automatically identify files that differ between a source and target directory and copy only those files that have changed.

---

### Post by barisurum on 2011-03-23
[QUOTE=SeijiSensei]By the way, if you writing this as part of a backup script, you might find rsync to be a better...[/QUOTE]

Damn! I knew I had been inventing the wheel from scratch! :( I had no idea on rsync.. I'll finish the script anyway and use it coz its MINE MINE! hahaha :D. Thanks so much you've been of great help! :D

---


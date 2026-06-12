---
title: "How to du -sm all?"
date: 2011-08-20
forum: Programming Talk
---

### Post by huangyingw on 2011-08-20
Hello,
   I have run such command, with intention to calculate the size of all sub folders under /home/huangyingw
   ```
root@desktop:/home/huangyingw# du -sm /home/huangyingw/*|sort -n
```
   But in fact, I found that, the hidden folder like /home/huangw/.android, /home/huangyingw/.mozilla, could not be listed.
   How could I list all sub directories , including those .* directories, in one command?

---

### Post by The Cog on 2011-08-20
I can think if a couple of ways, but they're not very nice.
This first one launches du many times:
```
find . -maxdepth 1 -type d -exec du -sh '{}' \;
```
This one needs to set IFS to be able to handle filenames with spaces:
```
IFS=$'\n'
du -sh $(find . -maxdepth 1 -type d)
```

---

### Post by sisco311 on 2011-08-20
In bash you can enable the dotglob option:
```
shopt -s dotglob
du -sh *
shopt -u dotglob
```

---

### Post by ofnuts on 2011-08-20
> **The Cog said:**
> I can think if a couple of ways, but they're not very nice.
This first one launches du many times:
```
find . -maxdepth 1 -type d -exec du -sh '{}' \;
```
If you terminate your grep -exec command with '+' instead of ';' the command is called only once on all the files together.

---

### Post by SeijiSensei on 2011-08-20
```
du -s \.?*
```

will display the hidden directories.

---

### Post by sisco311 on 2011-08-20
> **SeijiSensei said:**
> ```
du -s \.?*
```

will display the hidden directories.

That will also match .. (the hardlink to the parent directory).

. is no a special character, so you don't have to quote it.

You can match all the dot files, but not . or .. with two globs:
```
echo .[^.]* ..?*
```

Or you could use the GLOBIGNORE variable:
```
GLOBIGNORE=.:..
echo .*
```

---

### Post by huangyingw on 2011-08-20
> **The Cog said:**
> I can think if a couple of ways, but they're not very nice.
This first one launches du many times:
```
find . -maxdepth 1 -type d -exec du -sh '{}' \;
```
This one needs to set IFS to be able to handle filenames with spaces:
```
IFS=$'\n'
du -sh $(find . -maxdepth 1 -type d)
```
Really, your solution is too complicated.

---

### Post by huangyingw on 2011-08-20
> **sisco311 said:**
> In bash you can enable the dotglob option:
```
shopt -s dotglob
du -sh *
shopt -u dotglob
```
I appreciate this solution.:popcorn:

---


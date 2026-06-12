---
title: "Highlighted Directories HELP!!"
date: 2019-09-13
forum: New to Ubuntu
---

### Post by tshenukahp on 2019-09-13
[ATTACH=CONFIG]284017[/ATTACH]
Can anyone explain why these directories are highlighted ?

---

### Post by Impavidus on 2019-09-13
The colours used by ls are defined by the environment variable LS_COLORS; for details, see```
echo $LS_COLORS
man ls
man dircolors
dircolors --print-database
```
The colours depend on the file type (regular file, symlink, pipe etc.), permissions and extension. As you show some files and directories in /media, they may be on a different filesystem type (like ntfs) that doesn't support Unix permissions. This means different permissions than on the directories in your home directory and therefore different colours.

---


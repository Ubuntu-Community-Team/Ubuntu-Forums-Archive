---
title: "scripting - grep - distinct list of found files"
date: 2018-09-27
forum: Programming Talk
---

### Post by marchello_lippi2 on 2018-09-27
Hi all, 
When I look for some keyword1 in path1 and the keyword1 is found several times in the same file, it returns the file path several times accordingly.
Is there any way to get distinct list of files (full file path) ?

---

### Post by steeldriver on 2018-09-27
What exactly is the command you are using? if you use grep's `-l` option it should exit after the first match:

```

       -l, --files-with-matches
              Suppress normal output; instead print the  name  of  each  input
              file  from  which  output would normally have been printed.  The
              scanning will stop on the first match.

```

---

### Post by aromo2 on 2018-09-27
or even better:
```
ls -l /*path1*/**keyword1**
```

---

### Post by marchello_lippi2 on 2018-09-27
[COLOR=#DD4814][steeldriver]("https://ubuntuforums.org/member.php?u=1627500"), [/COLOR][COLOR=#DD4814][COLOR=#000000][aromo2]("https://ubuntuforums.org/member.php?u=1843785"),[/COLOR][/COLOR]
The -l option is exactly what I was looking for. Thanks!

---

### Post by steeldriver on 2018-09-27
... fwiw I assumed you were searching for files with the keyword within their contents, not in their filenames

---

### Post by marchello_lippi2 on 2018-09-27
Yes, I was looking for a way to find file with keyword1 as part of file text, not part of filename. Anyway, ls -l would be helpful sometimes as well.

---


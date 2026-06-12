---
title: "Can I exclude a directory with diff?"
date: 2009-03-31
forum: Programming Talk
---

### Post by mike_g on 2009-03-31
I have a backup of a website. I want to diff the source to see what files have been changed. My problem is that theres a folder with lots of files in it that I want to ignore. I tried this:
```
diff -rqw [COLOR="DarkRed"]-X/var/www/mysite/mybigfolder[/COLOR] /var/www/mysite mybackupfolder
```
But I get an error in the red bit because its a folder not a file. Whats the simplest way I can do what I want to do?

Cheers,

Mike

---

### Post by ubuser_7 on 2009-03-31
```

       -x PAT  --exclude=PAT
              Exclude files that match PAT.

       -X FILE  --exclude-from=FILE
              Exclude files that match any pattern in FILE.
```

-X is used to give the path of the file which has patters for exclusion.

Something like 

```
-x "/var/www/mysite/mybigfolder/*"
```

should work. This will exclude all files which have /var/www/mysite/mybigfolder/ in their name.

---

### Post by Arndt on 2009-03-31
> **mike_g said:**
> I have a backup of a website. I want to diff the source to see what files have been changed. My problem is that theres a folder with lots of files in it that I want to ignore. I tried this:
```
diff -rqw [COLOR="DarkRed"]-X/var/www/mysite/mybigfolder[/COLOR] /var/www/mysite mybackupfolder
```
But I get an error in the red bit because its a folder not a file. Whats the simplest way I can do what I want to do?

Cheers,

Mike

The argument to -X is meant to be a file containing patterns of files to ignore. This is apparently not pattern in the regexp sense, but in the shell file expansion sense. I just tried it, so I can't say more about it.

---


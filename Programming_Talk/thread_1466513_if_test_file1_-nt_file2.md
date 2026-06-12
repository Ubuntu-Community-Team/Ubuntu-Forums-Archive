---
title: "if test file1 -nt file2"
date: 2010-04-30
forum: Programming Talk
---

### Post by dragos2 on 2010-04-30
I have this script:
```

if test "f1.txt" -nt "f2.txt";
then
 touch f2.txt
else
 touch f1.txt
fi

```which always returns that f1 has a newer time.

What I did wrong ?

---

### Post by kaibob on 2010-04-30
As written, your shell script modifies the time stamp of f2.txt and nothing else. Was it your intent for the second touch command to modify f1.txt? If so, the script works OK. 

> $ ls -l -t file1 file2
-rw-r----- 1 bob bob 143 2010-04-30 09:04 file1
-rw-r----- 1 bob bob  35 2010-04-30 09:03 file2

$ if test file1 -nt file2 ; then touch file2 ; else touch file1 ; fi

$ ls -l -t file1 file2
-rw-r----- 1 bob bob  35 2010-04-30 09:13 file2
-rw-r----- 1 bob bob 143 2010-04-30 09:04 file1

$ if test file1 -nt file2 ; then touch file2 ; else touch file1 ; fi

$ ls -l -t file1 file2
-rw-r----- 1 bob bob 143 2010-04-30 09:15 file1
-rw-r----- 1 bob bob  35 2010-04-30 09:13 file2

---

### Post by dragos2 on 2010-05-04
> **kaibob said:**
> As written, your shell script modifies the time stamp of f2.txt and nothing else. Was it your intent for the second touch command to modify f1.txt? If so, the script works OK.

Sorry, I edited, I have a script that runs through cron every x minutes and it updates file1
if file2 is newer and vice versa:

But everytime it updates f1.txt

```

if test "f1.txt" -nt "f2.txt";
then
 touch "f2.txt"
 echo "updating f2.."
 find $project/ 2>/dev/null > f2.txt
 touch "f2.txt"
 changed=$(diff f2.txt f1.txt)
 echo "$changed" | mailx -s "Someinfo" some@mail.com
else
 touch "f1.txt"
 echo "updating f1.."
 find $project/ 2>/dev/null > f1.txt
 touch "f1.txt"
 changed=$(diff f1.txt f2.txt)
echo "$changed" | mailx -s "Someinfo" some@mail.com
fi

```

I fixed it. The upper scripts works now. Maybe someone finds it useful :)

---


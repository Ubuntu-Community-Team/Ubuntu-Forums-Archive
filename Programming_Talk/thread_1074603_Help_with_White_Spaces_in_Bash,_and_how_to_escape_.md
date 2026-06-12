---
title: "Help with: White Spaces in Bash, and how to escape some..."
date: 2009-02-19
forum: Programming Talk
---

### Post by techflat on 2009-02-19
Hi there everybody,

I've been googling a lot to try to solve my problem, I think the closest I got was this post ( [http://ubuntuforums.org/showpost.php?p=2604052&postcount=11](http://ubuntuforums.org/showpost.php?p=2604052&postcount=11) ) and there's also something about $IFS but I think that won't solve my problem.

Here's my problem, I'm trying to run a script (to do a backup) in wich I'd like to execute a command. So far so good...
The problem comes when I try to "build" the command with a string, I need to escape a couple of white spaces inside the string but not all.

Here's my script (not all, only the parts needed to understand it):
```
#!/bin/bash

# Local dirs
dirs=(
# array position 1:
"/media/sdb1/academic"

# array position 2:
"/media/sdb1/archivos recibidos"

# array position 3
#here's my problem
"--exclude 'direcory name with spaces' /media/sdb1/media"
)

backupDiscDir=/backupDisc/backupDir

for ((i=0;i<${#dirs[*]};i+=1)); do
echo ""
echo ""
echo "rsync -avz -n --delete -u "${directorios[i]}" $backupDiscDir"
rsync -avz -n --delete  -u "${directorios[i]}" $backupDiscDir
done
```

So with this script, (array position 1) and (array position 2) work well, the problem comes in (array position 3).

I want the command to work like if it were tiped in in a terminal, so for (array position 3) it would be:
```

rsync -avz -n --delete  -u --exclude 'direcory name with spaces' /media/sdb1/media /backupDisc/backupDir

```

But instead of that, with what I've tried this happens:
[LIST]
[*]**Example Case 1:**
```
#!/bin/bash

# Local dirs
dirs=(
# array position 1:
"/media/sdb1/academic"

# array position 2:
"/media/sdb1/archivos recibidos"

# array position 3
#here's my problem
"--exclude 'direcory name with spaces' /media/sdb1/media"
)

backupDiscDir=/backupDisc/backupDir

for ((i=0;i<${#dirs[]};i+=1)); do
echo ""
echo ""
echo "rsync -avz -n --delete -u ${directorios[i]} $backupDiscDir"
rsync -avz -n --delete  -u ${directorios[i]} $backupDiscDir
done
```
The result in the command generated is:```

rsync -avz -n --delete  -u --exclude direcory name with spaces /media/sdb1/media /backupDisc/backupDir
```
Wich takes "directory", "name", "with" and "spaces" as parameters.
[*]**Example Case 2:**
```
#!/bin/bash

# Local dirs
dirs=(
# array position 1:
"/media/sdb1/academic"

# array position 2:
"/media/sdb1/archivos recibidos"

# array position 3
#here's my problem
"--exclude direcory\ name\ with\ spaces /media/sdb1/media"
)

backupDiscDir=/backupDisc/backupDir

for ((i=0;i<${#dirs[]};i+=1)); do
echo ""
echo ""
echo "rsync -avz -n --delete -u ${directorios[i]} $backupDiscDir"
rsync -avz -n --delete  -u ${directorios[i]} $backupDiscDir
done
```
The result in the command generated is:```

rsync -avz -n --delete  -u --exclude direcory\ name\ with\ spaces /media/sdb1/media /backupDisc/backupDir
```
Wich takes "directory\", "name\", "with\" and "spaces\" as parameters.
[*]**Example Case 3:**
```
#!/bin/bash

# Local dirs
dirs=(
# array position 1:
"/media/sdb1/academic"

# array position 2:
"/media/sdb1/archivos recibidos"

# array position 3
#here's my problem
"--exclude 'direcory name with spaces' /media/sdb1/media"
)

backupDiscDir=/backupDisc/backupDir

for ((i=0;i<${#dirs[]};i+=1)); do
echo ""
echo ""
echo "rsync -avz -n --delete -u "${directorios[i]}" $backupDiscDir"
rsync -avz -n --delete  -u "${directorios[i]}" $backupDiscDir
done
```
The result in the command generated is:```

rsync -avz -n --delete  -u --exclude direcory name with spaces /media/sdb1/media /backupDisc/backupDir
```
But with this method, (--exclude direcory name with spaces /media/sdb1/media) is taken like an argument and outputs as an error too...
[/LIST]



**Bottom line...**

I've tried a couple of other methods but they haven't worked either, so, for my troubleing line, I want to be able to escape some spaces, not all. From this line:
```
"--exclude 'direcory name with spaces' /media/sdb1/media"
```
I want to be able to escape spaces between directory-name, name-with, and finally with-spaces.

I want to do this because the script would be very easily maintained in case I need it to backup a very long list of directories.


I'm guessing this is a problem with a very simple solution so any help will be very apreciated.

Cheers,
techflat

---

### Post by stroyan on 2009-02-20
Use eval to evaluate the quotes in your array element.
The eval will repeat the evaluation of the quoting after variable expansion.
```

$ cat args.sh
#!/bin/bash
for a in "$@"
do
echo $a
done
$ l=( one two "two and a half" three "--exclude 'a directory name with spaces' /media/sdb1/media" )
$ for ((i=0;i<${#l[*]};i+=1)); do ./args.sh "${l[$i]}"; done
one
two
two and a half
three
--exclude 'a directory name with spaces' /media/sdb1/media
$ for ((i=0;i<${#l[*]};i+=1)); do eval ./args.sh "${l[$i]}"; done
one
two
two
and
a
half
three
--exclude
a directory name with spaces
/media/sdb1/media

```
You do have to be aware that the eval could interpret other strings in your command twice.  Notice what happens if you add "$RANDOM" to the array.
```

$ l=( "$RANDOM" "$RANDOM" )
$ for ((i=0;i<${#l[*]};i+=1)); do eval ./args.sh "${l[$i]}"; done
21301
19085

```

---

### Post by techflat on 2009-02-21
Hey there stroyan,

Thanks for your reply. It worked greatly!! I didn't know the eval command, very useful, I didn't think doing what it does was possible.

However, I'm a little confused with the last part of your message, could you please elaborate on that?

> **stroyan said:**
> 
(...)
You do have to be aware that the eval could interpret other strings in your command twice.  Notice what happens if you add "$RANDOM" to the array.
```

$ l=( "$RANDOM" "$RANDOM" )
$ for ((i=0;i<${#l[*]};i+=1)); do eval ./args.sh "${l[$i]}"; done
21301
19085

```

Cheers,
techflat

---

### Post by techflat on 2009-02-21
Here's my script, basic but useful, so it can be used and viewed by whoever needs it:

```
#!/bin/bash

## This script is intendet to do a backup of the directories listed inside the array dirs
## 
## Note that if directories with white spaces in them will be listed they should quoted in single quotes ( ' )

# Directories to be backed up
# If other directories should be backed up to, add another line to the $dirs array
# Change the list to whatever your needs are
dirs=(
"/media/sdb1/academic"
"'/media/sdb1/archivos recibidos'"
"--exclude 'backupsImportantes/macbook/rsync/Music' --exclude 'backupsImportantes/macbook/rsync/Parallels' /media/sdb1/backups"
"/media/sdb1/desarrollo"
"/media/sdb1/documentos"
"--exclude 'por sumar a tunes' --exclude 'Tunes' --exclude 'libros' --exclude 'video/miro' /media/sdb1/media"
)

# Backup dir
backupDiscDir=/media/disk/backup


case $1 in

"D" )
for ((i=0;i<${#dirs[*]};i+=1)); do
echo ""
echo ""
string="rsync -avz --delete --delete-excluded -u ${dirs[i]} $backupDiscDir"
echo $string
eval $string > log.log
done
;;

"K" )
for ((i=0;i<${#dirs[*]};i+=1)); do
echo ""
echo ""
string="rsync -avz -u ${dirs[i]} $backupDiscDir"
echo $string
eval $string > log.log
done
;;

* )
echo ""
echo "Usage"
echo "backup.sh [ D | K ]"
echo ""
echo "D = delete, this means that the backup will remove files that are on the backup drive but not on the directory being backed up"
echo "K = keep files, this means that the backup will not remove files that are on the backup drive but not on the directory being backed up"
;;

esac
```

---

### Post by stroyan on 2009-02-21
> **techflat said:**
> 
However, I'm a little confused with the last part of your message, could you please elaborate on that?

The eval operation will evaluate more than just quotes.
It will evaluate other shell expansions that could have unexpected side effects.
I got the quoting wrong in my first example, ruining the point I wanted to make.
Here is a more interesting example.
```

$ l=( '$RANDOM' "one 'and another'" '$RANDOM' )
$ for ((i=0;i<${#l[*]};i+=1)); do ./args.sh "${l[$i]}"; done
$RANDOM
one 'and another'
$RANDOM
$ for ((i=0;i<${#l[*]};i+=1)); do eval ./args.sh "${l[$i]}"; done
2017
one
and another
523
$ for ((i=0;i<${#l[*]};i+=1)); do eval ./args.sh "${l[$i]}"; done
15872
one
and another
28189

```
The values of '$RANDOM" appear as array elements as the shell variable name.
They are then expanded by the eval operation.
A more troublesome effect would be caused by strings containing $() or `` backquotes.
That could execute arbitrary commands if the string data contained such shell expressions.
Those troubles won't come up if you know your data has simple strings that don't have special meaning to the shell.

---

### Post by techflat on 2009-02-21
OK. Thanks for your help.

Cheers,
techflat

---

### Post by geirha on 2009-02-22
With your original code, making the array like this should work:
```

dirs=(
"/media/sdb1/academic"
"/media/sdb1/archivos recibidos"
"--exclude=backupsImportantes/macbook/rsync/Music" 
"--exclude=backupsImportantes/macbook/rsync/Parallels" 
"/media/sdb1/backups"
"/media/sdb1/desarrollo"
"/media/sdb1/documentos"
"--exclude=por sumar a tunes" 
"--exclude=Tunes" 
"--exclude=libros"
"--exclude=video/miro" 
"/media/sdb1/media"
)

```

EDIT: Err wait, you are running several rsync commands, not one. I see the actual problem now. Sorry for my useless post.

---

### Post by techflat on 2009-02-23
> **geirha said:**
> With your original code, making the array like this should work:
```

dirs=(
"/media/sdb1/academic"
"/media/sdb1/archivos recibidos"
"--exclude=backupsImportantes/macbook/rsync/Music" 
"--exclude=backupsImportantes/macbook/rsync/Parallels" 
"/media/sdb1/backups"
"/media/sdb1/desarrollo"
"/media/sdb1/documentos"
"--exclude=por sumar a tunes" 
"--exclude=Tunes" 
"--exclude=libros"
"--exclude=video/miro" 
"/media/sdb1/media"
)

```

EDIT: Err wait, you are running several rsync commands, not one. I see the actual problem now. Sorry for my useless post.

Hey there, just received this in my mail... I was going to tell you that it wouldn't work... but I hadn't seen the edit... :o

Cheers,
techflat

---


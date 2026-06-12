---
title: "[SOLVED] [BASH] Replace spaces with a character in file names"
date: 2008-09-17
forum: Programming Talk
---

### Post by PurposeOfReason on 2008-09-17
How would I go about making a bash script to replace a space in the file name (great song.flac) with a period or underscore?

---

### Post by ghostdog74 on 2008-09-17
in bash
```

# s="great song.flac"
# echo ${s/ //}
great/song.flac
# echo ${s/ /}
greatsong.flac
# echo ${s// /}
greatsong.flac

```

other ways
```

# echo $s | tr -d " "
greatsong.flac
# echo $s | sed 's/ *//g'
greatsong.flac
# echo $s | awk '{$1=$1}1' OFS=""
greatsong.flac

```

for a tool to do more, you can use the file rename scripts [here](http://www.linuxquestions.org/linux/blog/ghostdog74)

---

### Post by PurposeOfReason on 2008-09-17
Thanks. Do you by any chance know of a site that can walk me through the basics of bash scripting?

---

### Post by decoherence on 2008-09-17
```

#!/bin/bash

mv "$1" `echo $1 | sed 's/ /_/g'`
```

make it executable then run it like
```

command *filename*
```

NB: this command is potentially destructive. If you have the file "free bird - lynard skynard.mp3" studio recording and also have a wicked live version that happens to be called "free_bird_-_lynard_skynard.mp3" then running this command on "free bird - lynard skynard.mp3" will result in the loss of your wicked live recording! NOOOO!! When using simple one-liners, beware of naming conflicts. See post below.

---

### Post by stroyan on 2008-09-17
You should be careful about letting a script loose on your files.
You need to consider what it might do wrong.  For example, what
should it do if the new name is already in use by another file
or directory?  Here is an example that checks for existing files.
When developing something like this it is good to try it out in
a test directory first.  And you can replace a command like "mv"
with "echo mv" to just print out what it will do before really
using it.

```

#!/bin/bash
for f in *
do
  new="${f// /_}"
  if [ "$new" != "$f" ]
  then
    if [ -e "$new" ]
    then
      echo not renaming \""$f"\" because \""$new"\" already exists
    else
      echo moving "$f" to "$new"
      mv "$f" "$new"
    fi
  fi
done

```

---

### Post by stroyan on 2008-09-17
> **PurposeOfReason said:**
> Thanks. Do you by any chance know of a site that can walk me through the basics of bash scripting?

The "Advanced Bash-Scripting Guide" at [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
actually starts with the basics of bash scripting.
(It just goes much farther than the basics.)

---


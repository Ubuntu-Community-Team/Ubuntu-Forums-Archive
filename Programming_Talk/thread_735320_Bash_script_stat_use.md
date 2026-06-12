---
title: "Bash script: stat use?"
date: 2008-03-25
forum: Programming Talk
---

### Post by EvilMarshmallow on 2008-03-25
I'm trying to write a script and I need to get a file's last modification time.  I can't figure out how to construct the statement I need, which I think is some form of the stat command.

I want only mm/dd/yy hh:mm returned, in 24-hour format.  I must have googled a hundred pages but I can't figure it out, and the man page doesn't explain how to construct the statement (at least not for a noob like me).

Can anyone help?

---

### Post by scragar on 2008-03-25
try:

```
ls -l --time-style=full-iso **filename** | grep -o "[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9] [0-9][0-9]:[0-9][0-9]:[0-9][0-9]"
``` from a terminal. I'll convert this into a simple shell script that can just be run anywhere(I would use the {4} syntax to shorten the code, but for some reason grep for me was hopping between ereg and normal reg methods, which caused problems).

---

### Post by scragar on 2008-03-25
ok, this code works fine from a terminal:
```
#!/bin/bash

ls -l --time-style=full-iso $1 | grep -o "[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9] [0-9][0-9]:[0-9][0-9]:[0-9][0-9]"

sleep 5
```
and you can set it to a right click menu option, launching it using the command:
```
gnome-terminal -x  **PATH TO SCRIPT**
```

---

### Post by WW on 2008-03-25
**stat** can do what you want:
```

stat -t "%D %R" -f "%Sm"  filename

```
(Obvious, right? :) )

---

### Post by EvilMarshmallow on 2008-03-25
I tried the stat example by WW above... I get "cannot read file system informatio nfor '%D %R' and again for '$Sm', then I get the terse version of the stat command.

Does Ubuntu not use the standard implementation of stat?

---

### Post by WW on 2008-03-25
Sorry.  Lately I've been on a Mac more than Ubuntu.  The command I gave above works on the Mac, but the stat command in Ubuntu has very different options.  In the words of the immortal Emily Latella: "Oh.  That's different.  Never mind!"

---

### Post by nanotube on 2008-03-25
well, on ubuntu, the following seems to produce the desired result, e.g.:
```
$ stat -c '%z' .Xauthority 
2008-02-20 20:17:57.000000000 -0500
```

then all you need to do is cut it off where you want by any method you prefer. e.g.:
```
$ expr substr "$(stat -c '%z' .Xauthority)" 1 16
2008-02-20 20:17
```

(obviously substitute in the file you are interested in where you see ".Xauthority")

---

### Post by ghostdog74 on 2008-03-26
-z of stat command is time of last change. Use %y for last modification
```

# stat -c "%y" file | awk 'BEGIN{FS="[ .:]"}{gsub("-","/",$1);}{print $1,$2":"$3}'
2008/03/26 10:34

```

---

### Post by mssever on 2008-03-26
> **scragar said:**
> I would use the {4} syntax to shorten the code, but for some reason grep for me was hopping between ereg and normal reg methods, which caused problems.
Use egrep instead of grep for anything but the most trivial regular expressions.

---

### Post by nanotube on 2008-03-26
> **ghostdog74 said:**
> -z of stat command is time of last change. Use %y for last modification
```

# stat -c "%y" file | awk 'BEGIN{FS="[ .:]"}{gsub("-","/",$1);}{print $1,$2":"$3}'
2008/03/26 10:34

```

nice awk use. now... where i come from, modification is just a synonym for change. :) while i was man-ing stat, i saw the two options, but had no clue why there were two different ones so just picked one. so could you please enlighten me what the difference between the two is, in the context of stat?

---

### Post by ghostdog74 on 2008-03-26
> **nanotube said:**
> nice awk use. now... where i come from, modification is just a synonym for change. :) while i was man-ing stat, i saw the two options, but had no clue why there were two different ones so just picked one. so could you please enlighten me what the difference between the two is, in the context of stat?

meta-data such as owner, group etc are stored in the inode. when you do chmod, chown etc on a file, you modify its last change time.  when you change the actual  data of the file itself, you changed its modification time.

---

### Post by nanotube on 2008-03-28
> **ghostdog74 said:**
> meta-data such as owner, group etc are stored in the inode. when you do chmod, chown etc on a file, you modify its last change time.  when you change the actual  data of the file itself, you changed its modification time.

thanks, that was useful info! :)

---


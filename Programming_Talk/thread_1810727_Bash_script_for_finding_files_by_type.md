---
title: "Bash script for finding files by type"
date: 2011-07-23
forum: Programming Talk
---

### Post by masamunedark on 2011-07-23
Hello all,

First, I am not experienced in scripting, so be gentle with me :D

Anyway, I tried making a script for finding files by type ( audio, video, text...etc), and here's the poor result I came up with.

```
#!/bin/bash

FINDPATH="$1"
FILETYPE="$2"


locate $FINDPATH* | while read FILEPROCESS

do

   if  file -bi "$FILEPROCESS" | grep -q "$FILETYPE" 
   then 
      echo $FILEPROCESS
   fi
 
done
```It works, but as you could guess, the performance is not so good.

So, can you guys help me make it better ? and also, I don't want to rely on files extensions.

---

### Post by AlphaLexman on 2011-07-23
Maybe you should squeeze 'awk' in the middle, like this...
```
file -bi * | awk '{print $1}' | grep "text/" | sort | uniq -c
```
Although not quite perfected to your variable names, it might get you going in another direction!

---

### Post by masamunedark on 2011-07-23
Thanks for the tip :)

Right now this is how I am doing it, it's a bit faster

```
#!/bin/bash

FINDPATH="$1"

find "$FINDPATH" -type f | file -i -F "::" -f - | awk -v FILETYPE="$2"  -F"::" '$2 ~ FILETYPE { print $1 }'
```

---

### Post by AlphaLexman on 2011-07-23
> **masamunedark said:**
> Thanks for the tip :)

Right now this is how I am doing it, it's a bit faster

```
#!/bin/bash

FINDPATH="$1"

find $FINDPATH* -type f | file -i -F "::" -f - | awk -v FILETYPE="$2"  -F"::" '$2 ~ FILETYPE { print $1 }'
```

I understand you are trying to test files vs. file-types...

You might want to tackle one problem at a time...

But from a debugging point-of-view, you should solve your script to the current directory, then expand the script to include sub-directories.

First, get the information you want from the current directory, then get the information from recursive sub-directories. Don't try to solve two problems at once.

It seems to me that you are struggling with the $FINDPATH variable before you have solved the $FILETYPE code.

Work on getting the script/code to work for the current directory, then modify the code for recursive sub-directories.

Good Luck!

---

### Post by masamunedark on 2011-07-25
Thanks, I'll keep that in mind.

---


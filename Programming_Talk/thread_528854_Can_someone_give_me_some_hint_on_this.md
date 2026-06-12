---
title: "Can someone give me some hint on this?"
date: 2007-08-18
forum: Programming Talk
---

### Post by kurt_issac on 2007-08-18
Im still new in learning bash script. I want to write a moving file script,

For example,

move a.txt b.txt

I want to modified the mv command. Instead of overwrite the b.txt, i want to make the new file as b.txt.1

So when i type move a.txt b.txt, a.txt will change to b.txt.1 if b.txt exist. And if b.txt.1 already exist, the a.txt will change to b.txt.2 instead. So the previous b.txt will not be overwritten.

How can i do this?

---

### Post by cwaldbieser on 2007-08-18
> **kurt_issac said:**
> Im still new in learning bash script. I want to write a moving file script,

For example,

move a.txt b.txt

I want to modified the mv command. Instead of overwrite the b.txt, i want to make the new file as b.txt.1

So when i type move a.txt b.txt, a.txt will change to b.txt.1 if b.txt exist. And if b.txt.1 already exist, the a.txt will change to b.txt.2 instead. So the previous b.txt will not be overwritten.

How can i do this?

You could start by making a script that does what you want:
1) Check if target name exists.
2) If target name exists, create new target name based on source name and running number.  Goto step 1.
3) Do the move.

```

#! /bin/bash

SRC="$1";
DST="$2";
i=0;

while [ -e "$DST" ] ; do
    i=$((i+1));
    DST="$SRC.$i";
done

mv "$SRC" "$DST";

```

If you name your script something like "mv2" and then set its permissions to be executable, you can run it.  You probably want to put it somewhere in your local PATH.  You could give yourself an alias so that the real mv command is now youe script (e.g. alias mv=/home/username/bin/mv2).

---

### Post by Chaotic Thought on 2007-08-18
The default **mv** command already includes an option very similar to what the OP wants, although not precisely the same. Example:

```
mv --backup=numbered source destination
```

If **destination** already exists, it will first be renamed with an extension **.~1~** (or the next available number).

If you want this to be the default behavior in your shell, use an alias:

```
alias mv='mv --backup=numbered'
```

Put it in your **.bashrc** and it will be the default when you start an interactive session of bash.

---

### Post by kurt_issac on 2007-08-18
Thank you very much!

---

### Post by kucai on 2007-08-26
I really love this post !

---


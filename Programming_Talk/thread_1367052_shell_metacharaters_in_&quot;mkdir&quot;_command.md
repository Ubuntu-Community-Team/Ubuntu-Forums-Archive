---
title: "shell metacharaters in &quot;mkdir&quot; command"
date: 2009-12-29
forum: Programming Talk
---

### Post by piyush.neo on 2009-12-29
i have something interesting to share...when i give command in terminal(BASH shell)
[B]mkdir chap[1-9]
[/B]a directory named chap[1-9] is created..
after that i created 2 more dir
[B]mkdir chap1 chap2
[/B]now when i am trying to create 
**mkdir chap[1-5]**
its giving error
[B]mkdir: cannot create directory `chap1': File exists
mkdir: cannot create directory `chap2': File exists
[/B]why is it not creating the dir named **chap[1-5]** or if it is showing error for** chap1** and **chap2 **why it is not creating **chap3 chap4 **and **chap5**...
:confused::confused:

---

### Post by ghostdog74 on 2009-12-29
use brace expansion
```

mkdir chap{1..5}

```

---

### Post by lloyd_b on 2009-12-29
> **piyush.neo said:**
> i have something interesting to share...when i give command in terminal(BASH shell)
[B]mkdir chap[1-9]
[/B]a directory named chap[1-9] is created..
after that i created 2 more dir
[B]mkdir chap1 chap2
[/B]now when i am trying to create 
**mkdir chap[1-5]**
its giving error
[B]mkdir: cannot create directory `chap1': File exists
mkdir: cannot create directory `chap2': File exists
[/B]why is it not creating the dir named **chap[1-5]** or if it is showing error for** chap1** and **chap2 **why it is not creating **chap3 chap4 **and **chap5**...
:confused::confused:

Hmmm - that's a funny one.

What's happening is that the [1-9] is a bash pattern match.  So "chap[1-9]" will match the letters "chap" followed by any number from 1 to 9.  Apparently, when you type "mkdir chap[1-9]", the shell attempts to perform shell expansion on the pattern, which will return "chap1" and "chap2" if they exist.  But, of course, since they exist, you can't mkdir them.  If no files are matched by the pattern, then the literal "chap[1-9]" is passed to "mkdir", and it creates a directory by that name.

If you actually need to create a directory named "chap[1-5]" in a directory that has "chap1", you'll need to enclose the argument to mkdir in quotation marks to block the shell expansion:```
mkdir "chap[1-5]"
```

Lloyd B.

---

### Post by piyush.neo on 2009-12-29
thanks a lot .......:guitar:

---

### Post by dwhitney67 on 2009-12-29
You can also use the -p option with mkdir to ignore cases where the directory already exists, and it can create the parent directory should it not exist.

So:
```

mkdir chap1
mkdir -p chap{1..5}    # will not produce an error for chap1
mkdir -p chap6/pg1     # will create chap6 and pg1 directories

```

---


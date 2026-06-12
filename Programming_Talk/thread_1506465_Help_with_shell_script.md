---
title: "Help with shell script"
date: 2010-06-10
forum: Programming Talk
---

### Post by smitty92 on 2010-06-10
ok so i made a shell script that copys some files and i would like to know how to make it show me what it is coping, right now all it does is tell me when its done, i would like to see the actual copying process if thats possible
also id like it to check and see if it has enough room if thats possible with a script,
command is just simply cp -n -r (dir) (destination)

---

### Post by geirha on 2010-06-10
Add the -v option to cp, and cp will tell you what it's doing. 

Checking if there is enough space is not bullet-proof. You might have enough space before you start copying, but some other program may be using up space while the copy is going on and you end up with a full filesystem anyway. Then again, if there's not enough space to start with, there's no point in beginning the copy, so this may give you some clues: [http://mywiki.wooledge.org/BashFAQ/094](http://mywiki.wooledge.org/BashFAQ/094)

---

### Post by conundrumx on 2010-06-10
Put
```

set -x

```
After the shebang (or before any commands you want to see.)

---

### Post by jimhenry on 2010-06-10
> **conundrumx said:**
> Put
```

set -x

```After the shebang (or before any commands you want to see.)

For debugging a shell script, I generally put 

```

set -xv

```at the beginning and

```

set +xv

```at the end -- if you leave off the latter, you'll still have the x and v verbosity options turned on while you're in interactive mode when the script is done, which is usually not what you want.  But that's not a substitute for giving the -v (verbose) option to various commands the shell script is calling in turn.

---


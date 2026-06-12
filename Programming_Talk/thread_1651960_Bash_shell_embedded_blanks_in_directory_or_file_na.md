---
title: "Bash shell embedded blanks in directory or file names"
date: 2010-12-24
forum: Programming Talk
---

### Post by rhdinah on 2010-12-24
Given a directory on the Desktop named **"A B"** ... embedded blank in the name.

and a +x script named **lsl** in the home directory:

```
#!/bin/bash
DIR="~/Desktop/A B"
ls -d ~/Desktop/A\ B
ls -d $DIR

```

when the script is invoked the following is observed:

```
me@machine:~$ ./lsl
/home/me/Desktop/A B
ls: cannot access ~/Desktop/A: No such file or directory
ls: cannot access B: No such file or directory
me@machine:~$
```

Normally on the CL you escape out the space, but how do you accomplish such a thing within a script using variables.

You can try to escape out the blank in the variable assignment but nothing comes of it. So basically how is this done with variables? :D

Actually it's pretty embarrassing to ask this, but I've been working on it for hours.

I can't find much on the Internet other than embedded blank file traversing iterations which is really not what I need.

Thanks!

---

### Post by Vox754 on 2010-12-24
> **rhdinah said:**
> Given a directory on the Desktop named **"A B"** ... embedded blank in the name.


Use double quotes
```

ls -d "$DIR"

```

Embedded blanks?

Search for "filename with spaces". It's more straight-forward.

---

### Post by rhdinah on 2010-12-24
> **Vox754 said:**
> Use double quotes
```

ls -d "$DIR"

```

Embedded blanks?

Search for "filename with spaces". It's more straight-forward.

Thanks for your fast reply, but sorry that does ***NOT*** work! LOL!

---

### Post by Vox754 on 2010-12-24
> **rhdinah said:**
> Thanks for your fast reply, but sorry that does ***NOT*** work! LOL!

*Sigh*

It does work, there is a different issue though.

For your variable, the doubles quotes prevent expansion of the tilde, it seems.

```

# do this
DIR=~/Desktop/"A B"

# you can also use this environmental variable
DIR="${HOME}/Desktop/A B"

```

---

### Post by rhdinah on 2010-12-24
> **Vox754 said:**
> *Sigh*

It does work, there is a different issue though.

For your variable, the doubles quotes prevent expansion of the tilde, it seems.

```

# do this
DIR=~/Desktop/"A B"

# you can also use this environmental variable
DIR="${HOME}/Desktop/A B"

```

Thanks for spotting that! Now I wonder if that is a bug in the shell? This problem has been a real hair puller for me! Thanks for the help!

---

### Post by Vox754 on 2010-12-24
> **rhdinah said:**
> Thanks for spotting that! Now I wonder if that is a bug in the shell? This problem has been a real hair puller for me! Thanks for the help!

Lol no. It is not a bug, it is a "known fact", that is, documented in the 200-page bash manual.

```

man bash

```

Search for "tilde".

Quotes also prevent expansion of other characters such as * and ?

By the way, I recommend using $HOME instead of the tilde, to avoid these issues, and also because it's more explicit.

---


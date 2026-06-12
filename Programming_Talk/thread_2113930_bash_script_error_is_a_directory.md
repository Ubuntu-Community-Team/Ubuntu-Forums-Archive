---
title: "bash script error: is a directory"
date: 2013-02-08
forum: Programming Talk
---

### Post by oleink on 2013-02-08
My code is rather basic so excuse my lack of shell scripting experience. I keep getting errors for line 3. I have tried changing "$1" to echo $1 cat $1 and even turning the whole line into a variable which i read in another forum and then calling that variable seperately (the variable being inside of backquotes. It's giving me headaches seems like it should be simple. The goal is to make all .sh files rwx and to allow the user to pass an argument directory into the script so that it will change them in a specific directory rather than globally.

The worst part is this runs perfectly fine (without if statement obviously) going line by line in the shell but the sub shell that is reading the bash script is apparently having a hard time with what to do with directory that I am trying to pass into the find command (it apparently thinks I am trying to execute it)

Here is my code:

```
#!/bin/bash
if $1 ; then
    find $1 -name "*.sh" > temp.txt
else
    find /home -name "*.sh" > temp.txt
fi
sudo chmod 770 `cat temp.txt`
```


> Here is a full output of the error:

jordan@fire:~$ ./test.sh ~/documents ./test.sh: line 6: /home/jordan/documents: is a directory find:/home/accounts': Permission denied

(Just so you know.  I am cross forum posting.  I posted this same thing on daniweb.  I dont know why people have a problem with cross posting on multiple forums that are different but I am looking for help from coders and from other linux users so I posted both places)

---

### Post by schragge on 2013-02-08
Already answered [post=12499384]there[/post].

---

### Post by oleink on 2013-02-08
> **schragge said:**
> Already answered [post=12499384]there[/post].

Thanks I thought I had closed it before any replies.

> **schragge said:**
> Well, this ```
if $1; then
``` should be
```
if [ -d "$1" ]; then
```
But you also can execute any command as an action in *find*.
```

find /some/directory -name "*.sh" -exec chmod 770 {} \+

```


Here is the solution for anyone else who may run into this problem.  Thanks schragge for your help.  (I feel like a noob lol)):P

---

### Post by schragge on 2013-02-09
After giving it some more thought, I'd rewrite your script this way
```

#!/bin/sh
exec find ${1:-/home} -name \*.sh -exec sudo chmod 770 {} +

```
Alternatively, it could be done as a shell function defined in *~/.bashrc* or some other shell start-up file
```

mkshx(){ find ${1:-/home} -name \*.sh -exec sudo chmod 770 {} +;}

```

---

### Post by oleink on 2013-02-21
> **schragge said:**
> After giving it some more thought, I'd rewrite your script this way
```

#!/bin/sh
exec find ${1:-/home} -name '*.sh' -exec sudo chmod 770 {} +

```
Alternatively, it could be done as a shell function defined in *~/.bashrc* or some other shell start-up file
```

mkshx() find ${1:-/home} -name '*.sh' -exec sudo chmod 770 {} +

```


I ended up with this before I finished everything.  Thought it was just as simple as the above code.  Any of these work great though! thanks again
```

#!/bin/bash

	find $1 -name "*.$2" | xargs -n 1 chmod 770 

```

---


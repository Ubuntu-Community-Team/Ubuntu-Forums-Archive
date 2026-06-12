---
title: "special issue on command line arguments"
date: 2010-10-31
forum: Programming Talk
---

### Post by idiolatrie on 2010-10-31
Hi,

I'm trying to write a program with the following execution scheme:

myprog "./myprog \"ps aux\" \"sort -n\"" "head -10"

so that each of these commands runs as its own process. 
It's no big deal to parse the "head -10" argument and execute it via execlp, but
however the first argument is a little bit tricky.

Do I have to write some sort of special parser, or is there some preexisting routine?

Mathias

---

### Post by mainerror on 2010-10-31
What exactly is the problem? The double-quote escaping? If that's the case you might want to use single-quotes as your outer quote, then you can use double-quotes inside them without having to escape them.

---

### Post by trent.josephsen on 2010-10-31
Quotes, spaces, and backslashes will be interpreted by the shell.  execlp isn't a shell.  That means, if you persist in using it, you will have to handle those things yourself.  E.g.
```
./myprog './myprog "ls -Al" "df -h"'
```
Unless you write your own code to group things in quotes, this will probably end up executing
```
./myprog \"ls -Al\" \"df -h\"
```

system() calls a shell, which can interpret the quotes, but you don't necessarily know which shell it is all the time, so you want to be careful with it.

---

### Post by Reiger on 2010-10-31
Hmm this sort of thing looks easier to do in sh:

```

#!/bin/sh

create_script() {
  for i in "$@"
  do
    echo $i
  done
}

create_script "$@" | sh
exit $?

```

Test:
```

> ./test 't="hello world"; echo "$t"' 'echo "test this too"'
hello world
test this too

```

---

### Post by idiolatrie on 2010-10-31
Thx alot,

since this is some sort of homework for my OS class I'm limited to C and not allowed to use either popen or system.
The original task is to emulate[INDENT]ps aux | sort -n | head -10

[/INDENT]in C. I thought of creating a program that takes 2 commands and their options and runs them. And then I take my own program with another 2 parameters as argument 1 as stated above. Now I can simulate 2 pipes with a program that does implement only one. 
For execvp I need to convert ./myprog "ps aux" "sort -n" into an argv[] and hoped that there is some function that takes such a string and then converts it just like the shell does.

Or I just implement 2 pipes within my program, but that's lame, isn't it? :)

Thanks,
Mathias

---


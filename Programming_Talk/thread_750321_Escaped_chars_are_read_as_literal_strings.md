---
title: "Escaped chars are read as literal strings"
date: 2008-04-09
forum: Programming Talk
---

### Post by saphil on 2008-04-09
I have a script example that worked with echo and line returns, and I thought I understood the mechanism by which the line return characters are parsed in Bash

I had a shellscript adapted from arachnoid.com that basically puts items in order.
```
#!/bin/bash

echo "Dinosaur Bird Porcupine" | tr " " "\n" | sort
```
This produces a proper output...

```
wolf@prospero:~/Documents/Shellscripting$ ls
helloworld.sh               locate.sh       sorting.sh
wolf@prospero:~/Documents/Shellscripting$ /bin/bash sorting.sh
Bird
Dinosaur
Porcupine

```
Maybe it was just the tr command working.  

...but this one doesn't work
```
#!/bin/bash
        echo "\"Hello World\"" '\n' '\n' '\a'

# I expect to produce the literal term "Hello World" then 2 line returns and a beep
# what I get is "Hello World" \n \n \a
# The escaped characters are not doing what I expect.  This has failed identically
#in terminal emulators on Knoppix, Fedora 7 and Ubuntu 8.4
```  I have tried single and double quotes, which I understand to be almost identical in behaviour, and neither of which make the escaped a and n do anything.

---

### Post by mike_g on 2008-04-09
I don't knwo anything about bash so i'm pretty clueless here, but have you tried:
```
echo "\"Hello World\"\n\n\a"
```
?

edit: no, I just tried it and it wont work :(

---

### Post by WW on 2008-04-09
Use the **-e** option to echo:
> 
$ echo 'ABC\nDEF'
ABC\nDEF
$ echo -e 'ABC\nDEF'
ABC
DEF
$ 


---

### Post by saphil on 2008-04-15
Thanks,
After trying this it occurred to me to try the --help option to see what else echo could do.  So I typed in ```
wolf@prospero:~$ echo --help 
--help

```Duh!
man echo helped too because it reminded me about the manual about all core utilities 
```
wolf@prospero:~$  info coreutils &#8217;echo invocation&#8217;

```and so finally I wrote a copy of that to a file to read when I am not near the computer
```
info coreutils >> info_coreutils.txt
```

Oops.. That last one produced a file in Chinese.  I don't know what happened there...

---


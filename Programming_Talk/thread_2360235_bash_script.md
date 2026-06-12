---
title: "bash script"
date: 2017-05-02
forum: Programming Talk
---

### Post by hesus-red-hand on 2017-05-02
Hi,

I need to make a bash script for school and have been trying to figure out how to go around with this but until this point i am clueless on how to start it. I have no knowledge of scripting what so ever so i have been trying to look for clues and other useful tips and tricks on the internet. This might probably be an easy task for the most of you. :)

description of what the script should do :

I have to write a script that needs to read an entire filename like /usr/local/squid/bin/squid for example. The script needs to give the message "This is an executable file in an existing directory" if the directory part of the file path exists and if the file is executable.

I think i need to split the path somewhere and i know i should be able to do this with dirname and basename.

This is what i have so far but it does fail so actually i still have nothing :)

echo -n "Give the path of the file : "
read $file

DIRNAME=$file
BASENAME=$file

if [[ -x "$BASENAME" ]] && [[ -d "$DIRNAME" ]];
       then
             echo "The file is executable and is in an existing directory"
fi

Any help on this is very appreciated.

---

### Post by steeldriver on 2017-05-02
You're thinking along the right lines, however:

1. in bash shell syntax (unlike perl or php for example), the $ is only used when de-referenceing vairables - not when assigning to them. So
```

echo -n "Give the path of the file : "
read $file

```

should just be
```

echo -n "Give the path of the file : "
read file

```

In fact, bash has a form of its built-in read command that allows you to echo a prompt string directly, so a neater way to do this would be

```

read -p 'Give the path of the file: ' fname

```

2. You seem to be familiar with the concepts 'dirname' and 'basename' but if you want to use them you need to call the actual command and substitute the results e.g.

```

DIRNAME=$(dirname $file)
BASENAME=$(basename $file)

```

HOWEVER you should always quote expansions like $file in case they contain whitespace. Also (as a matter of style rather than functionality) you should avoid ALL-CAPS variable names as these are informally reserved for system variables. So let's make that something like:
```

dname=$(dirname "$fname")
bname=$(basename "$fname")

```

Finally, your test
```

[[ -x "$BASENAME" ]]

```
is going to fail unless the file is in the current directory (the -x test doesn't search your PATH) - you need to do the test on the fully-qualified path (so in fact you don't need `basename` at all).

Putting it all together:
```

#!/bin/bash

read -p 'Give the path of the file: ' fname

dname=$(dirname "$fname")

if [[ -x "$fname" ]] && [[ -d "$dname" ]]; then
  echo "The file is executable and is in an existing directory"
fi

```

Of course the [[ -d "$dname" ]] test is superfluous in this context since if the fully-qualified file is executable, it must be in an existing directory - so all you really need to do is

```

#!/bin/bash

read -p 'Give the path of the file: ' fname

if [[ -x "$fname" ]]; then
  echo "The file is executable and is in an existing directory"
fi

```

or even

```

#!/bin/bash

read -p 'Give the path of the file: ' fname

[[ -x "$fname" ]] && echo "The file is executable and is in an existing directory"

```

---

### Post by hesus-red-hand on 2017-05-03
Thank you so much this helped me a lot.

---

### Post by howefield on 2017-05-03
Thread moved to the "*Programming Talk*" forum.

---


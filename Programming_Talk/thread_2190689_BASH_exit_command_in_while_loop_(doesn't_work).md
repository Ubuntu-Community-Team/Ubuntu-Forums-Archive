---
title: "BASH: exit command in while loop (doesn't work?)"
date: 2013-11-28
forum: Programming Talk
---

### Post by sha1sum on 2013-11-28
Here is the problem I have:

Say we have a the file instruments.txt
```

guitar
piano
violin
cello
trumpet
ukelele

```


Now we do the following

```
#!/bin/bash

cat instruments.txt | while read; do
if [[ $REPLY =~ trumpet ]]; then
    echo "trumpet is not a stringed instrument!"
    exit 1
else
    echo $REPLY
fi
done

echo "All are stringed instruments" # last line of the program

```

I expected that upon reading the line "trumpet", the program would exit. So the output should look like this:
```
guitar
piano
violin
cello
trumpet is not a stringed instrument!

```

However, the output I get is the following

```
guitar
piano
violin
cello
trumpet is not a stringed instrument!
All are stringed instruments
```

So what seems to happen is that the exit command doesn't exit the program, but only the loop. After that, the rest of the program is still executed.

How can I make the exit command exit the entire program?

---

### Post by sha1sum on 2013-11-28
Maybe worth mentioning that I could work around it by doing the following:

```
#!/bin/bash

varex=

cat instruments.txt | while read; do
if [[ $REPLY =~ trumpet ]]; then
    echo "trumpet is not a stringed instrument!"
    varex=1
    exit 1
else
    echo $REPLY
fi
done

if [[ -n varex ]]; then
exit
fi

echo "All are stringed instruments"


```

Then it does work properly, but I don't really consider that a solution, but rather an ugly work-around. The exit command is behaving like the break command, which is not what I want it to do.

---

### Post by steeldriver on 2013-11-28
Is the catch that, by piping into the while loop from a cat command you are implicitly spawning a subshell, and it is *that* shell that is being exited? How about

```

while read; do
if [[ $REPLY =~ trumpet ]]; then
    echo "trumpet is not a stringed instrument!"
    exit 1
else
    echo $REPLY
fi
done **< instruments.txt**

```

---

### Post by sha1sum on 2013-11-28
EDIT: I tried that and it works. Thanks!

I also think that it's some kind of subshell being exited instead of the entire program.

EDIT2: This solution also works on the bigger program I was writing (the one with the musical instruments was purely for illustration), so I'm out of the woods for now. :D

I'm leaving the topic open to see if somebody has another way of fixing it. There has to be a way to exit the program, even if the while-read loop is reading from a pipeline.

---


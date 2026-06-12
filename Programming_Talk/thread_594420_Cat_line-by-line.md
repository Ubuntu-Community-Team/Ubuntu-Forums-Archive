---
title: "Cat line-by-line"
date: 2007-10-28
forum: Programming Talk
---

### Post by kvdbreem on 2007-10-28
I have a question

Let's say we want to go through a file line-by-line

How would I do this?  I've tried it with cat but that only works if the lines have no spaces.  Otherwise, a file whose lines are 

```

hello how are you
i am fine

```

when processed as follows:
```

#!/bin/bash
for i in `cat file`
do
  echo ${i}
done

```

will come out as 

```
hello
how
are
you
i
am
fine
```

---

### Post by ghostdog74 on 2007-10-28
what do you want to do with those lines? I hope its not just echoing them out because you can easily do that with tools like  awk/cat/more/grep/sed....which internally will "loop" over files for you. however, still to do it in bash , you can use the while loop.

```

while read line;
do
  echo $line
done < "file"

```

---

### Post by kvdbreem on 2007-10-28
ghostdog:

Thanks for the tip.  I had a friend actually asking me about this one at work.  I couldn't help very well.  I think he needed it for driving another program using paths or something.

cheers

---

### Post by geirha on 2007-10-28
Read about the $IFS variable in the bash documentation, and try ```
IFS=$'\n'
```

---


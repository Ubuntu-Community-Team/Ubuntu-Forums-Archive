---
title: "How to use Linux find command to find filenames greater than 256 characters"
date: 2015-11-07
forum: Programming Talk
---

### Post by kevdog on 2015-11-07
I'm pretty stuck in how to do this an efficient way.

I want to find all files whose entire path is greater than x amount of characters.  I thought I could do this with the linux find command, however I'm finding out this is a little bit more difficult than I thought.   Any thoughts on an efficient way of doing this?  The directory tree I'm going to recurse through is thousands of files.  I basically want to find the files with names greater than a certain length and them store them in a file.

---

### Post by steeldriver on 2015-11-07
How about

```

find some/path/ -regextype posix-egrep -regex '.{256,}'

```

Not sure it will count as 'efficient' though

---

### Post by kevdog on 2015-11-07
Hmm -- I must have a different version of find than you because this is what I get:

```

find: -regextype: unknown primary or operator



```

So I'm using OS X, I think the equivalent is the following:

find -E some/path/ -regex '.{256,}'

However I get the following:
```

find -E /Users/ -regex '.{256,}'
find: -regex: .{256,}: invalid repetition count(s)

```

---

### Post by steeldriver on 2015-11-07
Sorry - I don't know anything about the OSX implementation, your title specifically said "Linux find"

You would probably be better off asking on a different forum - perhaps [Unix&Linux](http://unix.stackexchange.com/questions) or [askdifferent](http://apple.stackexchange.com/)

---

### Post by kevdog on 2015-11-07
Well googling around I think I found the answer. At least with the regexp version I'm working for I can get regex longer than 255 characters.  So I if change 256 to 255 in your suggestion, the expression works.  I'm not sure why the limitation however it seems to be a very common limitation.

---

### Post by spjackson on 2015-11-08
See also [http://ubuntuforums.org/showthread.php?t=2296705](http://ubuntuforums.org/showthread.php?t=2296705)

---


---
title: "Using grep on to assign variables within a line"
date: 2008-12-23
forum: Programming Talk
---

### Post by editorreilly on 2008-12-23
I've got a file ale.txt' that looks like this:

M20922C01 BF INTV 1	14:38:42:13	14:44:15:29	M20922C01
M20922C01 BF INTV 4	14:44:50:24	15:12:02:04	M20922C01
M20922C01 BF INTV 5	14:44:50:24	15:12:02:04	M20922C01
M20922C01 BF INTV 6	14:44:50:24	15:12:02:04	M20922C01

I want to use grep to assign some of the values in the file a variable.

I am using ```
INPUT=$(cat -v ale.txt | head -1)
``` to assign the variable INPUT to line 1.  

```
echo $INPUT 
M20922C01 BF INTV 1	14:38:42:13	14:44:15:29	M20922C01
```

This is as far as I can get.  What I need to do now is assign 'M20922C01 BF INTV 1' to another variable and the numbers '14:38:42:13' to yet another variable.  

How do I go about using grep to get those variables assigned?  Is grep the best way to go about it?

Thanks in advance for any help.

-Ryan.

---

### Post by mister_pink on 2008-12-23
I wouldn't use grep, although you could. I'd be more inclined to use cut as an easy option, or awk as the more difficult but flexible option. Pipe INPUT through:

cut -d ' ' -f 1

to get the first one.

Edit: Whoops, didn't read carefully enough. But you get the idea! Might need to use awk to get more than one field in a nice way.

---

### Post by editorreilly on 2008-12-23
Thanks.  Cut is exactly what I needed.  You've saved me from a huge headache!

---


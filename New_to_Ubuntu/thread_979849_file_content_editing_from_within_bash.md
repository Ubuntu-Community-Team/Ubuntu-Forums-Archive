---
title: "file content editing from within bash"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by RedList on 2008-11-12
Hello world!

I feel ashamed for even asking this, and didn't have the courage to ask anywhere else.

I already tried looking for answers on the www, but couldn't find an answer I could comprehend.

Basically i have a text file, which is the result of

"ls > list"

What i need to do is remove the double extension at the end of all the file names

"1234567.ex1.ex2" to become "1234567"

Could any kind soul please halp???

:?

Thanks for the reply, solved it!!! :D

ls > listtemp
sed "s/.hgt.zip//" "listtemp" > list

---

### Post by igknighted on 2008-11-12
You can do it in vi pretty easily, but sadly I am not up enough on my vi commands to remember how to do it the fast way.

---

### Post by gollum2000 on 2008-11-12
I think sed it's what you're looking for, it's a stream editor, try "man sed" or google for more info.

---

### Post by andrew.46 on 2008-11-28
Hi,

Did a bit of work on this one before I noticed that you had already solved it to your satisfaction :(. Anyway here is another solution and a quick demonstration of the best way to present such problems / solutions:

```
echo '1234567.ex1.ex2' | \
sed 's/.\{8\}$//g'
```

All this does is remove the last 8 characters of every individual line in a file and will work if your file always has a dot and then three characters x 2 at the end of each line. Just copy and paste it into a terminal and it will make more sense. All you need to do is pipe the input into the command and redirect the output to a file as you have previously done.

All the best,

  Andrew

---


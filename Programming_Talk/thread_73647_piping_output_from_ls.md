---
title: "piping output from ls"
date: 2005-10-09
forum: Programming Talk
---

### Post by test on 2005-10-09
I'm trying to concatentate the, say, 2 most recent recent files in a directory and processes them using grep and whatnot.  So I thought I'd try something like

ls -t | head -n 2 | cat | grep stuff

However, that really work.  Can someone point me in the right direction? 

Thanks!

---

### Post by toojays on 2005-10-09
How about "ls -t | head -n 2 | xargs cat | grep stuff"?

---

### Post by test on 2005-10-09
I tried that, but for some reason it doesn't work.  I get:

ls -t | head -n1 |  xargs cat
cat: test2: No such file or directory


where test2 is the correct file and, of course, it exists.

?

---

### Post by LordHunter317 on 2005-10-10
You don't need cat in the pipeline:```
ls -t | head -2 | xargs grep stuff
```

---

### Post by test on 2005-10-10
I still get an error.

ls -t | head -n1 | xargs grep stuff
grep: test: No such file or directory

If it's of any use, the word 'test' is colour-coded as it would be displayed in the shell - it is not plain text.  It's as if the output text of 'ls' is encoded and it's execution by xargs therefore fails.

even this doesn't work:
ls -t | head -n1 | xargs ls
ls: test: No such file or directory


Thanks

---

### Post by thumper on 2005-10-10
It should be
```
head -1
```not```
head -n1
```

---

### Post by jrib on 2005-10-10
"head -2" is equivalent to "head -n 2"

```
ls -t | head -2 | grep stuff
```

seems to work for me

---

### Post by jerome bettis on 2005-10-10
what is ls -t  ??

i type it and it does the exact same thing as ls without the -t

---

### Post by jrib on 2005-10-10
[QUOTE=jerome bettis]what is ls -t  ??

i type it and it does the exact same thing as ls without the -t[/QUOTE]

"-t     sort by modification time" 

you can check man pages for a quicker answer to questions like these :D

[edit]a really quick way to find out would be: $man ls | grep '\-t '

---

### Post by Nixed0 on 2005-10-10
How about:
```

ls -t | head -n2 | while read line; do cat $line | grep STUFF ;done

```

---

### Post by Nixed0 on 2005-10-10
Do you have spaces in your filenames? Thats the only reason I can see none of these examples working.

---

### Post by test on 2005-10-10
There are no spaces in the file name.  As you can see from the error message, the file name is  'test'.  BTW, if there's some confusion, I'm trying to grep the contents of the files - not the output of ls.

---

### Post by munitras on 2005-10-10
to find the two most recent files in a directory and then grep the contents of those file for a specified string ("stuff" in this example)

try 
```
ls -t | cat | head -2 | xargs grep stuff
```

if you want more or less most recent files change the 'head -n' - as required
if you want to work with oldest files change the 'head -n' to 'tail -n'

an alternative structure would be to do this
```
grep stuff $(ls -t | cat | head -2)
```

mileage may vary depending on which shell you are running. I run bash.

hope it helps

---

### Post by LordHunter317 on 2005-10-10
Given the error is returned by ls, I'm wondering if you have filesystem corruption.  Post the exact output of 'ls', 'ls -t' and the output of your command.

---

### Post by test on 2005-10-10
Thanks for your help everyone.  This isn't working on two of my systems and is working on a third, so I don't think it's  filesystem corruption

Here's a demo output


$ ls
test1  test2

$ls -t
test2  test1

$ cat test1
1

$ cat test2
2

ls -t | cat | head -n2 | xargs grep 1
grep: test2: No such file or directory
grep: test1: No such file or directory

---

### Post by jerome bettis on 2005-10-11
for i in `ls -t | head -n2` ; do cat $i  ; done | grep stuff

---

### Post by munitras on 2005-10-11
Are you sure that you have not had ls aliased in ~/.alias or ~/.bashrc

---

### Post by test on 2005-10-11
OK, munitras was on to something.  I had aliased ls as 

alias ls="ls --color"

and had thought nothing of it. However, --color encodes the output so it's in color.  The correct thing to do is to use 

alias ls="ls --color=auto"

To quote from 'man ls'

"auto   Only use color if standard output is a terminal".  That way when you pipe it the encoding is removed.

Thanks for your help and sorry for such a silly problem.

---

### Post by munitras on 2005-10-11
kewl.
glad it is working now.

---


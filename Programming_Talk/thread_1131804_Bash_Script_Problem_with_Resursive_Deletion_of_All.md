---
title: "Bash Script Problem with Resursive Deletion of All Empty Files"
date: 2009-04-21
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-04-21
Sup fellas, well here is my code:

```

#!/bin/bash

for a in `ls -R`
do
	if !(test -s $a); then
		echo rm $a
	fi
done

```

This are the files/folders I am testing this on:

```

$ ls -aRl
.:
total 20
drwxr-xr-x 4 aaron aaron 4096 2009-04-21 04:11 .
drwxr-xr-x 4 aaron aaron 4096 2009-04-21 02:44 ..
drwxr-xr-x 2 aaron aaron 4096 2009-04-21 01:55 [1-5]
drwxr-xr-x 3 aaron aaron 4096 2009-04-21 04:11 chaat
-rw-r--r-- 1 aaron aaron  526 2009-04-21 03:55 cleaner.sh
-rw-r--r-- 1 aaron aaron    0 2009-04-21 04:11 touchy

./[1-5]:
total 8
drwxr-xr-x 2 aaron aaron 4096 2009-04-21 01:55 .
drwxr-xr-x 4 aaron aaron 4096 2009-04-21 04:11 ..

./chaat:
total 12
drwxr-xr-x 3 aaron aaron 4096 2009-04-21 04:11 .
drwxr-xr-x 4 aaron aaron 4096 2009-04-21 04:11 ..
drwxr-xr-x 2 aaron aaron 4096 2009-04-21 01:56 chutney
-rw-r--r-- 1 aaron aaron    0 2009-04-21 04:11 heythere
-rw-r--r-- 1 aaron aaron    0 2009-04-21 01:56 nole

./chaat/chutney:
total 8
drwxr-xr-x 2 aaron aaron 4096 2009-04-21 01:56 .
drwxr-xr-x 3 aaron aaron 4096 2009-04-21 04:11 ..

```

When I run my script with "bash cleaner.sh" with all the files and folders empty(besides cleaner.sh of course), I get:

```

$ bash cleaner.sh 
rm .:
rm touchy
rm ./[1-5]:
rm ./chaat:
rm chutney
rm heythere
rm nole
rm ./chaat/chutney:

```

Now I put some text in two of the files:
```

$ head touchy 
created by touch touchy command

$ head chaat/heythere 
hey hey hey!!!! -fat al

```

So my filesystem is now like so:
```

$ ls -aRl
.:
total 24
drwxr-xr-x 4 aaron aaron 4096 2009-04-21 04:06 .
drwxr-xr-x 4 aaron aaron 4096 2009-04-21 02:44 ..
drwxr-xr-x 2 aaron aaron 4096 2009-04-21 01:55 [1-5]
drwxr-xr-x 3 aaron aaron 4096 2009-04-21 04:07 chaat
-rw-r--r-- 1 aaron aaron  526 2009-04-21 03:55 cleaner.sh
-rw-r--r-- 1 aaron aaron   32 2009-04-21 04:06 touchy

./[1-5]:
total 8
drwxr-xr-x 2 aaron aaron 4096 2009-04-21 01:55 .
drwxr-xr-x 4 aaron aaron 4096 2009-04-21 04:06 ..

./chaat:
total 16
drwxr-xr-x 3 aaron aaron 4096 2009-04-21 04:07 .
drwxr-xr-x 4 aaron aaron 4096 2009-04-21 04:06 ..
drwxr-xr-x 2 aaron aaron 4096 2009-04-21 01:56 chutney
-rw-r--r-- 1 aaron aaron   24 2009-04-21 04:07 heythere
-rw-r--r-- 1 aaron aaron    0 2009-04-21 01:56 nole

./chaat/chutney:
total 8
drwxr-xr-x 2 aaron aaron 4096 2009-04-21 01:56 .
drwxr-xr-x 3 aaron aaron 4096 2009-04-21 04:07 ..


```

And now when I run my script I get this:

```

rm .:
rm ./[1-5]:
rm ./chaat:
rm chutney
rm heythere
rm nole
rm ./chaat/chutney:

```

The file heythere still get shows up as being removed even though it is not empty... what's the dealio? Any help greatly appreciated and thanks in advance!

---

### Post by odyniec on 2009-04-21
That's because it looks for "heythere" in the current directory, not in "chaat" as you expect it to. Replace "ls -R" with "find .", and you should get the correct result.

In fact, you could replace the whole thing with find:
```
find . -type f -empty -exec echo rm {} ';'
```

---

### Post by Arndt on 2009-04-21
> **odyniec said:**
> That's because it looks for "heythere" in the current directory, not in "chaat" as you expect it to. Replace "ls -R" with "find .", and you should get the correct result.

In fact, you could replace the whole thing with find:
```
find . -type f -empty -exec echo rm {} ';'
```

Or pipe the output from 'find' through 'xargs', perhaps with the help of the -print0 and -0 options to guard against spaces in filenames.

If there are spaces in filenames, doing

```
rm $a
```

won't work well either; doing 

```
rm "$a"
```

is better.

---

### Post by StunnerAlpha on 2009-04-21
Thanks a lot for the help you guys, that did the trick! Thanks for pointing out the quotes there Arndt.

---


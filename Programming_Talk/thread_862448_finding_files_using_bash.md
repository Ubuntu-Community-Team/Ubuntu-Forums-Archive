---
title: "finding files using bash"
date: 2008-07-17
forum: Programming Talk
---

### Post by jbsimon000 on 2008-07-17
I have a program, that when runs, creates a file with a name simlilar to "thisisfile1.120". The next time it runs it might make a file called "thisisfile1.121".

What I need to do is parse the filenames to get the "120" or "121" offa them. The file name will only ever have one ".", so that is what I wish to key on.

I have this so far...

   FILE_NAME="thisisfile1.*"

   for file in $FILE_NAME
   do
     printf "FILE = %s\n" $file
     # now, parse file to find the "."
     # HOW, I HAVE NO IDEA what function to use to search a string.
   done

I get each file name printed out, but can't seem to find the correct command to extract the "120", or "121", I have tried various combinations of echo `expr match "$file" '\.'`
     echo `expr index "$file" \.` and others to try and get the index of the "." character, or to get the substring, I can't seem to find the right magic incantation to get what I want.

Thanks for your time !
Joe

---

### Post by WW on 2008-07-17
Here's one way, using bash parameter expansion:
```

$ FN="thisisfile1.120"
$ echo ${FN/*./}
120
$ 

```

---

### Post by Felson on 2008-07-17
You could also do it using sed or awk

```

echo $FILE_NAME | sed 's/thisisfile1\.//'

```

or

```

echo $FILE_NAME | awk -F. '{print \$2}'

```

---

### Post by jbsimon000 on 2008-07-17
Thanks All !

Works great wooowhoooo !

---

### Post by ghostdog74 on 2008-07-17
> **Felson said:**
> 
```

echo $FILE_NAME | awk -F. '{print \$2}'

```

don't put backslash when its not necessary. the backslash will escape the $ sign and you should get an error.
```

echo $FILE_NAME | awk -F. '{print $2}'

```

---

### Post by daRealScanMan on 2008-07-17
I thought he wanted to do them all at once:

```
find thisisfile1.* | awk -F. '{print $2}'
```

---


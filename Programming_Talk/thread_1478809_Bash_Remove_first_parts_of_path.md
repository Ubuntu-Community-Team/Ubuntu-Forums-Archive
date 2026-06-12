---
title: "Bash: Remove first parts of path"
date: 2010-05-10
forum: Programming Talk
---

### Post by kkjaergaard on 2010-05-10
How do I remove the first parts of a path using Bash? I have "/path/to/my/file", and I want to have "to/my/file" or "my/file" depending on a variable.

---

### Post by Compyx on 2010-05-10
Something like this should do:
```

#/bin/bash

MY_PATH=/path/to/my/file

# display part of path
# args: string holding path
#       number of parts to display, starting from the end
subpath()
{
    echo "$1" | rev | cut -d"/" -f1-$2 | rev
}

subpath $MY_PATH 1
subpath $MY_PATH 2
subpath $MY_PATH 3

```

Output:
```

compyx@aspire7730g:~$ ./subpath.sh 
file
my/file
to/my/file

```

The general idea is to use the `cut' command to split a string on a delimiter, in this case '/'. Since cut doesn't have a syntax for specifying the number of fields starting at the end, we reverse the string using `rev'. We then cut the fields we want starting at the beginning of the reversed string and then reverse the result once more to get the string we wanted.

---

### Post by Portmanteaufu on 2010-05-10
> **kkjaergaard said:**
> How do I remove the first parts of a path using Bash? I have "/path/to/my/file", and I want to have "to/my/file" or "my/file" depending on a variable.

Alternatively, you could use sed:

```

#!/bin/bash
BASE_PATH=/path
FULL_PATH=/path/to/my/file
REL_PATH=`echo $FULL_PATH | sed 's|'$BASE_PATH'/|./|'`
echo $REL_PATH

```

---

### Post by kaibob on 2010-05-10
> **kkjaergaard said:**
> How do I remove the first parts of a path using Bash? I have "/path/to/my/file", and I want to have "to/my/file" or "my/file" depending on a variable.

It's not a very good solution, but just for the sake of completeness:

> $ var=/path/to/my/file ; var=${var#*/} ; echo ${var#*/}
to/my/file

$ var=/path/to/my/file ; var=${var#*/} ; var=${var#*/} ; echo ${var#*/}
my/file

---

### Post by tbastian on 2010-05-10
> **kkjaergaard said:**
> How do I remove the first parts of a path using Bash? I have "/path/to/my/file", and I want to have "to/my/file" or "my/file" depending on a variable.

I don't do much bash, but if you have a filename variable you could do something like:

```
file=`basename $file`
file='desired/path/'$file
```

assuming that 'file' is assigned your original filepath

---

### Post by tbastian on 2010-05-10
for example, this is my little test that I ran...

```

file=$HOME
echo $file
file=`basename $file`
file='a/new/path/'$file
echo $file

```

---

### Post by kkjaergaard on 2010-05-10
> **Compyx said:**
> Something like this should do:
```

#/bin/bash

MY_PATH=/path/to/my/file

# display part of path
# args: string holding path
#       number of parts to display, starting from the end
subpath()
{
    echo "$1" | rev | cut -d"/" -f1-$2 | rev
}

subpath $MY_PATH 1
subpath $MY_PATH 2
subpath $MY_PATH 3

```


Actually, I wanted to cut from the left side of the path:

```

#!/bin/bash

s=3
echo /path/to/my/file | cut -d"/" -f$s-

```

Anyway, I didn't know about the cut command. Thanks Compyx.

---


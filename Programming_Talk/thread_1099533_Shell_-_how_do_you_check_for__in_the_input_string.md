---
title: "Shell - how do you check for * in the input string"
date: 2009-03-18
forum: Programming Talk
---

### Post by akvino on 2009-03-18
I am not sure if this is possible, but how would you check for * in the input string when calling executable.(C shell or Bash shell)

Exmp myprogram *  - is there a way to check for a wildchar-star in the input string?

---

### Post by geirha on 2009-03-18
No, the program never sees the *. The shell expands the * to all files in the current directory and then executes the program.

If you have a directory with
```
$ ls
file1.txt  file2.txt  [COLOR="Lime"]myprog[/COLOR]

```
And run: ```
./myprog *.txt
```, then the shell first replace *.txt with file1.txt and file2.txt, so the command actually run is equivalent to running
```
./myprog file1.txt file2.txt
```

So with "./myprog *.txt", argv[1] and argv[2] of your program will contain the filename of file1.txt and file2.txt.

And if you actually want to pass the symbol * in an argument, escape it or quote it:
```
./myprog \*.txt
# or
./myprog "*.txt"

```

---

### Post by rendon on 2009-03-18
agreed, I think you'd have to find a work-around test case for such a scenario. 

Something like this will tell you if ONLY a * was passed

```

#!/bin/bash

all_args=${@}
wildcard=*
stuff=`echo $wildcard`



if [ "$all_args" == "$stuff" ]
    then echo "wildcard"
    else echo "no wildcard"
fi


```

and you might play with that a little to get your desired result

---

### Post by ghostdog74 on 2009-03-18
> **akvino said:**
> I am not sure if this is possible, but how would you check for * in the input string when calling executable.(C shell or Bash shell)

Exmp myprogram *  - is there a way to check for a wildchar-star in the input string?

before executing your script, you can set noglob
```

# set -o noglob
# myprogram *

```
however your wildcard expansion will be disabled.

---

### Post by akvino on 2009-03-18
noglob -hmmm

can this be set within the program and then unset at the end of the program?

---

### Post by akvino on 2009-03-18
> **rendon said:**
> agreed, I think you'd have to find a work-around test case for such a scenario. 

Something like this will tell you if ONLY a * was passed

```

#!/bin/bash

all_args=${@}
wildcard=*
stuff=`echo $wildcard`



if [ "$all_args" == "$stuff" ]
    then echo "wildcard"
    else echo "no wildcard"
fi


```

and you might play with that a little to get your desired result


Thanks will try it.

---

### Post by snova on 2009-03-18
> **akvino said:**
> noglob -hmmm

can this be set within the program and then unset at the end of the program?

Yes, but it won't do any good. The point is to prevent the shell from processing the * automatically. Setting it within the script is too late.

Actually testing for the character shouldn't be difficult (an example has already been posted), it's escaping it so the program sees it that is tricky. The simplest solution is probably just to escape or quote the character in the first place, as geirha suggested at the end of his post.

---


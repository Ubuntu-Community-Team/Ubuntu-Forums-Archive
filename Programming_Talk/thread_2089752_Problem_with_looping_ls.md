---
title: "Problem with looping ls"
date: 2012-11-30
forum: Programming Talk
---

### Post by alkal0id on 2012-11-30
Heres the script I'm testing:
```

#!/bin/bash

for pname in "$( ls )"
  do
    
    if [ -d "$pname" ];
      then
        echo "$pname"
      else echo "Couldnt find any directories"
      fi
    done

```

Its supposed to output a list of all the directories present in the directory. There are plenty of directories as well as normal files in this particular folder. The loop works, if I echo $pname without the if statement, then it lists all the files in the directory. Its the if statement thats giving me trouble. I added a file called "test" then changed the if statement to:
```
    if [ "$pname" = "test" ];
      then
        echo "Found it"
      else echo "Couldnt find it"
      fi

```
it returned negative. It is definitely a member of the loop so why can't the if statement detect it?

---

### Post by Vaphell on 2012-11-30
**do not use ls for anything other than "let's look what's in current directory"**

Shell globs should be used in scripts as they are exactly for that purpose and have none of the caveats that lurk when using ls.
```
for pname in *
do
  *something with "$pname"*
done
```


```
for pname in *
do
  if [ "$pname" = "test" ]
  then
    echo "Found it"
  else
    echo "Couldnt find it"
  fi
done
```
? if i am not mistaken, that should print "coudn't find it" a lot of times (for every !test) and "found it" once, when pname=test

---

### Post by drmrgd on 2012-11-30
Do you need to loop through every file in a directory, or can you just use a test operator ( [ -d ] or [ -e ] ) to look in the current directory to see if a file or directory exists?  I didn't think you had to loop over every file manually when testing.

EDIT: maybe an example of what I was thinking:

```

#!/bin/bash
file=$1
if [ -e $file ]; then
        printf "%s exists\n" $file
else
        printf "%s does not exist\n" $file
fi
```

```
$ ls
file1.txt  file2.txt  test.sh
$ ./test.sh file1.txt 
file1.txt exists
$ ./test.sh something
something does not exist

```

---


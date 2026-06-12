---
title: "pull the filename out of a path using sed"
date: 2008-03-27
forum: Programming Talk
---

### Post by jobsonandrew on 2008-03-27
Hi, Ive searched everywhere for this and come up with nothing... im writing a script to copy a file from a path to the home dir.. for example

```
source_file_path=$( echo $NAUTILUS_SCRIPT_SELECTED_URIS | sed -e 's/file:\/\///g' -e 's/\%20/\ /g')
source_file_name="$source_file_path" | sed m/\/*\.*$/g
```

I know this code doesnt work, but what I'm trying to do is pull the filename out of a path.. eg, turn:
/home/<username>/pictures/car.jpg
into:
car.jpg

im annoyed at myself for not remembering how to do this! any help appreciated
=================================================================
SOLVED
typical, i find the answer 2 minutes after i post a new topic:

Given:
foo=/tmp/my.dir/filename.tar.gz 
We can use these expressions:
path = ${foo%/*} 
To get: /tmp/my.dir (like dirname)
file = ${foo##*/} 
To get: filename.tar.gz (like basename)
base = ${file%%.*} 
To get: filename 
ext = ${file#*.} 
To get: tar.gz

---

### Post by ghostdog74 on 2008-03-27
in bash
```

# p=/home/user1/pictures/car.jpg
# echo ${p##*/}
car.jpg

```


with awk
```

# echo $p | awk -F"/" '{print $NF}'
car.jpg

```

I would rather not use sed for such stuff, although it can be done.

---

### Post by Martin Witte on 2008-03-27
with basename
```
martin@toshibap200:~$ basename /home/user1/pictures/car.jpg
car.jpg
martin@toshibap200:~$ 
```

---

### Post by WW on 2008-03-27
> **jobsonandrew said:**
>  im writing a script to copy a file from a path to the home dir.. 
Unless $HOME is not defined in your script, why not just do this:
```

cp full_path_name $HOME

```

---

### Post by ghostdog74 on 2008-03-27
@OP, take note that for many such path entries, using inbuilt bash shell string manipulation is more efficient than calling an external command like basename every time through the numbers

---


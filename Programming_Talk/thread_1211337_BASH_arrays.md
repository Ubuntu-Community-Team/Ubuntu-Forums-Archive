---
title: "BASH arrays"
date: 2009-07-12
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-07-12
Hello,
I'm writing a script that makes a link of all the files in the pwd, and puts the links in another directory. For this I want to put the values of the ls command into an array, and then I can step through the array using a for loop.  Can any one help with storing the values of the ls command in an array?

thanks

---

### Post by MadCow108 on 2009-07-12
```

i=0
while read line; 
do 
 files[i++]=$line; 
done < <(ls)
 

for (( i = 0 ; i < ${#files[@]} ; i++ ))
do
 echo ${files[$i]}
done

```

wouldn't it be easier to do it in one step for such a simple task?

---

### Post by c0mput3r_n3rD on 2009-07-12
> **MadCow108 said:**
> ```

i=0
while read line; 
do 
 files[i++]=$line; 
done < <(ls)

```
That's asking for user input.

I'm looking for more of a :
```

myArray='ls'

```
type of thing

---

### Post by MadCow108 on 2009-07-12
yes it stores everything ls lists in an arry
for only files modifiy the ls command (e.g. ls -1 | grep -v ^d)
works on my machine
GNU bash, version 3.2.48(1)-release (i486-pc-linux-gnu)

---

### Post by c0mput3r_n3rD on 2009-07-12
```

i=0
while read line; 
do 
 files[i++]=$line; 
done < <(ls)
```
will get everything ls lists, and then i can use the for loop to step through the array that was created?

---

### Post by MadCow108 on 2009-07-12
oh right:
```

IFS=$'\n'
files=(`ls -1`) 
unset IFS

```
is a much easier solution :)

IFS change so it handles spaces correctly

---

### Post by c0mput3r_n3rD on 2009-07-12
Awsome! Thank you very much :D

---

### Post by MadCow108 on 2009-07-12
the unset IFS may be problematic when you need it again
better:
```

bac=$IFS
IFS=$'\n'
files=(`ls -1`) 
IFS=$bac

```

---

### Post by ghostdog74 on 2009-07-12
you don't need arrays for this
```

find /path -type f | while read FILE
do
   #do your stuff with $FILE
done

```

---

### Post by kaibob on 2009-07-12
I'm just learning arrays, but it was mentioned in another thread that you can create an array as in the following:

```
array=( * ) ; for f in "${array[@]}" ; do echo "$f" ; done
```

Is it necessary to use ls?

---

### Post by ghostdog74 on 2009-07-12
> **kaibob said:**
> 

Is it necessary to use ls?
no need.

---


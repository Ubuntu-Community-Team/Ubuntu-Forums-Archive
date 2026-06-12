---
title: "[SOLVED] Shell Scripting Shift Command"
date: 2008-03-13
forum: Programming Talk
---

### Post by DGortze380 on 2008-03-13
Hey All,

Again, I've been searching for two hours and can't find an answer here or on google. I know how to use a shift for command line arguments, is there a way to use it for variables that are read in? Or is there a similar command?

EX:

```


#!/bin/ksh

while read name var0 var1 var2 var3 var4 ;do
     for (( x=0;x<4;x++ )) ;do
          sampleArray[x]=$var0
          shift 1
     done
done<fileName


```

The above obviously doesn't work or I wouldn't be asking. This is a simple example, but I need to read 50+ variables into an array :???:

Thanks

---

### Post by WW on 2008-03-14
Can you read directly into the array?  For example,
> 
$ read a[0] a[1] a[2]
first second third
$ echo ${a[2]} ${a[1]} ${a[0]}
third second first
$ 


---

### Post by DGortze380 on 2008-03-14
> **WW said:**
> Can you read directly into the array?  For example,

Not sure how I'd do that, or if it would work.  I'm reading from a text file, that has 15 to 20 lines and 50+ entries per line. I need an array for each line.

---

### Post by ghostdog74 on 2008-03-14
you can put into array
```

while IFS=" " read -a array; 
do 
  echo ${array[0]}; 
  # use a for loop to iterate the elements.
done < file

```

---

### Post by WW on 2008-03-14
I don't know if ksh is different, but in bash, the **read** command has the **-a** option:
> 
$ read -a myarray
zero one two three four five six seven eight nine ten eleven 
$ echo ${myarray[3]}
three
$ echo ${myarray[11]}
eleven
$


---

### Post by nanotube on 2008-03-14
you can read the line directly into an array, as long as items are separated by space. the following bash session should give you some clues:

```

$ myarr=( bla shmu gnu )
$ echo ${#myarr[*]}
3
$ echo ${myarr[0]}
bla
$ echo ${myarr[1]}
shmu
$ echo ${myarr[2]}
gnu
$ myarr=( $(ls -1) )
$ echo ${#myarr[*]}
9
$ ls -1
bin
Desktop
dev
documents
Examples
seamonkey-1.1.7.en-US.linux-i686.tar.gz
ssh
tmp
vmware
$ echo ${myarr[5]}
seamonkey-1.1.7.en-US.linux-i686.tar.gz


```

so, once you have a "line" in one variable, (say, $line), to make an array out of it, you can simply do
```
myarr=( $line )
```

---

### Post by DGortze380 on 2008-03-14
ok, I've pretty much got it working, I have a few other things to work out, I'll post back if I get stuck, otherwise I'll mark it solved.

---

### Post by DGortze380 on 2008-04-08
I know, old thread. but I finally got around to finishing this problem. 
Ended up using a compound variable. Reading directly into and array worked in bash but not ksh, and left me with too many indirect variable references and control breaks. Unfortunately you do have to read it all in, but it ended up being shorter in the end.

```

#!/bin/ksh

itemCount=0
items=
(
     typeset=" "
     integer bal[52]
)

while read items[$itemCount].name items[$itemCount].bal[0] ... items[$itemCount].bal[51] ;do

echo " "
(( intemCount++ ))

done<filename


```

Thanks for the help!

---


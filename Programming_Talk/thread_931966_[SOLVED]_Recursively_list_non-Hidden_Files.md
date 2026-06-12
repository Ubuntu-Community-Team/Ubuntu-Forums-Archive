---
title: "[SOLVED] Recursively list non-Hidden Files"
date: 2008-09-27
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-09-27
I need to "Recursively list non-Hidden Files" like this

Directory
[PHP]/home
	/apple
		/.seeds
		/.core
		/yummy
	/pear
		/.stem
		/good
	/banana
		/.potassium
	/.fruit
		/.betterthenveggies[/PHP]

Producing
[PHP]/home/apple/yummy
/home/pear/good
/home/banana[/PHP]

Thanks

---

### Post by kjohansen on 2008-09-27
in what language?

you could get the list of dirs and just check for the leading "."

---

### Post by Mr.Macdonald on 2008-09-27
Language is important, huh?

Bash, Awk (embedded in Bash)

---

### Post by OutOfReach on 2008-09-27
EDIT: Woops, saw you need Bash, Awk. Nevermind.

It can be done in Python like this:
```

result = []
for x in os.listdir("YOUR_DIRECTORY_HERE"):
    if x.startswith("."):
        continue
    else:
        result.append(x)
print result
```
That should print out the non hidden directories

---

### Post by Mr.Macdonald on 2008-09-27
Recursively means reading directories inside other direcories

---

### Post by ghostdog74 on 2008-09-27
just use find
```

find /path -type d  -name "[^.]*"

```

---

### Post by stylishpants on 2008-09-27
I think that the thing to do here is go low-tech:

```
find | grep -v '/\.'
```

This has one problem:  If a filename actually contains a / followed by a ., then this will not show that file.  Given that embedding a slash in a filename is weird, frowned upon and unusual, this isn't that onerous a restriction.

---

### Post by ghostdog74 on 2008-09-27
> **stylishpants said:**
> I think that the thing to do here is go low-tech:

```
find | grep -v '/\.'
```

This has one problem:  If a filename actually contains a / followed by a ., then this will not show that file.  Given that embedding a slash in a filename is weird, frowned upon and unusual, this isn't that onerous a restriction.

there's no need to pipe to grep. find can find patterns.

---

### Post by ad_267 on 2008-09-27
> **ghostdog74 said:**
> just use find
```

find /path -type d  -name "[^.]*"

```

I think he wants files not directories, so it's "-type f". Also you might want to exclude files with a ~ at the end.
```

find /path -type f  -name "[^.]*[^~]"

```

---

### Post by Mr.Macdonald on 2008-09-27
only

find ./ | grep "\/." worked so i guess thats what i will use. but i would like a command that would test the first letters not the whole thing

thanks

---

### Post by slavik on 2008-09-27
what class is this for?

---

### Post by ghostdog74 on 2008-09-27
> **Mr.Macdonald said:**
> only find ./ | grep "\/." worked 
are you sure?

---

### Post by stylishpants on 2008-09-28
Some clarifications are in order:

1. Do you want files only, or some other subset of files, directories, symlinks and devices?

2. Do you want to find non-hidden files within hidden directories, such as: 
       /home/.fruit/pear

3. What do you mean by "test the first letters?"  Do you mean the first letters of the basename? (eg. pear, in the above example)


ghostdog, find's pattern matching seems to be insufficient here, in that it doesn't seem to prune off hidden directories entirely (I was assuming that the answer to #2 above was "no", you appear to have assumed "yes".)  Perhaps you can get find's -prune option to work as desired, I gave up on that after a couple of minutes and decided that the simpler solution was sufficient here.

---

### Post by ghostdog74 on 2008-09-28
> **stylishpants said:**
> 
ghostdog, find's pattern matching seems to be insufficient here, 
what the oP want's to do can be done with just shell expansion. as an illustration
```

# ls -tlr
total 4
-rw-r--r-- 1 root root    0 Sep 20 08:47 testfile_withouthidden
drwxr-xr-x 2 root root 4096 Sep 28 13:20 .testdir
-rw-r--r-- 1 root root    0 Sep 28 13:20 .testfile
#                      

```

there's 1 hidden directory, 1 hidden file and a normal file.
```

# find . -name "[^.]*"
./testfile_withouthidden

## ls [^.]* #using ls with shell expansion
testfile_withouthidden


```

---

### Post by stylishpants on 2008-09-28
> **ghostdog74 said:**
> what the oP want's to do can be done with just shell expansion. as an illustration
```

# ls -tlr
total 4
-rw-r--r-- 1 root root    0 Sep 20 08:47 testfile_withouthidden
drwxr-xr-x 2 root root 4096 Sep 28 13:20 .testdir
-rw-r--r-- 1 root root    0 Sep 28 13:20 .testfile
#                      

```

there's 1 hidden directory, 1 hidden file and a normal file.
```

# find . -name "[^.]*"
./testfile_withouthidden

## ls [^.]* #using ls with shell expansion
testfile_withouthidden


```

So far as your example goes, I completely agree with you.  Where our solutions differ is here:

```
# touch .testdir/.testfile
# touch .testdir/testfile_withouthidden

#### Complete file list:
# find
.
./testfile_withouthidden
./.testfile
./.testdir
./.testdir/.testfile
./.testdir/testfile_withouthidden

#### Your solution:

# find . -name "[^.]*"
./testfile_withouthidden
./.testdir/testfile_withouthidden

#### My solution:
# find | grep -v '/\.'
.
./testfile_withouthidden

```

My solution was written with the assumption that the OP would not want to see non-hidden files within hidden directories.

---

### Post by koenn on 2008-09-28
how about just ' ls -R ' ?

This is "everything" :
```

x:~/TEST$ ls -1 -RA
.:
afile
folder
.hiddenfile
.hiddenfolder

./folder:
afile
.hiddenfile

./.hiddenfolder:
afile
.hiddenfile


```

This is "non-hidden files only"
```

x:~/TEST$ ls -1 -R
.:
afile
folder

./folder:
afile


```
non-hidden files in hidden directories are not shown.

the "-1" is just for output formatting.

---

### Post by nvteighen on 2008-09-28
> **slavik said:**
> what class is this for?
I also ask the same... but "[In dubio pro reo]("http://en.wikipedia.org/wiki/In_dubio_pro_reo")"

---

### Post by Mr.Macdonald on 2008-09-28
> what class is this for?

Ill ask you what kind of class would ask this as a homework assignment?

I am in High School, If this is what they ask for homework in college then Ill get by very easily


I was trying to avoid it but I used Awk and solved it

---

### Post by slavik on 2008-09-29
in college, an assignment similar to this appeared in my workstation programming class where we wrote shell level code in C. :) (the midterm was to write a simple shell)

---

### Post by dwhitney67 on 2008-09-29
> **Mr.Macdonald said:**
> Ill ask you what kind of class would ask this as a homework assignment?

I am in High School, If this is what they ask for homework in college then Ill get by very easily


I was trying to avoid it but I used Awk and solved it
Thanks for sharing your solution.

---


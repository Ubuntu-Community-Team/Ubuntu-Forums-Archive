---
title: "shell: using textfile for file locations?"
date: 2008-03-15
forum: Programming Talk
---

### Post by flowevd on 2008-03-15
hi

i've got a list of some files on my computer (with their full paths) in a text file. I want to execute a shell command such that I can use this textfile as a kind of index to copy all of these files into one directory.

how to??

thanks for your help
flowevd

---

### Post by ruy_lopez on 2008-03-15
The file needs absolute pathnames.

```

for file in `cat /path/to/file_with_filenames`
do
        if [ -e "$file" ]; then
                echo "$file"
                cp "$file" "/path/to/folder/for/backup/"
        fi
done

```

-e tests if the file exists.

If the file contains relative pathnames, you'll need to add a prefix.

---

### Post by flowevd on 2008-03-15
aha

thank you!!

---

### Post by flowevd on 2008-03-15
ah...

all goes well... except my path and filenames contain spaces, which means there's no output (i found this out by removing the 'if' from the script, and got a 'cannot stat' for each space-divided part of each filename). have tried enclosing a test filename in "" and '' but to no avail... how do i get around this?

---

### Post by stroyan on 2008-03-15
The "for" style breaks input at spaces.
You can instead use the shell "read" builtin to read a line into a variable.
```
while read file
do
        if [ -e "$file" ]; then
                echo "$file"
                cp "$file" "/path/to/folder/for/backup/"
        fi
done < /path/to/file_with_filenames
```

---

### Post by ghostdog74 on 2008-03-15
```

awk '{ cmd="cp \042"$0"\042 /backup";system(cmd) }' file

```
or 
```

grep . file | xargs -i cp "{}" /backup

```

---

### Post by flowevd on 2008-03-15
hi

i lost the -e part in quest for simplicity, and eventually ended up with the following, which worked fine.

```

cat '/home/duncan/lists.txt' | while read FILE
do
	cp "$FILE" ~/OUTPUT
done

```


at this stage, probably would have been quicker for me to copy em all by hand :) ... next time, though...

thanks for the help

---

### Post by ghostdog74 on 2008-03-15
> **flowevd said:**
> hi

i lost the -e part in quest for simplicity, and eventually ended up with the following, which worked fine.

```

cat '/home/duncan/lists.txt' | while read FILE
do
	cp "$FILE" ~/OUTPUT
done

```


at this stage, probably would have been quicker for me to copy em all by hand :) ... next time, though...

thanks for the help

forget the cat. the while loop can read a file direct.
```

while read -r FILE
do
	cp "$FILE" ~/OUTPUT
done < '/home/duncan/lists.txt'

```
the least you can do is practice "good" habits.

---

### Post by stroyan on 2008-03-15
Ghostdog:
  Speaking of things that can be left out-
  I was surprised by your use of 'grep .' with xargs.
  I find that 'xargs -i' skips over blank lines itself.
  (But your awk example could benefit from a 'grep .' filter)

> **ghostdog74 said:**
> ```

awk '{ cmd="cp \042"$0"\042 /backup";system(cmd) }' file

```
or 
```

grep . file | xargs -i cp "{}" /backup

```

---

### Post by flowevd on 2008-03-15
ah, i see. thanks!

---

### Post by ghostdog74 on 2008-03-15
> **stroyan said:**
> Ghostdog:
  Speaking of things that can be left out-
  I was surprised by your use of 'grep .' with xargs.
  I find that 'xargs -i' skips over blank lines itself.
  (But your awk example could benefit from a 'grep .' filter)

i am not really sure what you mean by "skips over blank lines". maybe you would want to show an example. the awk one too. with awk, there's no need for any other tools, for this case. also, using grep is only one "crazy" idea that came to me. a more "sane" way could be simply
```

more  file | xargs -i cp "{}" /backup

```

---

### Post by ruy_lopez on 2008-03-15
> **flowevd said:**
> 
i lost the -e part in quest for simplicity


-e is what happens when a C programmer writes a shell script. (I need to remember that bash doesn't explode on errors, like C does)

> **flowevd said:**
> 
at this stage, probably would have been quicker for me to copy em all by hand 

That wouldn't be any fun.

---

### Post by stroyan on 2008-03-15
> **ghostdog74 said:**
> i am not really sure what you mean by "skips over blank lines". maybe you would want to show an example. the awk one too. with awk, there's no need for any other tools, for this case. also, using grep is only one "crazy" idea that came to me. a more "sane" way could be simply
```

more  file | xargs -i cp "{}" /backup

```

The only helpful effect that 'grep .' might have is to eliminate blank lines from
the input file that would otherwise cause a strange cp command with no source argument.  That might actually happen with the awk example because there is no test for $0 being non-null.
The simplest way to use xargs on an input file is to redirect the stdin of xargs from the file rather than piping the output of a command like cat or grep or more.  See the last command below
```

$ printf "a\nb\n\nc\n\nd\n" > input
$ cat input
a
b

c

d
$grep . input
a
b
c
d
$ awk '{ cmd="echo cp \042"$0"\042 /backup";system(cmd) }' input
cp a /backup
cp b /backup
cp  /backup
cp c /backup
cp  /backup
cp d /backup
$ grep . input | awk '{ cmd="echo cp \042"$0"\042 /backup";system(cmd) }'
cp a /backup
cp b /backup
cp c /backup
cp d /backup
$ xargs -i echo cp "{}" backup < input
cp a backup
cp b backup
cp c backup
cp d backup
$ 

```

---

### Post by ghostdog74 on 2008-03-15
> **stroyan said:**
> The only helpful effect that 'grep .' might have is to eliminate blank lines from
the input file that would otherwise cause a strange cp command with no source argument.  That might actually happen with the awk example because there is no test for $0 being non-null.
The simplest way to use xargs on an input file is to redirect the stdin of xargs from the file rather than piping the output of a command like cat or grep or more.  See the last command below
```

$ printf "a\nb\n\nc\n\nd\n" > input
$ cat input
a
b

c

d
$grep . input
a
b
c
d
$ awk '{ cmd="echo cp \042"$0"\042 /backup";system(cmd) }' input
cp a /backup
cp b /backup
cp  /backup
cp c /backup
cp  /backup
cp d /backup
$ grep . input | awk '{ cmd="echo cp \042"$0"\042 /backup";system(cmd) }'
cp a /backup
cp b /backup
cp c /backup
cp d /backup
$ xargs -i echo cp "{}" backup < input
cp a backup
cp b backup
cp c backup
cp d backup
$ 

```
its trivial to skip checking newlines in awk , again no need for grep
```

awk '!/^$/{ cmd="cp \042"$0"\042 /backup";system(cmd) }' file

```
even if this check is not done, the cp will just copy the rest of the files and produce errors on the blank lines, which can be easily masked out 
eg awk 'blahblah' file 2>/dev/null
thanks for the last eg, totally forgot about that.

---

### Post by mridkash on 2008-03-16
A method I use for backing up files, 

I guess it is faster than any of the methods above,

```
cat files.list | xargs -IA cp "A" /dest/dir
```No blank space issue.

---

### Post by ghostdog74 on 2008-03-16
> **mridkash said:**
> A method I use for backing up files, 

I guess it is faster than any of the methods above,

```
cat files.list | xargs -IA cp "A" /dest/dir
```No blank space issue.

cat can be dropped.

---

### Post by mridkash on 2008-03-17
> **ghostdog74 said:**
> cat can be dropped.

You mean this,
```
xargs -IA cp "A" /dest/dir < files.list
```

---

### Post by ruy_lopez on 2008-03-17
> **mridkash said:**
> You mean this,
```
xargs -IA cp "A" /dest/dir < files.list
```

or this:

```
xargs -a files.list -IA cp "A" /dest/dir
```

---

### Post by pmasiar on 2008-03-17
> **flowevd said:**
> except my path and filenames contain spaces, 

I recommend to get rid of spaces in directories and filenames - space is delimiter, you will have no end of problems with that! Use underscore if you have to.

---


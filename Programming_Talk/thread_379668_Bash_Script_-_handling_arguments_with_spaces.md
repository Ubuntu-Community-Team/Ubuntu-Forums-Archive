---
title: "Bash Script - handling arguments with spaces"
date: 2007-03-08
forum: Programming Talk
---

### Post by neilp85 on 2007-03-08
What's the proper way to pass/handle arguments to a bash script that have spaces in them. Right now I'm using $* to get all the arguments. This fails when escaping the spaces or protecting the arguments in quotes. Here's the relavent code
```
for FILE in $*
do
    cp $FILE $TMPDIR
done
```

---

### Post by Mr. C. on 2007-03-08
See Loose Ends, Week 11: 

[http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

MrC

---

### Post by neilp85 on 2007-03-08
That document didn't explain how to solve this. The only relevant part was on quoting variables that can contain whitespace. Doing that to $* won't work either. Let me illustrate my problem more clearly

```
#!/bin/bash
for i in $*
do
    echo "$i"
done 
```

This produces the following output 
```
 $ ./test "a b" c d "e f g"
a
b
c
d
e
f
g
```

When what would really like is this
```
$ ./test "a b" c d "e f g"
a b
c
d
e f g
```

Is there a way to get the second output? The only other idea I could come up with was using xargs and modifying my script but it seems to me like there should be a way to do this.

---

### Post by Mr. C. on 2007-03-08
Sure it did.  I wrote it.

Here's the output of the script using what's mentioned:

```
$ foo.sh "a b" c d "e f g"
a b
c
d
e f g
```

---

### Post by neilp85 on 2007-03-08
This is odd, what could cause this difference in execution?

---

### Post by Mr. C. on 2007-03-08
You are using the wrong $ variable.  I didn't say I have the same one as you - just that the variable you seek is in that paper.  Hint: search for $*, and see what else appears.

MrC

---

### Post by neilp85 on 2007-03-08
After some more searching I figured this one out

```
#!/bin/bash
for i in `seq 1 $#`
do
    eval a=\$$i
    echo $a
done
```

---

### Post by Mr. C. on 2007-03-08
Oh, dear, that's convoluted !

Ok, you've suffered enough.  Copy and paste this into your shell:

```
man -P "less -p 'Expands  to  the positional'" bash
```

MrC

---

### Post by ghostdog74 on 2007-03-08
```

for FILE in "$@"
do
    echo $FILE $TMPDIR
done


```

---

### Post by weegreenblobbie on 2010-01-19
For those who want to pass arguments to another bash script from the main one, this is what I've done.

The main script is of the form:

script OPTIONS DIRS+

Where there may be one or more options followed by one or more directory paths, these directory paths could contain spaces or other special characters like $.

My solution is to create a bash array, then handle the arguments and build a new array for the directories to pass to another script to do special processing.

```


# Create a bash array for all the arguments passed to this script

i=0
argv=()
for arg in "$@"; do
    argv[$i]="$arg"
    i=$((i + 1))
done

# Handle OPTIONS and build directory array

n_threads=1
check_env=1
run_jobs=0
set_version="3c4n.15"
is_2010=""

i=0
dir_index=0
while test $i -lt $# ; do

    arg="${argv[$i]}"

    case "$arg" in

        --2010)    is_2010="--2010";;

        -h|--help) printUsage;;

        -j|--jobs) i=$((i + 1)); n_threads=${argv[$i]};;

        -rj|--run-jobs) run_jobs=1;;

        --no-env-check) check_env=0;;

        --set-version) i=$((i + 1)); set_version="${argv[$i]}";;

        *) if ! test -d "$arg" ; then
            error "Unknown argument or directory '$arg'"
        else
            source_dirs[$dir_index]="$arg"
            dir_index=$((dir_index + 1))
        fi;;

    esac

    i=$((i + 1))

done

# Call the other bash script to do special processing

ds_process_dirs.bash $is_2010 --no-env-check --jobs $n_threads "${source_dirs[@]}"


```

---

### Post by original_MikZ on 2013-01-23
That's awesome, @weegreenblobbie! Your example has allowed me to get this working:
```

#!/bin/bash
i=0
argv=()
for arg in "$@"
do
    argv[$i]="${arg#file://}"
    i=$((i + 1))
done
/bin/$(basename $0) "${argv[@]}"
```

I've saved that to ~/bin/fix_url and softlinked my own versions of mv and cp to it, like this:
```

cd ~/bin
ln -s fix_url mv
ln -s fix_url cp
```

So now I can do this:
```

mv -a file:///home/mikz/inbox/2013-01-23_162541.jpg ~/somewhere_useful/better_name.jpg
```

Why bother? If you use the copy command in nautils and paste it into a terminal, it prefixes the path with 'file://'. It means I can use nautils to see what a file is, but handle giving it a better name in the shell.

I'm excited, and it's all thanks to @weegreenblobbie =D>

---


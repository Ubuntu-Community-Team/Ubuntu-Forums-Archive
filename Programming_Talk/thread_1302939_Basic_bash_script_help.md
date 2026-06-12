---
title: "Basic bash script help"
date: 2009-10-27
forum: Programming Talk
---

### Post by chuuk on 2009-10-27
Hi,

I want a script that can output all the .s, .o and executable files in the current directory. So far, I've got this far:

```
  
  1 for X in *.s *.o 
  2     do
  3     echo $X
  4 done

```

But I don't know how to search for executables because they don't have any extension. What would be an easy way of doing this?

Cheers

PS: I don't want to use find/grep because I might want to modify the code to do more later on.

---

### Post by djurny on 2009-10-27
> **chuuk said:**
> Hi,

I want a script that can output all the .s, .o and executable files in the current directory. So far, I've got this far:

```
  
  1 for X in *.s *.o 
  2     do
  3     echo $X
  4 done

```

But I don't know how to search for executables because they don't have any extension. What would be an easy way of doing this?

Cheers

PS: I don't want to use find/grep because I might want to modify the code to do more later on.

maybe just
```
ls *.s *.o
```
and something like
```

for f in "$(ls *)"; do
  [ -x ${f} ] || continue
  echo "${f}"
done

```
the last snippet could be done more efficiently, but i cannot think of something at the mo..

---

### Post by djurny on 2009-10-27
> **chuuk said:**
> Hi,

I want a script that can output all the .s, .o and executable files in the current directory. So far, I've got this far:

```
  
  1 for X in *.s *.o 
  2     do
  3     echo $X
  4 done

```

But I don't know how to search for executables because they don't have any extension. What would be an easy way of doing this?

Cheers

PS: I don't want to use find/grep because I might want to modify the code to do more later on.

maybe just
```
ls *.s *.o
```
and something like
```

files="$(ls *)"
for f in ${files}; do
  [ -x ${f} ] || continue
  echo "${f}"
done

```
the last snippet could be done more efficiently, but i cannot think of something at the mo..

---

### Post by chuuk on 2009-10-27
Ok, me again. So I'm trying out if statements:

```

  1 for X in *
  2  do
  3     if [ -f $X]
  4         then echo "hello"
  5     fi
  6 done

```

Why does this refuse to work?

Cheers

---

### Post by ghostdog74 on 2009-10-27
> **djurny said:**
> maybe just
```
ls *.s *.o
```
and something like
```

for f in "$(ls *)"; do
  [ -x ${f} ] || continue
  echo "${f}"
done

```
the last snippet could be done more efficiently, but i cannot think of something at the mo..

no need ls , its useless and written like that is prone to white space in file names problem

---

### Post by ghostdog74 on 2009-10-27
> **chuuk said:**
> Ok, me again. So I'm trying out if statements:

```

  1 for X in *
  2  do
  3     if [ -f $X]
  4         then echo "hello"
  5     fi
  6 done

```

Why does this refuse to work?

Cheers

to check for execute permission use -x... see man test for info
```

for x  in *
do
  if [ -x "$x" ];then
    # do something
  fi
done

```

---

### Post by falconindy on 2009-10-28
```
find . -type f -executable
```
Add a '-maxdepth 1' before -type if you want to limit it to your current directory.

Solutions using 'ls' as part of a for loop will fail on files with white space in the name.

---

### Post by djurny on 2009-10-28
> **ghostdog74 said:**
> no need ls , its useless and written like that is prone to white space in file names problem
if you are present in an empty directory, and bluntly use
```
for i in *; do ..; done
```
i will be '*' .. the [ -x * ] || .. will also fail ;)

edit

```

for i in *; do
  # break if no files found
  [ "${i}" = "*" ] && break

  # this will interpret whitespace as separators
  echo ${i}
  ls ${i}

  # this will NOT interpret whitespace as separators..
  # quotes rule :)
  echo "i='${i}'"
  ls "${i}"
done

```

---

### Post by ghostdog74 on 2009-10-28
don't understand what you are trying to say. if you run the for loop on an empty directory,
```

$ ls -ltr
total 0
$ for i in *; do if [ -x "$i" ];then  echo "executable"; fi; done

```

"executable" is not echoed in the above, which is correct behaviour. what's the deal with "spaces" in an empty directory?

---

### Post by djurny on 2009-10-28
the spaces have nothing to do with an empty directory
its about the expansion your shell (bash) performs;

```
for i in *; do echo "i='${i}'"; done
```
the '*' in the **for** statement will be expanded to all files your shell finds in the current directory.. if there are no files present in the current directory, this snippet will produce
```
i='*'
```on your terminal.

the whitespace remark is another cup o'tea.. most commands use the whitespace (space) as a parameter separator, which will not behave as expected in some cases..

if you do 
```
for i in *; do cat ${i}; done
``` and your directory contains filenames with whitespaces in them, e.g.
```
./a b c
./d e f
./ghi
```
the shell will expand '*' to 'a b c d e f ghi'.. **for** will iterate that string and assign **i** to each item in the expanded '*' string.. what happens next is not what you would expect; for each of the items, ```
ls ${i}
``` will be executed, resulting in 
```
ls a b c
ls d e f
ls ghi
```
this looks normal, but **ls** is executed with its argv filled with a b c, with whitespace as its separator.. in other words, 
```
argv[1]=a argv[2]=b argv[3]=c
```
this will be equivalent to 
```
ls a
ls b
ls c
ls d

```
etc..
..

---

### Post by ghostdog74 on 2009-10-28
> **djurny said:**
> the spaces have nothing to do with an empty directory
its about the expansion your shell (bash) performs;

```
for i in *; do echo "i='${i}'"; done
```
the '*' in the **for** statement will be expanded to all files your shell finds in the current directory.. if there are no files present in the current directory, this snippet will produce
```
i='*'
```on your terminal.


in the above, you are just echoing out whats the value of the variable is and doing nothing else.  BUT i am talking about doing this:
```

for i in *; do if [ -x "$i" ];then  echo "executable"; fi; done

```
on an empty directory like what you said. in this case, there is a specific check on what $i is before anything is done on that variable.

---

### Post by djurny on 2009-10-28
> **ghostdog74 said:**
> in the above, you are just echoing out whats the value of the variable is and doing nothing else.  BUT i am talking about doing this:
```

for i in *; do if [ -x "$i" ];then  echo "executable"; fi; done

```
on an empty directory like what you said. in this case, there is a specific check on what $i is before anything is done on that variable.
true, but in that example, [ -x "$i" ] is saved by the quotes :) as it will actually check if a file called '*' is executable or not.. even though there is no file called '*' in the current directory..

---

### Post by ghostdog74 on 2009-10-28
> **djurny said:**
> true, but in that example, [ -x "$i" ] is saved by the quotes :) as it will actually check if a file called '*' is executable or not.. even though there is no file called '*' in the current directory..
that's the correct behaviour whether you are in an empty directory of a directory with files. When you iterate files and directories using for loops, you will one way or the other check whether they are directories of files or whether they exists etc according to the task at hand...eg
the common things to do when iterating files using for loop
```

for f in * 
do
  if [ -d "$f" ]; then
    echo "$f is a directory and do something"  
  fi 
  if [ -f "$f" ] ;then
    echo "$f is a file and do something"  
  fi
  # and so on
done

```

you don't just iterate the files and do nothing except echoing out their file names.

---

### Post by Arndt on 2009-10-28
> **ghostdog74 said:**
> that's the correct behaviour whether you are in an empty directory of a directory with files. When you iterate files and directories using for loops, you will one way or the other check whether they are directories of files or whether they exists etc according to the task at hand...eg
the common things to do when iterating files using for loop
```

for f in * 
do
  if [ -d "$f" ]; then
    echo "$f is a directory and do something"  
  fi 
  if [ -f "$f" ] ;then
    echo "$f is a file and do something"  
  fi
  # and so on
done

```

you don't just iterate the files and do nothing except echoing out their file names.

You might have an 'else' branch in the script. Or the test might be "is the file not executable".

---

### Post by ghostdog74 on 2009-10-28
> **Arndt said:**
> You might have an 'else' branch in the script. Or the test might be "is the file not executable".

that was done up as a quick example...

---

### Post by Arndt on 2009-10-28
> **ghostdog74 said:**
> that was done up as a quick example...

Well, I meant, in that case the script may report something spurious like "the file * is not executable".

---

### Post by djurny on 2009-10-28
> **ghostdog74 said:**
> that's the correct behaviour whether you are in an empty directory of a directory with files. When you iterate files and directories using for loops, you will one way or the other check whether they are directories of files or whether they exists etc according to the task at hand...eg
the common things to do when iterating files using for loop
```

for f in * 
do
  if [ -d "$f" ]; then
    echo "$f is a directory and do something"  
  fi 
  if [ -f "$f" ] ;then
    echo "$f is a file and do something"  
  fi
  # and so on
done

```

you don't just iterate the files and do nothing except echoing out their file names.

true, but, i was trying to say that it is a bit weird iterating a for loop for something in case that there is no reason to iterate it..

in c:
[php]
for (i = 0; i != 0; ++i) {
  printf("no way\n");
}
[/php]
will not printf anything, as i is already 0..

in the case of the script example, 
```

for i in *; do
  echo "no way"
done

```
**'*'** is actually empty, that is, the shell wildcard expansion fails on an empty directory.. the **for** loop is iterated anyway.. regardless the wildcard expansion 'result'.. the script for will actually echo "no way" in this case..!

it gets even more interesting/annoying when you actually have a file called '*' on your filesystem :D

```

touch \* abc def ghi
for i in *; do echo "i='${i}'"; done

```

---

### Post by ghostdog74 on 2009-10-28
> **djurny said:**
> 
**'*'** is actually empty, that is, the shell wildcard expansion fails on an empty directory.. the **for** loop is iterated anyway.. regardless the wildcard expansion 'result'.. the script for will actually echo "no way" in this case..!

i know what you mean. but you are detracting from our discussion. Why would he want to iterate the directory if its empty? please look at the first post again. he is clearly trying to find .so and .o files. he should write his code this way without any ls:
```

for f in *.so *.o
do
   if [ -e "$i" -a -x "$i" ];then  
       echo "$i exists and do something"
   fi
done

```

or the checking can be omitted if he is sure there are .so and .o files in the directory.

> 
it gets even more interesting/annoying when you actually have a file called '*' on your filesystem :D

if * is a file, it will just act as a file. 
```

$ echo "test" > *
$ for i in *; do echo "$i"; done
*
$ for i in *; do rm -f $i; done
$ ls
$

```
so why is it "annoying"?? really don't understand

---


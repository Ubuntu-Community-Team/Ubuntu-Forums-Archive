---
title: "Help me finish this very easy shell script"
date: 2007-08-12
forum: Programming Talk
---

### Post by jimmymus on 2007-08-12
This script should be very easy but I'm pretty new to shell scripting. All I want to do is to output all the files in a directory and all it's subdirectories, with the files' full locations, into a text file.

I have this so far

#!/bin/bash
for i in $(ls); do
test -f $i && echo $i
done

This is just where I'm at now. I can't make it do it in subdirectories though. If I change
for i in $(ls)
to
for i in $(ls -R)
it still only prints out the files in the working directory, not the other files in the subdirectories. 

So that's my first problem. Then, I don't know how to have it output the file in it's full path. I'm getting a list of 
file1
file2
file3
but I want a list of 

/home/jimmy/file1
/home/jimmy/file2
/home/jimmy/file3

like that. 

Then, I need to output them to a file. I know how to output things into a file, like this
ls -R >list.txt

but I'm doing this in a for-loop. Can I just add stuff onto the next line of a file? If I add >list.txt into my program won't it just create a file called list.txt with one file location in it, then recreate the file with another location in it? Etc etc?

I hope this made sense, I'd love an answer here. Thanks
Jimmy

---

### Post by Jessehk on 2007-08-12
Without knowing much about bash scripting (somebody else can probably think of something better), here's what I came up with:

```

#!/bin/bash

location=$(pwd)

for thing in $(ls); do
    if [ -f $thing ]; then
        echo "${location}/$thing"
    fi
done

```

---

### Post by jimmymus on 2007-08-12
Thanks jessehk
I'm glad to learn about the 'pwd' command. If I could run that command with a file as an argument and get back the file's location that would be good, but as it stands 'pwd' doesn't help me.

I also don't understand what's wrong here. In this code

for i in $(ls -R); do
echo $i
done

It prints out file1, file2, and then file3 and file4, both located in a folder. If I say
[-f $i] && echo $i

It will only print out the files in the main directory and I won't see file3 and file4. Why is this happening?

---

### Post by slavik on 2007-08-12
ls -r doesn't print the full path I think.

it only does something similar to this:

/:
file1
file2
/opt/:
file3
file4

---

### Post by jimmymus on 2007-08-13
This is what I have now

#!/bin/bash

for i in $(ls -R); do
if test -f $(find ./ -name $i); then 
echo $(find .  -name $i)
else
echo "$i not a file"
fi

done

The files within any directory but the current working directory were not being recognized as files because they were being tested without their full path and thus not recognized as files. When I added $(find ./ -name $i) then it would test the output of find, which contains the full path. 

However, there are two problems with this approach. One, is that find is a pretty slow way of traversing all these files one by one. If there were 1000 files in the folder that would take a while. And two, when find gets an argument that it can't handle it spits out this big long error paragraph thus making the output of this program sloppy and unusable. I tried to do

$(find ./ -name $i 2>/dev/null) to pipe stderror to /dev/null but it not only doesn't work but it breaks what little of the program does work. I 'm too new at this to debug the piping so I just pulled that bit out.

So that's where I'm at right now.

Thanks guys!

---

### Post by slavik on 2007-08-13
you can do something along the lines of:

func blah
cd $1
for i in ls; do
if test -f $i then
do something
elif test -d $i then
func $i
fi

basically, traverse the directories yourself recursively

---

### Post by Mr. C. on 2007-08-14
```
find . -print
```

MrC

---

### Post by dscherry on 2007-08-14
> **Mr. C. said:**
> ```
find . -print
```

MrC
find . -print > textfile.txt

I know this is picky, but the OP wanted a text file.
Dan

---

### Post by Mr. C. on 2007-08-14
The OP knows how to perform redirection:

> I know how to output things into a file, like this
ls -R >list.txt

MrC

---

### Post by dscherry on 2007-08-14
> **jimmymus said:**
> 
I know how to output things into a file, like this
ls -R >list.txt

but I'm doing this in a for-loop. Can I just add stuff onto the next line of a file? If I add >list.txt into my program won't it just create a file called list.txt with one file location in it, then recreate the file with another location in it? Etc etc?


MrC...
Not trying to take anything away from your solution - it's spot on!  
The second half of the OP's comment about redirection made it sound like he wasn't sure where to put the redirection (or whether to use something else).  So I clarified.

Sorry if you felt I was slighting your reply.  Definitely was not my intention.

Dan

---

### Post by Mr. C. on 2007-08-14
No problems.

---

### Post by jimmymus on 2007-08-14
Laugh, that's pretty damn elegant. Thanks for that. I'm going to work on the program pretty full on for a while and see if I can't finish it with that handy tidbit.

So many shell tools, so little time..

---


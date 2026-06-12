---
title: "Read line in a file then delete it in BASH."
date: 2010-03-04
forum: Programming Talk
---

### Post by Tristanm1 on 2010-03-04
I am attempting to add to a script I am working on. What I want to do is read a line from a file, work with the line from the file, then delete the line from the file. 

My test code looks like this: 
```
#!/bin/bash

cd ~/Desktop
$TEXT=`head -1 test.txt`
echo "$TEXT"
awk 'FNR>1' text.txt
```

the test text file holds:
```
Testing, testing.
Don't print this!
```

Unfortunately, this code returns the following errors:
```
./test.sh: line 4: =Testing,: command not found

awk: cmd. line:1: fatal: cannot open file `text.txt' for reading (No such file or directory)

```

The file is in the same directory I am executing the script from, which is also the same directory as the script itself. As for line for, that is where I am attempting to hold the first line of the file in a variable.

---

### Post by sisco311 on 2010-03-04
$TEXT is the VALUE of the TEXT variable. ;)
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html)

---

### Post by Tristanm1 on 2010-03-04
The only thing I see in that link is to change "$TEXT=`head -1 test.txt`" to "$TEXT=$(head -1 test.txt)"

That does not change any of the errors at all.

EDIT: Wait. I see the mistake on that line. Damn, that's like missing a semicolon in a C-based language.
EDIT2: Awk's error is still there. It can't find the file even though it should be able to no problem.

---

### Post by sisco311 on 2010-03-04
> **Tristanm1 said:**
> 
EDIT2: Awk's error is still there. It can't find the file even though it should be able to no problem.

it's a typo in the file name. shouldn't it be test.txt & not te**x**t.txt?

---

### Post by Tristanm1 on 2010-03-04
Yeah, I found that and fixed it. That's what I get for programming late night. 

The only problem I have is that awk isn't actually removing the line from the file. As it is, it prints the second line to the screen while not deleting the first from the test file. All I need is a command that will delete the first line from a text file.

```
#!/bin/bash

cd ~/Desktop
TEXT=$(head -1 test.txt)
echo "$TEXT"
awk 'FNR>1' test.txt
```

---

### Post by sisco311 on 2010-03-04
```
sed -i '1d' test
```

I hope this isn't your homework. :)

---

### Post by Tristanm1 on 2010-03-04
No, this is a script to help make converting videos easier. At the moment it has no way of knowing if it has been stopped or not. The idea is that it will keep a file with all the files to convert instead of just iterating over everything in the folder like it currently does. That way, if the script is stopped, it can start from the file it was on later instead of beginning at the first file again. I just haven't really done any bash scripting and it's late night, so the learning is a bit sloppy at the moment.

Currently, I have a quick, dirty addition of having it move the source files once it's converted them, but I do not like that approach. Having it make and check for a resume file containing a list of filepaths would be a better approach than moving the video files around.

---

### Post by Tristanm1 on 2010-03-05
Well, the script is put together and everything seems to work except for the fact that it doesn't break out of the loop when there is nothing left in the file. I have attempted to account for whatever could be at the end of the file with the following conditional: ```
while [ FILE != "" ]||[ -n FILE ]||[ FILE != " " ]||[ FILE != "\n" ]
```
Obviously the end of file doesn't meet any of those conditions.

The variable FILE is obtained by storing the results of using head to obtain the first line from the file. That line is then deleted once it's been used from the file.

---


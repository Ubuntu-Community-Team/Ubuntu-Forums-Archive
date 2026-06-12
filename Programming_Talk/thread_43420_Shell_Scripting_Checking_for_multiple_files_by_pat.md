---
title: "Shell Scripting: Checking for multiple files by pattern"
date: 2005-06-21
forum: Programming Talk
---

### Post by audax321 on 2005-06-21
I have a problem with my shell script for nautilus. I need to have it check and see if *.par2 files exist in the current directory. I can do this with:

```

if [ -f *.par2 ]

``` 

if there is only 1 par2 file in the current directory, but in some cases there are more and in those cases the above if statement return false. Is there a way to get the if statement to return true no matter how many *.par2 files there are and also a way to find out how many *.par2 files there are?

Thanks  :)

---

### Post by audax321 on 2005-06-21
I think I found another way to do it. I got it to output the list of par2 files, but now I need to add them all together and insert spaces where appropriate to it is a list as follows:

file1.par2 file2.par2 file3.par2  and so on... Here is my code:

for i in *.par2
do
    if [ -f "$i" ]; then
        PAR2_LIST="$PAR2_LIST" + " " + "$i"
    fi
done

I'm not sure how to add those strings together....  :-|

---

### Post by cwaldbieser on 2005-06-21
What about something like:

```

rval=false
for file in *.par2; do
   if [ -f "$file" ]; then
      rval=true
      break
   fi
done
#rval is either true or false at this point.

```

---

### Post by audax321 on 2005-06-21
Thanks, that worked, but then I found out it didn't because the par2 program refuses to check more than 1 par during any one run... what a waste of time....

Oh well, I guess I'll just have to run the pars individually. I was hoping I could get it to check all the pars in one run, but I guess thats not going to happen.   :mad:

---

### Post by LordHunter317 on 2005-06-22
You could just say:```
for i in *.par ; do par "$i" ; done
``` to run a par command per file.

---


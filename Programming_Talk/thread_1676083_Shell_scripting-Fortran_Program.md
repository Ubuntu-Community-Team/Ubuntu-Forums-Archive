---
title: "Shell scripting-Fortran Program"
date: 2011-01-26
forum: Programming Talk
---

### Post by madtowneast on 2011-01-26
Hi all,

I am in a little bit of a pickle. I am trying to write a shell script that will run through a data analysis fortran program automatically. 

The problem is that the fortran program has a lot of individual steps that prompt the user for input. For example,  you need to input selection if you want to run in an interactive or batch mode, then which data channel to analyze, etc. I wanted the program to loop through the data channels and basically do the same task over and over again. 

I have been digging through google, but cant seem to find what I need esp. with waiting for the program to prompt the user for an input and all.

Thanks for any input.

---

### Post by K.Mandla on 2011-01-26
Moved to Programming Talk. ;)

---

### Post by smo0th on 2011-01-26
got this from [here]("http://www.tolmol.com/gp/linux-system-administration/interactive-shell-script-ask-for-user-inputaction.htm"):

```
echo "How are you feeling today? ( good/bad ) : "
read response
if [ "$response" = "good" ] || [ "$response" = "GOOD" ]
then
echo "Great to know that. Keep your spirits up!"
else
echo "Sorry, hope you feel better soon"
fi
```

---

### Post by madtowneast on 2011-01-26
> **smo0th said:**
> got this from [here]("http://www.tolmol.com/gp/linux-system-administration/interactive-shell-script-ask-for-user-inputaction.htm"):

```
echo "How are you feeling today? ( good/bad ) : "
read response
if [ "$response" = "good" ] || [ "$response" = "GOOD" ]
then
echo "Great to know that. Keep your spirits up!"
else
echo "Sorry, hope you feel better soon"
fi
```

Sorry I meant that the fortran program is prompting the user not the shell script. The input into the prompts from the fortran is basically always the same besides the channel number, which I plan to change using a for loop, btw. 

I edited the original post to make it clearer. Sorry about the confusion

---

### Post by apmcd47 on 2011-01-26
I would have thought *expect *is the tool you are looking for, however I always found the documentation difficult to understand.

Andrew

---

### Post by MadCow108 on 2011-01-26
there is also a python version of expect
[http://www.noah.org/wiki/pexpect](http://www.noah.org/wiki/pexpect)
I find it simpler than the tcl version

---

### Post by madtowneast on 2011-01-27
Thanks for the info guys. I will look into the options.. I am really like the python solution, since my post-processor is already written in python, so maybe i can combine the two.

Cheers

---

### Post by madtowneast on 2011-01-27
I found that the EOF command to actually does the job pretty well. Now I just need to deal with the for loop in tcsh shell.... which leads me to another question... I am trying to cp a file into a different directory as well, but the original filenames are numbered p00, p01, p02, ...p34, p35 ( I hope you get the trend) and I am wondering how to get the 0 from the numbers less than 10.

---

### Post by Arndt on 2011-01-28
> **madtowneast said:**
> I found that the EOF command to actually does the job pretty well. Now I just need to deal with the for loop in tcsh shell.... which leads me to another question... I am trying to cp a file into a different directory as well, but the original filenames are numbered p00, p01, p02, ...p34, p35 ( I hope you get the trend) and I am wondering how to get the 0 from the numbers less than 10.

Do you mean like this?

```
$ echo p03 | sed 's/p0/p/'
p3

```

---

### Post by madtowneast on 2011-01-28
More something along the lines of:

```

i5r05_9hst-p00_2011-01-27_17-46-45.88.data
.
.
.
i5r05_9hst-p35_2011-01-27_17-46-45.88.data
```

I have got it to work using 

```

cp ./$1_plots/data/$1_9hst-p{0,1,2}{0,1,2,3,4,5,6,7,8,9}_${D}_*.data $HOME/Users/riedel/iceanalysis/
```

but it cant rename the files for some weird reason, which I am trying to figure out right now.

---


---
title: "Need help with simple shell script"
date: 2009-02-12
forum: Programming Talk
---

### Post by geo909 on 2009-02-12
Hello everybody,

I amnot familiar with shell scripting, and I would
really appreciate any help on this..

I have made a program who takes as an input a .txt file (of a certain form) and whose output ends like this:
```

.
.
.
Total steps:
48469
Status:
Solution found
Running time:
60000.000000

```

I have to try this program with many files and make a table with the results for each file, so we will compare it in class with the other students and talk on the results. Anyway, nobody likes copy-pasting and 
I think I should start learning some shell scripting anyway.

What I want to do is to make a small script that does this:

I will have a folder with my executable and all the files which I have to try as inputs for my program. I want my shell script to generate a Latex file (no help on Latex needed, please keep reading!) with a cute table with the results. Then I will send it out to the other students, saving 30 minutes of their time and making myself more popular and cool :) Very generally, it will work this way:

Pseudocode:
```

FOR (each file X in the folder that ends in .txt) DO
execute my program with input file X.
Var_1 <- last line of the output
Var_2 <- Line 3 from the end of output
Var_3 <- Line 5 from the end of output

echo " (appropriate latex code with Var_1, Var_2, Var_3 inside) "

END DO


```

So what I really want to know at this moment is how I do this 
"for every file in folder do", and how do I grab certain lines from my text.
Using the tail command will grab all the lines from the end. I only want those particular ones..

Thanks very much in advance!!

---

### Post by ghostdog74 on 2009-02-12
please read the bash link in my sig for a start.

---

### Post by geo909 on 2009-02-12
Thanks a lot!
I think I will manage to do the "for every file in folder do" thing, I already found something.
Though I do need some help on how I am going to grab a line and put it in a variable.

How do I grab a certain line from the end?

Thanks again

---

### Post by mkrahmeh on 2009-02-12
sorry am behind a windows system, but i can recall the follwoing:
for executing a command for all files in a given folder
```
for d in `ls *path*`
do
*command $d*        
done
```

generally speaking, if you are looking for files with certain type like .txt, but you have to be sure that their file names are annotated with .txt
```
find *path* -name *.txt | xargs *command*
```
but if file names do not end with .txt, there is another method for that..
anyway, note that in the latter approach the command is handed without arguments, since it will be executed upon the results returned by the find command

hope i helped, though having a shell at hand would help me check my answers :)
good luck

---

### Post by mkrahmeh on 2009-02-12
about grabbing a line in a file, its simple:
```
cat *file* | grep *keyword*
```
where keyword can be any word that you would be certain that the line will contain..better yet, it can be a regular expression

if you are strcit about grabbing the line from the lines at the end of the file, you may
```
tail *file* | grep *keyword*
```

you may add the -i flag to the grep for case insensetive grepping, along with many other options, consult the manual for grep

---

### Post by geo909 on 2009-02-12
Thanks very much!

I will try what you say, though the grep command is really not what I am looking for.
There's nothing to "grep" in these lines, it will just be a number,.
So I would prefer something more accurate like "grab line 3 from the end".
The Tail command is close, but it grabs all 3 lines from the end, which is not what I want either..

---

### Post by geo909 on 2009-02-12
I am almost done! There are only 2 things left to finish, please help guys!!

1) I understand how I use find and grep to show all the *.txt files, but how am I going to use that to do "for every file in folder that ends in .TXT do"?

2) I still haven't found how do I grab "lin n from the end". There must be a unix command for this, right?!

---

### Post by geo909 on 2009-02-12
OK, I found what I wanted to find.
For some reason the thread cannot be mark as solved.

---


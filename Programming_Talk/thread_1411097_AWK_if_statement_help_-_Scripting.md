---
title: "AWK if statement help - Scripting"
date: 2010-02-19
forum: Programming Talk
---

### Post by davidhusker on 2010-02-19
Ok well i have been sitting here trying to read and figure out why i cannot get this working and i hope someone out there can help out. Here is the story:
 
I have a file, say file.txt
in file.txt is this:
 
>  
4000 1 5 4 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1
4000 1 6 1 0.0 0.0 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.0 0.2
4000 1 6 2 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3
4000 1 6 3 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3
5000 1 6 4 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1
5000 1 7 1 0.0 0.0 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.0 0.2
5000 1 7 2 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3
6000 1 7 3 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3
6000 1 7 4 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1
 

 
I have an awk statement
 
> awk '/4000.......4/ {print; print " 3500 1 5 5 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 6.6"; next} {print}'
 
Basically my goal is for awk to insert a new line in the file after it matches my string.
 
This works when i run it from the command line
 
> awk '/4000.......4/ {print; print " 3500 1 5 5 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 6.6"; next} {print}' file.txt
 
I want to have this inside an if statement, so that i can have it search and replace after different things. I haven't figured this out. For example something like
 
> 'if (/**4000**.......4/) {print; print " 3500 1 5 5 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 6.6"; next} {print}
 
else if (/**5000**.......4/) {print; print " 3500 1 5 5 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 6.6"; next} {print}
 
else if (/**6000**.......4/) {print; print " 3500 1 5 5 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 6.6"; next} {print}
 
On top of this, i want to have this inside a script, so from the command line i can just say
./newscript file.txt
OR
awk -f awkfile file.txt
 
in the end, the file should be like 
 
> 
4000 1 5 4 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1
[B]4000 1 6 5 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3
[/B]4000 1 6 1 0.0 0.0 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.0 0.2
4000 1 6 2 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3
4000 1 6 3 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3
5000 1 6 4 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1
**5000 1 6 5 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3**
5000 1 7 1 0.0 0.0 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.0 0.2
5000 1 7 2 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3
6000 1 7 3 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3
6000 1 7 4 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1
[B]6000 1 6 5 0.1 0.1 0.6 0.6 0.6 0.5 0.5 0.5 0.6 0.6 0.6 0.1 0.3
[/B]
 
 
It still needs to print out what was originally there. Can't figure this out. I have so far
 
> 
{
if (/4000.......4/)
{print; print "         4000 1  5  5   0.0   0.0   0.0   0.0   0.0   0.0   0.0   0.0   0.0   0.0   0.0   0.0   6.6"; next} {print}
else if (/5000.......4/)
{print; print "         5000 1  5  5   0.0   0.0   0.0   0.0   0.0   0.0   0.0   0.0   0.0   0.0   0.0   0.0   7.7"; next} {print}
}

 
This only outputs the line before and the new line??
 
I do not know much about this bash/shell/awk/sed stuff, but if anyone has some help or ideas, they'd be much appreciated, thanks.

---


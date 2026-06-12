---
title: "How do I do this in a bash script?"
date: 2011-04-12
forum: Programming Talk
---

### Post by CaptainMark on 2011-04-12
If a have a variable called $file which is a string of '/media/mark/Documents/file1' what syntax should i use in a bash script to keep this exactly as is but make a second string called $file2 which is '/home/mark/Documents/file1' basically i need to copy the string and alter the start of the copy, i have no idea how to do it, i tried playing around with sed but couldnt get it.
Its probably easy work for a pro bash scripter but im a beginner so please keep it simple for me,
Thanks

---

### Post by stchman on 2011-04-12
BASH does not have very powerful String parsing but you can use PERL or create a Java program.

---

### Post by Vaphell on 2011-04-12
```
file='/media/mark/Documents/file1'
file2=$( echo "$file" | sed 's:^/media/:/home/:' )
file3=${file/\/media\///home/}

echo "$file2"
/home/mark/Documents/file1

echo "$file3"
/home/mark/Documents/file1

```

^ in sed makes sure it's in the beginning, bash solution replaces /media/ with /home/ anywhere

---

### Post by BkkBonanza on 2011-04-12
file2=/home/${file1#/*/}

The # operator deletes the first shortest matching portion of string. In this case I use /*/ to match any first level directory but you could be more specific with /media/

Likewise the % operator can be used to delete a matching portion off the end of a string.

---

### Post by PapaNerd on 2011-04-13
And the awk version would look like this:```
echo "/media/mark/Documents/file1" | awk 'BEGIN {FS=OFS="/"} {$1="/home"; print $0}'
```

---

### Post by DaithiF on 2011-04-13
or you can use bashs string substitution command:

```
$ f='/media/mark/Documents/file1'
$ echo ${f/media/home}
/home/mark/Documents/file1
```

man bash | less +/"Pattern substitution"

---

### Post by CaptainMark on 2011-04-13
Thank you all, I will try vaphells method as id like to understand sed better, it seems a very powerful tool

---

### Post by DaithiF on 2011-04-13
I didn't notice Vaphell had also included the bash version that I posted again.

Just to note that although sed is indeed a very powerful tool, its more efficient to do this within bash itself ... otherwise you are spawning a new process for sed unnecessarily.

you can achieve the equivalent of seds ^ anchoring of the pattern to the beginning of the string in bash too (using the # character):

echo ${f/#\/media/\/home}
will replace /media with /home only at the beginning of the path

---

### Post by CaptainMark on 2011-04-13
Ah okay ill take your advice then as this will be in a loop that will run several times and cpuld slow the script down

---


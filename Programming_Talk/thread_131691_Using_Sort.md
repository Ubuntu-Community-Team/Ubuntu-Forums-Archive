---
title: "Using Sort"
date: 2006-02-16
forum: Programming Talk
---

### Post by JustRandomName on 2006-02-16
Hi,

I am trying to sort a file, but due to my lack of knowledge of sort I have had to use hacky code. I have tried using the man pages, and various search querys for goole but I still can't seem to fathom the sort program.

What I want to do:

I have a file which has the following data:

===
<first name> <sir name> <misc data>

OR

<id> <misc data>

====

i.e. if there is no data about the name we use the ID.


I want to be able to sort the file by:

<sir name> <first name> <id>

In psuedo code it might be something like this:

if (name) then
  sort by <sir name> (MAJOR KEY)
  sort by <first name> (MINOR KEY)
else
  sort by <id>


I tried `sort -k 2 myfile' and this *seems* to do what I would like (order by sirname (if there is two identical sirnames, order by sirname, then firstname)

The problem lies in the <id> because this is numerical that takes precedence

e.g. instead of:
Debbie Andrews <misc>
John Smith <misc>
Steve Smith <misc>
456787 <misc>
456788 <misc>

I am getting:
456787 <misc>
456788 <misc>
Debbie Andrews <misc>
John Smith <misc>
Steve Smith <misc>

The current solution I have is very time consuming and consists of:
awk #get everything begining with <id>; ouput to tempfile
awk #get everything begining with <text>; ouput to tempfile2
sort tempfile2 > mySortedFile
sort tempfile1 >> mySorted file

Any advice, or links to a decent sort tutorial (other than man pages or implementations using awk) is appreciated.

---

### Post by thumper on 2006-02-17
My suggestion would be to use a scripting language that is good at text processing such as python, perl, or ruby to do the sorting.

---

### Post by JustRandomName on 2006-02-17
Unfortunaly I can't use a scripting language (apart from awk). Sort *Should* be able to do the trick

---

### Post by thumper on 2006-02-17
why not?

---

### Post by JustRandomName on 2006-02-17
is is major overkill, and also the system which I am going to be running this script on does not have perl/php/ruby/python/etc installed and I do not have the access level to install such a program.

---

### Post by cosmolee on 2006-12-27
I'm sure you've figured a solution out by now, since this question was posted a long time ago,  but here's for anyone else.  

Unix old timers believe that those who opt for something like Perl, etc, for text processing, just don't know their core Unix utilities, like grep, sed, awk, etc, and their Regular Expressions.  

I'm still learning this stuff, so I'm far from a guru, but I know enough to tell you that for your problem, you absolutely don't need to use those overkill programs.

Your solution requires knowledge of how to string tools together to create a solution.  This is part of the Unix toolbox philosophy, which can be paraphrased as "use existing tools, string them together to craft a specialized solution".  And it may require some cleverness and ingenuity on your part.

In the case of your problem, `sort` doesn't "do" what you want to do.  It's not always a question of whether a program "does" what you want to do, but whether you can "get it to do" what you want to do, by understanding how a program works.  

The solution would be, where records have the first two fields blank, to change content to something that sorts alphabetically after every non-blank name field.  I would guess that if you populate the blank fields to "zzzzzzz" that would do the trick.

Using 'sed' or 'awk' would do the trick.  So, each row that had blank names will now sort last on the first two keys.  The sort on the ID will kick in after the sort on the names, just like you wanted.  Then use `sed` to change the "zzzzzzz" fields back to blanks, and voila you've got your original values back!

The pipeline would look something like:

[CENTER][/CENTER]sed 'space-to-z-cmd' name_file | sort -k1 -k2 -k3 | sed 'z-back-to-space-cmd' > sorted_name_file


You've just crafted a specialized solution, for which there was previously no one program to do the job, from a few lightweight Unix tools, that run fast and light.  

No need to resort to a sledgehammer of a program like Python or Ruby to swat a fly.  

If someone tells you that you need to resort to Perl, etc, to process text, it's likely that they don't know their core Unix utilities and Regular Expressions.  The core Unix utilites ARE superb at text processing.  

Book I suggest: "Classic Shell Scripting" - O'Reilly publisher.

---


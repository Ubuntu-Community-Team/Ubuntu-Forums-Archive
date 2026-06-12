---
title: "Help whit command :: last"
date: 2011-05-25
forum: Programming Talk
---

### Post by MihaN on 2011-05-25
I have been trying to do this for 2 weeks and my eye's are starting to bleed if i wanted to
do this in C, Python or Java it would be a piece of cake but it needs to be done in Shell.

So here is what i am trying to do:
I am trying to read the wtmp  file for logged in users::

This is the standard output of "last" command.

dathvader      pts/1 :8.0    Mon May  9  09:03  - 09:23  (00:20)
dathvader      pts/1 :8.0    Mon May  9  09:03  - 09:23  (00:20)
dathvader      pts/1 :8.0    Mon May  9  09:03  - 09:23  (00:20)
jake              pts/1 :8.0    Mon May  9  09:03  - 09:23  (00:20)
superman      pts/1 :8.0    Mon May  9  09:03  - 09:23  (00:20)
warwick         pts/1 :8.0    Mon May  9  09:03  - 09:23  (00:20)

I am trying to get an output like this:

//Name     Times Loged In    Days       Hours
dathvader       3x                    1x       14:00
jake                1x                    0x        0:20

For instance dathvader logged in 3 times and was loged in for a total of 1 day and 14:00 hours, etc for each username on that list.

Here is what i have tried:

I know i can use cut to cut out part of the info i need.
So first thing i do is get rid of all the spaces and replace them whit "_"

row=$(last | tr -s " " "_")
for i in row
do                     #Here i will try to go over that list and store each username in to a           variable

name=$(row | cut -d"_" -f1) #here i store the name

Now i need 2 while or for loops 1 that will loop over the returned values calculate the
time for each user and one loop to print it all out.

---


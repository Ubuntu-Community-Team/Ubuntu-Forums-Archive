---
title: "[JAVA] Copy specified char range of an ArrayList instance?"
date: 2009-06-23
forum: Programming Talk
---

### Post by Igniteflow on 2009-06-23
I have an ArrayList, which is basically just a white space separated .csv text file read in line by line, each line being an element.  I'd like take each element, take the chars up to the first breaking white space and assign them to an array or string and then delete that content from the 
ArrayList element.  The point being to separate all the attributes into their own arrays.  Do that make sense?  Any help would be appreciated

---

### Post by froggyswamp on 2009-06-23
That sounds like homework, I think you should try and report where you failed. Googling reveals  loads of info about how to process cvs files too.

---

### Post by rocketflame on 2009-06-23
homework? c'mon, schools over!!! :)
for me anyway [Toronto Canada]

---

### Post by Igniteflow on 2009-06-25
Thanks Rocketflame, yes it isn't home work.  As I said it's a project, and this problem is but a minuscule part of it.  However, I probably should have been more clear, I had already successfully imported the .csv file and read it into the arrayList, I was just after a way to separate the information by white space.  Anyway I've done it now, to others who find themselves looking for a way to do the same thing...

*Convert an arrayList object to an array*
[PHP]arrayListNameHere.toArray(arrayNameHere);[/PHP]

*Find first white space in the array element*
[PHP]int whiteSpace = arrayNameHere[i].indexOf(" ");[/PHP]  // i is an integer signifying element number.  The space between the quotation marks can be replaced with whatever char you are looking for

*Make a string called substr and copy the contents of the array element up until the first white space to it*
[PHP]String substr = arrayNameHere[i].substring(0, whiteSpace);[/PHP]

* You can use a for loop to iterate this process, thus using i to move through an entire array

Hope this is useful

---


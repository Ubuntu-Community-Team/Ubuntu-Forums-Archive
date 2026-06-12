---
title: "how to query filesystem to get sorted entries"
date: 2010-12-25
forum: Programming Talk
---

### Post by jamesbon on 2010-12-25
My code
```

#include<stdlib.h>
#include<stdio.h>

int main()
{
    char startdir[20];
    printf("Scanning user directories\n");
    scanf("%s", startdir);
    printdir(startdir);
}


```When I check with gdb as why I do not get the desired output.

---

### Post by Arndt on 2010-12-25
> **jamesbon said:**
> I am trying to solve a simple puzzle.
Here is the puzzle
A C program to take directory name as command line argument and
print last 3  directories and 3 files in all subdirectories without using
api 'system' inside it.

suppose directory bond0 contains
bond1, di2, bond3, bond4, bond5 and my_file1, my_file2, my_file3, my_file4, my_file5, my_file6
and
bond1 contains bond6 my_file7 my_file8 my_file9 my_file10
program should output -
bond3, bond4, bond5, my_file4, my_file5, my_file6, bond6, my_file8, my_file9, my_file10



In the other thread you said last two. And why did you create a new thread?

> 
 Excerpts from man page of readdir
 
But that does not mean that it will point (or return a pointer ) to the above files in the sequence as alphabetical hence  output is not coming correctly.
Can some one suggest how do I read/query in alphabetical format.

You usually have to save all the entries from one directory somewhere first, and then sort them. But since you only want the last three, you can get away with just keeping the last three so far. If this actually becomes easier to program, I don't know.

---

### Post by jamesbon on 2010-12-26
> **Arndt said:**
> In the other thread you said last two. And why did you create a new thread?



You usually have to save all the entries from one directory somewhere first, and then sort them. But since you only want the last three, you can get away with just keeping the last three so far. If this actually becomes easier to program, I don't know.
Arndt now I want to be rude with you.Do not I repeat Do not reply to my threads.
You never reply any thing which makes sense.Your messages just increase your post count.You do not have any knowledge of programming or filesystem development etc.

Some one who genuinely might be willing to reply because of your non sense they will loose track of what I ask.So Arndt I repeat you do not reply and that is exactly the reason I opened the thread.
Your messages in fact are not at all helpful.Try to work on your acceptance rate rather than telling me how to ask and how not to ask.

---

### Post by worksofcraft on 2010-12-26
> **jamesbon said:**
> Arndt now I want to be rude with you.Do not I repeat Do not reply to my threads.
You never reply any thing which makes sense.Your messages just increase your post count.You do not have any knowledge of programming or filesystem development etc.

Some one who genuinely might be willing to reply because of your non sense they will loose track of what I ask.So Arndt I repeat you do not reply and that is exactly the reason I opened the thread.
Your messages in fact are not at all helpful.Try to work on your acceptance rate rather than telling me how to ask and how not to ask.

You should not take it so personally JamesBond :shock:

All Arndt appears to be saying is that the system calls do not do alphabetical sorting for you. He/she then suggested you can check each one against the last ones you already recorded rather than sorting the whole lot.

Personally I would just drop the whole "C" malarkey and bung them in an STL container, because C++ supplies sort algorithms for you... anyway there is no point me saying to use C++ if you want a C solution is there? ;)

---

### Post by nvteighen on 2010-12-26
The main issue I see here is that your code is mixing the following completely different processes:

1) Gathering data from fs
2) Sorting the data
3) Presenting the sorted data

1) I haven't followed any of your previous threads, so I'm not sure what data you want to read from the fs. But that's actually irrelevant for my point: isolate that task from the rest, but return a data structure that can be used for step 2). IMO, this first step should in theory be the easiest of all, given the POSIX fs API.

Of course, the data structure that will hold the information should be very well planned. I guess that in most cases the usual dirent structure or an array of them will be enough, but maybe some cases will require you to create a tree-like structure... It depends on what you want to do. Obviously, the design of this data structure should be done in a separate place.

2) The fs doesn't care about alphabethical order. It just cares about having the tree structure right and efficiently laid down.

The sorting algorithm can be the trickiest part of all, but following my first suggestion will make it much easier than your current approach. Think it this way: you have a machine that takes unsorted stuff and spits out a sorted version of it. That "machine" will be the sorting function (and auxiliary functions that may be needed) and it should work for any instance of the data structure class you created for step 1). In other words, the sorting function shouldn't care about whether the directories you want it to sort were really read from the fs or were crafted by you.

The C Standard Library has a generic sorting function called qsort. It has an interface that may seem a bit peculiar to you if you aren't used to languages of a higher abstraction level than C. But I'm sure that alphabethical sorting can be handled using a qsort-approach.

Of course, you can implement your own sorting function. No matter what approach you use, the sorted data structure should conform to the same interface the unsorted does.

3) Presenting the data to the user should be really trivial if your data structure is correctly designed. I suggest you to create a function whose purpose is just to print directories, no matter if sorted or not, so that it's completely independent of what you did above.

Epilogue:
What I've shown here is a practical guide to the most basic programming design laws there is: create interfaces (= abstraction!). I know your program is quite trivial and can be done in a sketchy rough way that just makes it work, but as soon as you try to get into more complex things, you'll have to apply what I've told you here if you want to succeed.

---

### Post by jamesbon on 2010-12-26
> **worksofcraft said:**
> You should not take it so personally JamesBond :shock:

All Arndt appears to be saying is that the system calls do not do alphabetical sorting for you. He/she then suggested you can check each one against the last ones you already recorded rather than sorting the whole lot.

Personally I would just drop the whole "C" malarkey and bung them in an STL container, because C++ supplies sort algorithms for you... anyway there is no point me saying to use C++ if you want a C solution is there? ;)
I can not comment on any thing you said above.While searching this problem I came across a system call  scandir and I found a method alphasort which does exactly what I have been asking.I expected such reply from Arndt.
My previous posts have been foolish enough to ask basic C syntax because of which most of the people got an idea that I was not good at C.I am not an expert at it.The problem is if you post such silly things on some ones post any one who might be willing to reply might get an idea that this is not an important thread and they might not reply.


> **nvteighen said:**
> 

The C Standard Library has a generic sorting function called qsort. It  has an interface that may seem a bit peculiar to you if you aren't used  to languages of a higher abstraction level than C. But I'm sure that  alphabethical sorting can be handled using a qsort-approach.

Ok I did not knew this.

 > **nvteighen said:**
> 
What I've shown here is a practical guide to the most basic programming  design laws there is: create interfaces (= abstraction!). I know your  program is quite trivial and can be done in a sketchy rough way that  just makes it work, but as soon as you try to get into more complex  things, you'll have to apply what I've told you here if you want to  succeed.
I will keep it in mind I am right now working on this problem.

---

### Post by Arndt on 2010-12-26
> **jamesbon said:**
> I can not comment on any thing you said above.While searching this problem I came across a system call  scandir and I found a method alphasort which does exactly what I have been asking.I expected such reply from Arndt.


As a matter of fact, I wasn't aware of 'scandir'. As for the rest of what you have written, I'm sure others will form their own opinion.

---


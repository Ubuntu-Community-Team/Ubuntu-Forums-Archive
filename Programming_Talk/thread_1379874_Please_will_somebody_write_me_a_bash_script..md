---
title: "Please will somebody write me a bash script."
date: 2010-01-13
forum: Programming Talk
---

### Post by ron999 on 2010-01-13
.

---

### Post by Locutus_of_Borg on 2010-01-13
we're going to need more information

like, what does the original file contain?

a list of names? how can the second file get the mailing address from a list of names?

an example of what the file actually looks like will probably be needed

---

### Post by cong06 on 2010-01-13
You should use perl instead of bash.
But since bash is easier to test, I can't really recommend against it.

Check out echo, cat, etc.
Maybe even try a search: [http://www.google.co.ke/search?q=editing+files+with+bash](http://www.google.co.ke/search?q=editing+files+with+bash)

Advanced scripting guide: [http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)
Perlintro: [http://perldoc.perl.org/perlintro.html](http://perldoc.perl.org/perlintro.html)

---

### Post by chewearn on 2010-01-13
This is a simple problem, and I have the script done shortly.  But I am not going to post the script just yet, because I hope you are not trying to get us to do your homework for you.

So, please convince us this is a genuine request. ;)

---

### Post by slooksterpsv on 2010-01-13
Wow, that took me a bit, you can do it in 4 lines of bash scripting. --EDIT Oops theres' more to the program than that, well I did some stuff in 4 lines, the rest, not yet.

If you need hints let me know, I found all the info on the pages listed above.

We'll here's a hint if you'd like it

>>

EDIT:

I hope you see we're not trying to be mean, but trying to help. It takes some critical thinking to figure out these kinds of problems. Try to make it into a longer explanation for example:

Ms. Peterson needs to enter data into her computer, she needs me to read each line while she types in the information. The information she's putting in will be if the customers title as well as if they have paid their bill. We're doing this until we've went through our list.

Cut it down, take out the basics:

She needs me to read each line.
She's inputing the information.
The information contains title name and if they've paid
Go through each line until list is done.

Then form it:
.... well that would give the answer so I'll stop there, call it hint 2

---

### Post by renkinjutsu on 2010-01-13
how does the script know that the clients have paid? or is it just supposed to mark paid for everyone?

---

### Post by lisati on 2010-01-13
> **renkinjutsu said:**
> how does the script know that the clients have paid? or is it just supposed to mark paid for everyone?

+1 A good question that occurred to me too! :)

---

### Post by ron999 on 2010-01-13
.

---

### Post by ron999 on 2010-01-13
.

---

### Post by ron999 on 2010-01-13
.

---

### Post by dwhitney67 on 2010-01-13
> **ron999 said:**
> Bump again.

I need some help here.

How can you expect anyone to help you?  So far...

1.  You have failed to answer all of the questions posed concerning your assignment?  For example, where does (do) the company address(es) come from?

2.  You have not really indicated if this is for a homework assignment;

3.  The code you presented contradicts some of the requirements (ie. those related to the hash marks) indicated in your opening post.

The assignment you have is really trivial; almost sounds like a class exercise.  Thus I hope your BS skills are up to par and you can entertain us when you attempt to answer item 2 above.

---

### Post by slooksterpsv on 2010-01-14
Here's another hint:

You need to read each line from the file.

---

### Post by ron999 on 2010-01-14
Thanks for nuthin' community.

**[SIZE="5"][SOLVED][/SIZE]**

---

### Post by dwhitney67 on 2010-01-14
> **ron999 said:**
> Thanks for nuthin' community.

**[SIZE="5"][SOLVED][/SIZE]**

You are most welcome!

---

### Post by lavinog on 2010-01-14
> **dwhitney67 said:**
> 
The assignment you have is really trivial; almost sounds like a class exercise.  Thus I hope your BS skills are up to par and you can entertain us when you attempt to answer item 2 above.

This is probably why the OP deleted his posts.

---

### Post by d3v1150m471c on 2010-01-14
> **ron999 said:**
> .

copy this to your gedit and save it your home folder as the name "wtf":

#!/bin/bash
# This is a bash script
firefox [http://en.wikipedia.org/wiki/Bash](http://en.wikipedia.org/wiki/Bash)
echo " Note to self....Google is my friend"
ext 0

Now right click the file in your home folder and set the permission to "allow this to run as a program"
OR... in your terminal type chmod +x wtf

in your terminal type:

./wtf

enjoy

---

### Post by chewearn on 2010-01-14
I pretty sure the point has been made.  There is no need to rub it in. [-X

---

### Post by d3v1150m471c on 2010-01-15
;) hey at least i provided what he wanted. secondly, "hello world" is lame.

---

### Post by lisati on 2010-01-15
> **ron999 said:**
> Thanks for nuthin' community.

**[SIZE="5"][SOLVED][/SIZE]**
You're welcome!
I wish to voice curiosity on behalf of everyone who might come by this thread who didn't the original question (now edited out), as to what it was and how it was solved.
(I saw the original question and could probably have managed something in C or BASIC that accomplished the task)

---

### Post by lavinog on 2010-01-15
> **lisati said:**
> You're welcome!
I wish to voice curiosity on behalf of everyone who might come by this thread who didn't the original question (now edited out), as to what it was and how it was solved.
(I saw the original question and could probably have managed something in C or BASIC that accomplished the task)

Thanks to google:
> 
Hi
Please will somebody write me a bash script to run in Ubuntu.
This is the requirement:-

I have a text file containing a list of names. The number of entries isn't known, it will vary from day to day.
I want to generate another text file containing a reader-friendly report.

The name of the original file is foo1.txt.
The name of the generated file is to be foo2.txt.

The top line of the report is to be a heading Clients.
Then there will be 2 spare lines containing # symbols.

Then there will be a list of clients' names.
In front of each name will be his title Mr.
Following each name will be the letter P to show that he's paid his bill.

At the bottom of the list will be 2 more spare lines containing # symbols.
Then there will be 3 lines of text showing the company's mailing address.

For example:-

foo1.txt

Quote:
Smith
Jones
Harris
Brown
foo2.txt

Quote:
Clients
#
#
Mr Smith P
Mr Jones P
Mr Harris P
Mr Brown P
#
#
Acme Ltd
London
England


---

### Post by lisati on 2010-01-15
> **lavinog said:**
> Thanks to google:

:) I must've used the wrong search terms - I found the thread but not a cached copy of the original post.

---


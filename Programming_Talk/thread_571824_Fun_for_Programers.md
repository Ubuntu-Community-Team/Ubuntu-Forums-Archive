---
title: "Fun for Programers"
date: 2007-10-09
forum: Programming Talk
---

### Post by oneadvent on 2007-10-09
Here is a fun one:

Write a shell script to do the following:

Append a file we'll name: scriptfun.txt
with the following information:
Date
[1st query] {TAB} [2nd query]

The querys are based on the total count of product1 (1st query) and the total count of product2 (2nd query)
The data base is /usr/task/task

The goal is to have this append the file every day, so there is a running total.

Good Luck those who dare to try.

---

### Post by Wybiral on 2007-10-09
lol. Do your own homework.

---

### Post by ryno519 on 2007-10-09
> **Wybiral said:**
> lol. Do your own homework.

Haha. That's what I was thinking. I remember doing something similar back in college.

---

### Post by Nekiruhs on 2007-10-09
Care to explain more about the database? How does it work? I dont have a /usr/task/task

---

### Post by oneadvent on 2007-10-09
> **Nekiruhs said:**
> Care to explain more about the database? How does it work? I dont have a /usr/task/task

sure. what do you need to know?

And by the way, I'm not in college, and this is no assignment. I was trying to figure it out, and couldn't. 

The database is an informix database. That is the location. The actual query is a little different than the one I was thinking though.

Good Luck!

---

### Post by Nekiruhs on 2007-10-09
I am not sure you can do this in BASH. I dont thing BASH is capable of accessing databases. Get on yahoo, talk to me there.

---

### Post by yabbadabbadont on 2007-10-09
It it is an Informix database, then how about using ESQLC for your program?  Assuming that you know C, then it is pretty straight forward.  (at least it was when talking to informix on HP-UX ((back in the 90's)))

---

### Post by oneadvent on 2007-10-09
I dunno what that is. The majority of the programs on the machine are in 4gl, but I was trying to do it in script just because its cool.

Sounds like we cant do it in script?

---

### Post by nss0000 on 2007-10-10
I dunno ....

Some recent papers using fMRI have demonstrated single neurons SHORTING-OUT when a patient attempted to read BASH-script. Similarly increased PRION production was observed in coders attempting to do any form of maths in BASH. 

OTOH a form of the "happy neuron syndrome" was reported in patients coding C-pointers. YMMV

---

### Post by pmasiar on 2007-10-10
But other research shown beta-amyloid plaques forming in inter-neuronal space after heavy use of {} and static typing, substantially decreasing dendrite activity. Best solution seems to be rely on plain whitespace for structuring your code. Also having fun while coding is important - it improves outcome and reduces burn-out significantly. :-)

BTW nss0000 I liked your joke.

---

### Post by oneadvent on 2007-10-10
The goal is to avoid doing it in 4GL or c or whatever. The goal is to do it in BASH. 

Personally, I thought this would be an easy one....however it looks like it is stumping the masses......

When I get it down, I will post the code. 

Josh

---

### Post by oneadvent on 2007-10-10
Ok, for anyone that is following this saga, the command to pull the information from the sql database is

```
isql -s task {sqlscript.sql}
```

So now all I need to figure out is how to get 2 queries to run and to put them in the flat file correctly.

Closer.....closer......

---

### Post by yabbadabbadont on 2007-10-10
It has been a while.  I forgot about the isql command.  We used it in quite a few korn shell scripts now that you've jogged my memory.  We needed an easy way to transfer data from the HP server to OS/2 boxes that were doing real time hardware control.  What we did was to use the isql command to create temp tables for the output and then populate them with our queries.  Then we would "unload table to 'filename'" (I think that was the syntax) to create flat files with the results.  Next we would drop the temp tables and then finally ftp the files to the OS/2 boxes.  I think we may have added an md5sum to each file as well as a sanity check.

Edit: I think there was a delimiter clause in the unload statment.  Something like
```
unload table to filename with delimiter '|'
```  We used pipe symbols for the field delimiter.

---

### Post by oneadvent on 2007-10-10
In this case we are simply counting, so we shouldn't need to have a delimiting field. 

Really what needs done now is to pull it all together.

That is the sql statement from cli, now to put it into a file and then constantly append it with more information.

Also, I think that it should do 2 more things, since I am having so much fun learning this far, it should email out to a specified email address when the count went down from the day before, and to auto delete part of itself when it gets to 25k. 

Hummm...Is this even possible?

---

### Post by oneadvent on 2007-10-10
So new stumbling block.

In order to use the sendmail command, it must be
```
#sendmail oneadvent@gmail.com
hello
There is a problem
.

```

so how can I put that in a shell script?

---

### Post by yabbadabbadont on 2007-10-10
```
#sendmail oneadvent@gmail.com << EOF
hello
There is a problem
.
EOF

```
You should probably do a search for online bash scripting tutorials.  There are many on the net as well as links to several of them in various bash threads here in the forums.  ;)

---

### Post by oneadvent on 2007-10-10
I have gotten pretty far thus far, so obviously I have been doing many searches.

Something you have to ask people not read.

Like where online is it going to show you how to compare numbers on different lines in a flat file in a script?

Remember this is for fun, not for serious. So far I have come up with the solutions myself, with the assistance of tuxincarnate

---

### Post by yabbadabbadont on 2007-10-10
> **oneadvent said:**
> Like where online is it going to show you how to compare numbers on different lines in a flat file in a script?


You can do that if you use the sed utility properly.  Exactly how, is left as an exercise for the student...  :D

Edit: and since there is always more than one way to do something in linux, you could also use the head and tail utilities to accomplish it too.  ;)

---

### Post by oneadvent on 2007-10-10
Ok, I think it is update time for the group:

Here is the parent code:

```

#!/bin/bash
#get the total number of records in the survey and listmaster tables. and then
#eventually to email out when the number in them goes down. Hummmm....

`date +%m/%d/%Y >> agoodone.josh`
echo "date done"
`isql -s task surveylist.sql >> agoodone.josh`
echo "counts done"
`mailing.sh`
echo "email sent"
exit 0
```

here is the sql query:
```

select count(*) from tlgi_survey;

select count(*) from listmaster 
```

and here is the mail perl code:

```

#!/usr/local/bin/perl
print "Content-type: text/html\n\n";
open (MAIL, "|/usr/lib/sendmail -t");
print MAIL "To: oneadvent\@gmail.com\n";
print MAIL "From: Noble.System\@tlgi.com\n";
print MAIL "Subject: The Listmaster-survey count is off\n\n";
print MAIL "There has been a decrease records in one of the tables.\n";
close (MAIL);
print "Message sent";
exit; 
```

so whats left? 

The sed command, which looks daunting, and the size of the file command, which seems easy enough, using heads and tails.

---

### Post by farruinn on 2007-10-10
If you really enjoy learning bash and would like to learn sed, I strongly recommend you get the relevant books from O'Reilly. They are indispensable. Also, if I were trying to do this I would try to do it all with one tool instead of mixing bash and perl and sed. Perl is tons of fun and can do basically anything bash and sed can do. Get the O'Reilly book for that one too! :)

Happy coding.

---

### Post by oneadvent on 2007-10-10
very good. I will look into that, but immediately I would like to learn to do this in script. (I had to use perl only because of that statement)

I have been looking at sed, and I seriously do not think that it can do what I want it to do. the end result of this in a flat file looks like:
```

10/09/2007
count(*)

11150000

count(*)

1251051
10/10/2007
count(*)

11250000

count(*) 
1251052 
```

how could i possibly do arithmatic with that?

'xcuse the spelling

Josh

---


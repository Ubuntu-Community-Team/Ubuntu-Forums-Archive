---
title: "[SOLVED] Need Urgent help in awk ..."
date: 2008-06-08
forum: Programming Talk
---

### Post by umshiva on 2008-06-08
Hi Buddies ,

I have a problem in awk 
I am a newbie to scripting 
and I need a awk program to satisfy my requirement.. i am working in UNIX not linux 


FILE1

CCC | Co Operative
DDD | Demo

FILE2
p898735 20080202 CCC
p267354 20080605 DDD

My output should be

FILE3 

P898735 20080202 Cooperative
P267354 20080605 Demo

File 2 has 400 + entries as such , so my script should search file 2 with File1 entries and Create file 3 which has the req output

Thanks a lot  in advance

---

### Post by HalPomeranz on 2008-06-08
I could script this easily in Perl.  Is awk an absolute requirement?  Also, should file3 only contain the lines from file2 that match a file1 tag, or should the program output every line of file2 making substitutions where appropriate?

---

### Post by umshiva on 2008-06-08
Hi HAl,

Buddy Thanks for the fast reply .... 

And I need awk program only ... perl is not supported on my work environment

And , 

Script should compare Field 1 of file 1 (ie CCC or DDD) with Feild 3 of FILE2 (ie CCC or DDD) 

if it matches, then Feild3 of FILE2 should be replaced with Feild2 of FILE1 

Ie if FIl2 Contains CCC then it should be replaced by co operative which is read from file 1

Thanks for the reply ...    

Thanks a lot in advance

---

### Post by HalPomeranz on 2008-06-08
No Perl?  Boo!  :-)

Here's an ugly shell script hack to do what you want:

```

#!/bin/bash

cp file2 file3

IFS=' |'
while read tag sub; do
    sed "s/$tag/$sub/" file3 >file3.new
    mv file3.new file3
done < file1

```

---

### Post by umshiva on 2008-06-08
Hi hal ,


It worked fine .... 

Thanks a lot

---

### Post by umshiva on 2008-06-08
Hi HAl,

I have someother req now ,,


FILE1
CCC|co oerative 
DDD|Demo
FFF,GGG | FIrst release

Now i need to check file2 for occurences of FFF or GGG and replace First release , can you modify your script to meed this req , i am also tryin here ... this is urgent ... i am new to scripting.

And if you have some doc to learn awk send me the link for those please or mailme at [email]umshiva@gmail.com[/email]


Sorry Buddy i forget to mention this earlier

Thanks a lot

---

### Post by Inxsible on 2008-06-08
since when did this forum become a place to get your work done by someone else???

Looks like the op joined the forum just for this question...seeing that he has only 4 posts until now.

---

### Post by HalPomeranz on 2008-06-08
```

#!/bin/bash

cp file2 file3

IFS=' |'
while read tag sub; do
    for elt in `echo $tag | sed 's/,/ /g'`; do
        sed "s/$elt/$sub/" file3 >file3.new
        mv file3.new file3
    done
done < file1

```

I believe O'Reilly and Associates publishes some good books on both awk/sed programming and shell scripting (ora.com).

---

### Post by cariboo on 2008-06-08
I guess since the Linux Gazette stopped answering home work questions they have to come somewhere to get it done :)

[http://linuxgazette.net/](http://linuxgazette.net/)


Jim

---

### Post by HalPomeranz on 2008-06-08
> **Inxsible said:**
> since when did this forum become a place to get your work done by someone else???

Looks like the op joined the forum just for this question...seeing that he has only 4 posts until now.

What does it hurt to try and help, regardless of the original poster's motives?  It's not like it took hours to develop the code, and besides it was an interesting programming challenge.  Maybe other people reading the thread will learn something as well.

---

### Post by umshiva on 2008-06-08
Well said hal,
You seemed to be a good nice friend 
It worked as well, thanks for needy and timely help .... as you said its interesting language which i started learning today morning and i learn it with good pace ....

---

### Post by Sef on 2008-06-09
Moved to programming talk.

If someone asks for help after having demonstrably done most of the work, then I would not give an infraction for that.  However, if on the other hand, they want someone to do the majority of the work that would earn an infraction.

This case seemed to be the former and not the latter.

---

### Post by HalPomeranz on 2008-06-09
> **Sef said:**
> 
If someone asks for help after having demonstrably done most of the work, then I would not give an infraction for that.  However, if on the other hand, they want someone to do the majority of the work that would earn an infraction.


Playing Devil's Advocate for a moment, there's also a point where people are just starting out and have no clue how to even start accomplishing the tasks they need to accomplish.  Yet they're aware that there probably is a scripting solution.  These people need to learn from others' examples in order to get started (at least that's how I started to learn this stuff).  Simply saying, "Figure it out on your own, and then maybe we'll let you post when you've got 90% of the solution", seems unfair and unhelpful and not a good way to gain converts.

Meh.  It's over and done with, and in the time we've all spent having a meta-discussion about whether or not I should have helped the original poster we all could have been helping other people with questions.  Peace out.

---

### Post by ghostdog74 on 2008-06-09
in awk
```

awk  '
    FNR==NR{
        c[$NF]=$1" "$2
        next
    }
    {
        m=split($0,a,"|") 
        print c[$1],a[m]
    }
' file2 file1


```
output:
```

# ./test.sh
p898735 20080202  Co Operative
p267354 20080605  Demo


```

---

### Post by dtmilano on 2008-06-09
Humm...
you should get rid of extra spaces in front of the name, replace the print line by
> print c[$1] "" a[m]

Anyway, this solution it's not very flexible. Just add lines that don't match and you'll obtain undesired output.

And, it doesn't hurt to learn another Unix/Linux tool: join.
The simplest approach would be to normalize field separator to | in all files:

 > sed 's/ /|/g' < file2 > file3

then

> join -t \| -1 1 -2 3 -o 2.1,2.2,1.2 file1 file3

(you can check 'man join' to see the supported options by your join version). In this case -t to specify separator, -1 and -2 to specify join fields, -o to specify output fields and then input files.

---

### Post by umshiva on 2008-06-09
Can any you please tell me where to start a new thread today

---

### Post by HalPomeranz on 2008-06-09
> **dtmilano said:**
> 
And, it doesn't hurt to learn another Unix/Linux tool: join.


join!  That was it!  I was trying to remember the name of this tool (and "man -k" wasn't helping).  All I could find was paste, which was not the right tool...  Thanks!

---

### Post by HalPomeranz on 2008-06-09
> **umshiva said:**
> Can any you please tell me where to start a new thread today

If it's related to programming/scripting, then it should go in the "Programming Talk" forum.

---

### Post by umshiva on 2008-06-12
Hi Buddies and Hal

In My Sql script .... 

sqlplus -s / <<%% >/dev/null 2>&1
spool file1
set head off
select refn,create_date,doc_id from table1 where corr_id IN ( ${array5} );
spool off
%%

array5 contains '0005724699', '0005672326', '0005672314', '0005672312', '0005672329', '0005672330', '0005672304', '0005688526', '0005725333', '0005748569', '0005733479', '0005749525', '0005637356', '0005672323', '0005753754', '0005753532', '0005750494', '0005746371', '0005744961', '0005738777', '0005737425', '0005703417', '0005748471', '0005698857', '0005719946', '0005708550', '0005674713', '0005682373', '0005719829'

file generated by this ..... 

D210309019 20080428 CCC
FV41327608 20080411 DDD
FW02411100 20080521 DDD
G735031013 20080415 CCC
etc 

but when i use 

while read tag sub; do
    for elt in `echo $tag | sed 's/,/ /g'`; do
        sed "s/$elt/$sub/" file1 >file1.new
        mv file1.new file1
    done
done < gfile

My gfile
----------
CCC | Co-operative
DDD | Demo


My output was ..

D210309019 20080428 Co-operative
FV41327608 20080411 Demo

FW02411100 20080521 Co -operative

G735031013 20080415 Demo
etc 

i used sed to remove blank lines .... it did  not work..

cat file1|sort -u|sed '/^$/d' 

Can you tell me the solution please ..

Thanks in advance

---

### Post by HalPomeranz on 2008-06-12
Remove blank lines from files with:

```

awk '!/^$/ { print }' file1

```

---

### Post by umshiva on 2008-06-12
Hal,

It did not work buddy....

I tried most of the scripts from internet ...


I dont know whts the problem
Its weird

Can you tell me what wold be the problem or recreate my problem , so can get a clear idea

---

### Post by ghostdog74 on 2008-06-12
when you say did not work, provide error messages if any!
```

awk  'BEGIN{FS="[| ]+"}
    FNR==NR{
        c[$1]=$2
        next
    }
    {
        m=split($0,a," ") 
        print a[1],a[2],c[a[3]]
    }
' gfile file1

```
output:
```

 # ./test.sh
D210309019 20080428 Co-operative
FV41327608 20080411 Demo
FW02411100 20080521 Demo
G735031013 20080415 Co-operative


```

---

### Post by HalPomeranz on 2008-06-12
> **umshiva said:**
> Hal,
It did not work buddy....
I tried most of the scripts from internet ...
I dont know whts the problem


There's probably some whitespace on your "blank" lines.  Try this:

```

awk '!/^[ \t]*$/ { print }' inputfile

```

---

### Post by umshiva on 2008-07-29
Hi  HalPomeranz 
 
can u help me with the latest post of mine ....

thanks friend

---

### Post by mssever on 2008-07-30
> **umshiva said:**
> can u help me with the latest post of mine ....
Um, several solutions were already given and you haven't said whether they work and/or what errors there are. How can anyone help you without knowing what kind of help you need? Especially on a month+ old thread.

---

### Post by umshiva on 2008-07-30
Please help me my latest post ....... i will be much greatfukl if anyone responds

SHiva

---

### Post by mssever on 2008-07-30
> **umshiva said:**
> Please help me my latest post ....... i will be much greatfukl if anyone responds
As I stated above, you haven't said what kind of help you need, so how can anyone help you? Or do you mean you want help in a different thread? In that case, please say so and provide a link to the thread. Nobody here can read your mind.

---

### Post by umshiva on 2008-07-30
hi msserver

i have posted the thread in a below link

can you plz look into it and let me know the solution.

[http://ubuntuforums.org/showthread.php?t=873659&page=1](http://ubuntuforums.org/showthread.php?t=873659&page=1)

Topic : Need help in inserting a a row via shell script  

I thought u would search for recent posted thread and anser my query ..

Thanks a lot in advance

---

### Post by mssever on 2008-07-31
> **umshiva said:**
> i have posted the thread in a below link

can you plz look into it and let me know the solution.

[http://ubuntuforums.org/showthread.php?t=873659&page=1](http://ubuntuforums.org/showthread.php?t=873659&page=1)

Topic : Need help in inserting a a row via shell script  

I thought u would search for recent posted thread and anser my query ..
Thanks for providing the link. Usually when people refer to their previous posts, they're talking about the current thread. And since you've never stated whether the problem mentioned in this thread is solved, it was reasonable to assume the same thing. Now that you've provided a link, it's clear that you meant to refer to a different thread.

In looking at that thread, I found it difficult to figure out what you wanted. You'll have better luck getting an answer if you describe your problem, and what the result should be in detail, and in a clear, coherent manner. It also helps to use proper spelling and capitalization. I gather that English isn't your native language--and that's fine--but any spell checker will point out (for example) that *please* isn't spelled *plz*. Also, *you* isn't spelled *u* (and the time saving from silly abbreviations like that is insignificant). Misspellings and omitting capitalization make your writing much harder to read quickly.

---


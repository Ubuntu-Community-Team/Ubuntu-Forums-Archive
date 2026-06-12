---
title: "Easier in bash, python, C ? Which is quickest?"
date: 2014-04-13
forum: Programming Talk
---

### Post by freebird54 on 2014-04-13
I have a fairly simple task in mind, but am not sure what best to tackle it with.  My knowledge is insufficient to be sure of any of them!

What I want to do is resolve the following:
```

    Given: 2 times, one smaller (lesser) than the other
   Format: most often mm:ss - sometimes hh:mm:ss (minimum known :ss - maximum known h:mm:ss)
Determine: total seconds in each
Calculate: percentage that the smaller is of the larger
   Return: that percentage (on stdout) or zero

```

I can't think of any reason it cannot be done with any of them, but my years with 'C' are further in the past than I care to think about (though not beyond retrieval) - my python is non-existent (but looks easy to learn enough for this(dare I sat BASIC like?)) and bash looks like it might be convoluted to attempt at my level of familiarity with it!  On top of all that, the time and resources required should be small, as it will be called frequently.

Any suggestions/recommendations/alternatives from the experts out there? I don't want to sink too much effort and time into the wrong choice:)

---

### Post by pauljwells on 2014-04-13
**Python**, absolutely no question! Look at the 'time' module (part of the built in modules) It will handle all the conversions and the rest is just maths.

---

### Post by freebird54 on 2014-04-16
Well - I took another look at Python - and I just can't get my head around the weird ways it does things... some of them seem designed just to be different where no advantage is gained :)

Bash - still don't know enough - especially for testing purposes...

So - back to 'C' - the old-fashioned way.  A little popen(), a little strtok() and a little sscanf() took care of it. Oh - I mean the old-fashioned way - heavily commented the source is only 2.5K - and the executable is 13.4K so it shouldn't be too slow for its intended purpose.  Now to integrate its results into conky....

I'll just mark it [SOLVED] - 'cos in a way it is.

---

### Post by Vaphell on 2014-04-16
lol, how frequently do you call your prog in conky that you need C performance? :-)

in bash and python it would be like 10 lines tops.

eg bash
```
#!/bin/bash

t1=$1
t2=$2

# normalize format to h:m:s
until [[ $t1 = *:*:* ]]; do t1=0:$t1; done
until [[ $t2 = *:*:* ]]; do t2=0:$t2; done

# parse normalized time1, calculate seconds
IFS=: read hh mm ss <<< "$t1"
(( hh=10#$hh, mm=10#$mm, ss=10#$ss ))
s1=$(( hh*3600+mm*60+ss ))

# parse normalized time2, calculate seconds
IFS=: read hh mm ss <<< "$t2"
(( hh=10#$hh, mm=10#$mm, ss=10#$ss ))
s2=$(( hh*3600+mm*60+ss ))

# determine numerator, denominator
(( s1>s2?(n=s2, d=s1):(n=s1, d=s2) ))
# print percentage (rounded)
printf '%d%%\n' $(( (100*10*n/d+5)/10 ))
# print percentage (truncated)
#printf '%d%%\n' $(( (100*n/d ))

```

```
$ ./pcent.sh 59 0:0:59
100%
$ ./pcent.sh :59 1:0:59
2%
$ ./pcent.sh 29:59 1:0:0
50%
```

---

### Post by freebird54 on 2014-04-16
> **Vaphell said:**
> lol, how frequently do you call your prog in conky that you need C performance? :-)

in bash and python it would be like 10 lines tops.


Well - minimum would be about every 2 seconds, maximum would be once a second I suppose.  It is not just the performance, it is that you get the whole python interpreter loaded - however small the code!  Assuming I have that information right, of course :)

Also - the input comes from another program running, and thus I open it with a pipe from mine, then process as described.  I ended up with about 44 lines (including declarations - not including 'prettifying' and comments) so it wasn't too bad! I'm a bit hesitant to post it (showing how out of practice (and old-fashioned) I am) but I will if anyone wants to see it...

Thanks - I knew the code would be short in Python - but the process of figuring how to generate it would be long (it took me a few hours of looking through documentation to decide it wouldn't do for me for this!).  Now all I have to do is figure how to ship the answer I get over to a lua routine for display (can't find a 'user' variable in conky, and I don't know any other way yet to pass it).

On we go.....

---

### Post by Vaphell on 2014-04-16
yes, overhead might be a problem. Minimizing number of processes would be nice. So where do you get these times from?

btw, if you feel like reverse engineering to understand it, a simple python solution ;-)

```
#!/usr/bin/env python

import sys

def time2sec( t ):
    l = [ int('0'+x) for x in t.split(':') ]
    for i in range(0, 3-len(l)):
        l.insert( 0, 0 )
    return sum( 60**(2-i)*l[i] for i in range(0, len(l)) )

n, d = sorted( time2sec(p) for p in sys.argv[1:3] )

# .1: precision, %: percentage
print '{0:.1%}'.format( 1.0*n/d )
```

---

### Post by freebird54 on 2014-04-16
> **Vaphell said:**
> yes, overhead might be a problem. Minimizing number of processes would be nice. So where do you get these times from?

btw, if you feel like reverse engineering to understand it, a simple python solution ;-)

```
#!/usr/bin/env python

import sys

def time2sec( t ):
    l = [ int('0'+x) for x in t.split(':') ]
    for i in range(0, 3-len(l)):
        l.insert( 0, 0 )
    return sum( 60**(2-i)*l[i] for i in range(0, len(l)) )

n, d = sorted( time2sec(p) for p in sys.argv[1:3] )

# .1: precision, %: percentage
print '{0:.1%}'.format( 1.0*n/d )
```


 Well - simple if you know it I guess!  However, I don't see handling of 'outliers' - hour+ times...

For the laugh - here's the (old-style)  'C'
[php]
/* calculate percentage of song played for graph */

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

long elapsed, duration, length;
double percent;
char data[20];
char *times[2][10];
const char delimit[2]=" \n"; /*for strtok - split elapsed and duration - and lose the newline */

void GetData(char *data);  /*buffer for redirect ouput from rhythmbox-client */
long CalcSeconds(char *timestr, long length);

main()
	{
    /* run rhythmbox-client */
    GetData(data);
    /* split up returning elapsed and duration data */
    times[0][0] = strtok(data, delimit);
    if (times[0][0] != NULL)
        {   
        times[1][0] = strtok(NULL, delimit);
        } /*endif*/
    /* process from hh:mm:ss into total seconds */
    elapsed=CalcSeconds(times[0][0], strlen(times[0][0]));
    duration=CalcSeconds(times[1][0], strlen(times[1][0]));
    /* calculate percentage */
    percent=(elapsed*100)/(float)duration;
    /* dump result to stdout */
    printf("%3.f\n",percent);
    exit(0);	
    } /* end main */

void GetData(char *data)
    {
    FILE *pf;
    char command[100]="rhythmbox-client --print-playing-format '%te %td'";
 
    /* Setup our pipe for reading and execute our command. */
    pf = popen(command,"r"); 
 
    if(!pf)
        {
        fprintf(stderr, "Could not open pipe for output.\n");
        return;
        } /* endif */
 
    /* Grab data from process execution */
    fgets(data, 100 , pf);
 
    if (pclose(pf) != 0)
        {
        fprintf(stderr," Error: Failed to close command stream \n");
        } /* endif */
    return;
    } /* end GetData */

long CalcSeconds(char *timestr, long length)
	{
    long hr=0,min=0,sec=0,result=0;
    char *token[3][3];
    const char delim[2] = ":";
 
    /* get the first token */
    token[0][0] = strtok(timestr, delim);
    /* convert to numeric value */
    sscanf(token[0][0],"%ld",&hr);
    /* walk through other tokens */
    if (token[0][0] != NULL)
        {   
        token[1][0] = strtok(NULL, delim);
        sscanf(token[1][0],"%ld",&min);
        } /*endif*/
    /* use string length to show if hours are present */
    if (length>5)
        { 
        token[2][0] = strtok(NULL, delim);
        sscanf(token[2][0],"%ld\n",&sec);
        } /*endif*/
    else
        {
        /* move entries to correct places for value */
        sec=min;
        min=hr;
        hr=0;
        } /*endif*/
    /* calculate total seconds */
    hr=hr*3600;
    min=min*60;
    result=hr+min+sec;
    return(result);
    } /* end CalcSeconds */
[/php]

As you see, I 'split' the incoming data into 2 separate strings (I'd be using argc() and arg v() if I were running it directly), then split each in the function on the ':' before making them into numbers and sending them back for calculating.  Overcommented too - a habit from having to figure out what I did a couple of years later too often!

Thanks..

---

### Post by Vaphell on 2014-04-16
damn, quite a lot of boilerplate :-)

well, i figured out i don't need fixed 3 elem data structure so i shortened the code ;-)

```
#!/usr/bin/env python

import sys

def time2sec( t ):
    l = [ int('0'+x) for x in t.split(':')[::-1] ]
    return sum( 60**i*l[i] for i in range(0,len(l)) )

n, d = sorted( time2sec(p) for p in sys.argv[1:3] )

print '{0:.1%}'.format( 1.0*n/d )
```

sys.argv[1:3] are argv[1] and argv[2] (think *[noparse]for(i=1; i<3; i++) { argv[i] }[/noparse]* ).
Both params are sent to time2sec() to return seconds. Sorted() puts them in order so n is always <= than d.

time2sec function splits the param on ':' which yields a list (array) of substrings with 1-3 elems, reverses it ([::-1]) and for each elem converts to int. That '0' is to deal with empty strings so you can have '1::' understood as '1:00:00' because why not ;-)
tl;dr: l is a reversed list of ints (with m and h optionally missing if they were not in the input).
This order allows for automagical sum( l[i]*60^i ) for all existing elements, that is
s*60^0 for s
s*60^0+m*60^1 for m:s
s*60^0+m*60^1+h*60^2 for h:m:s

once n and d are calculated, print n/d.


```
$ ./pcent.py 1::3 2:11
3.6%
$ ./pcent.py :30 2:11
22.9%
$ ./pcent.py 2:11 30
22.9%
```

so the relevant command is
```
rhythmbox-client --print-playing-format '%te %td'
```

in the bash script i posted it would be enough to have this at the top instead of $1 and $2
```
read t1 t2 < <( rhythmbox-client --print-playing-format '%te %td' )
```

---

### Post by freebird54 on 2014-04-16
Yup - never claimed any efficiencies in the coding!  I see there are lots of neat features in that - but learning them (and realigning the brain to think in objects rather than event-driven) would take far longer than writing the extra code did.  Not to mention that I would have no idea where to start if it didn't run right away... for me debuggers are supposed to show me 680x0 machine code!

Are any of the compiled BASIC's worth anything for quick and dirty 'old-stylers' like myself? Or pehaps a Modula-2?  Or do I have to try to modernize?  :D

---

### Post by Vaphell on 2014-04-16
sure, you won't get much help from python with your current problem but imo it's beneficial to know it or some other higher level language that doesn't require 2 pages of code to read and trivial interpret input. Quoting one black lady "Ain't nobody got time for that" ;-)

google, stack overflow and docs.python.org and you are golden ;-)

---

### Post by freebird54 on 2014-04-16
> **Vaphell said:**
> 
google, stack overflow and docs.python.org and you are golden ;-)

THAT's the source of the problem!  Golden years...

I have looked at starting off in Python a couple of times now, and haven't gotten very far.  I don't think it's just motivation shortfall (though that IS possible) but perception shortfall.  Having indents matter (not since punchcards for me!), having to objectify things (coming from a VERY procedural background (assembler, C, BCPL, COBOL etc) and the interactive difference from the 20 or so different BASICs (msbasic, qbasic, AmigaBasic, GFABasic, AC/Basic, TrueBasic, VisualBasic, VB.net, and on and on) I have known seem to make the learning curve steep enough to cause me to backslide so far.  Maybe after I get the music collection organized :D

Thanks for the demonstration though - it shows why I WANTED to learn it - only to be frustrated so far...

---

### Post by Kamron on 2014-04-17
I've just shut my eyes and started with C, despite what people say, I hear PHP, Pythond, Java, Javascript and many others which one to start with is always subjective so I went with C and am not doing to bad so far. It is quicker since it is compiled.

---

### Post by freebird54 on 2014-04-17
> **Kamron said:**
> I've just shut my eyes and started with C, despite what people say, I hear PHP, Pythond, Java, Javascript and many others which one to start with is always subjective so I went with C and am not doing to bad so far. It is quicker since it is compiled.

Quicker to run - not necessarily quicker to program! (OK - necessarily NOT quicker to program!)  It requires a greater understanding of what the computer is actually DOING behind the scenes than the higher-level languages - but I don't think that hurts to know either. Of course, when I learned it - C WAS the higher level language - it saved a ton of time programming in assembler!

Good luck with your endeavours - and remember there are a TON of good tutorials/references only a google away...

---

### Post by Vaphell on 2014-04-17
> Having indents matter (not since punchcards for me!)

well, that's the most controversial part of python i think

> having to objectify things 

well, you don't have to in your own code, if it's the procedural style that blows your hair back, feel free to write your code that way :-) It's not java where you have to cram *public static void main()* into a class ;-)
Sure, types are objects but is there much difference between split( str, sep )->array and str.split(sep)->array? 

that python code could be written as let's say

```
#!/usr/bin/env python

import sys

def time2sec( t ):
    hms = t.split(':')               # list of strings   
    smh = []                         # list for s, m?, h?
    for n in hms:
        smh.insert( 0, int('0'+n) )  # insert int( '0'+num_str ) at idx=0
    secs = 0
    for i in range(0, len(smh)):     # for( i=0; i<len(smh); i++ )
        secs += 60**i*smh[i]         # +60^i*smh[i]
    return secs

n = time2sec( sys.argv[1] )
d = time2sec( sys.argv[2] )

print '{0:.1%}'.format( 1.0*n/d )
```
a bit more procedural, isn't it? ;-)
syntactic sugar like list comprehensions ( *f(x) for x in set* ) is there to cut down the amount of boilerplate to get what you need atm. If you don't feel comfortable with these features, you may avoid them, but the simple convenience stuff like split(), join() etc is still well worth the hassle.



either way it's good to know some higher level language so quick and dirty progs are a matter of minutes.

---

### Post by Kamron on 2014-04-21
> **freebird54 said:**
> Quicker to run - not necessarily quicker to program! (OK - necessarily NOT quicker to program!)  It requires a greater understanding of what the computer is actually DOING behind the scenes than the higher-level languages - but I don't think that hurts to know either. Of course, when I learned it - C WAS the higher level language - it saved a ton of time programming in assembler!

Good luck with your endeavours - and remember there are a TON of good tutorials/references only a google away...

Thanks for the encouragement, I need it!

---

### Post by King Dude on 2014-04-23
I would choose C, because C is usually faster than most other languages. However, your program may be simple enough to where differences in performance between those languages are negligible. Python is great for those that need a clear and easy-to-understand syntax.

Oh by the way, I almost forgot to mention [Julia]("http://julialang.org/"). It's a new language, but I suggest looking into it.

---


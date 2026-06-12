---
title: "Algorithm for determining the day"
date: 2009-01-18
forum: Programming Talk
---

### Post by Krupski on 2009-01-18
OK folks, I need an algorithm to determine what DAY any particular date is, in the form of an integer 0 through 6.

For example, I wish to do this:

```

// sunday january 18, 2009
day = 18;
month = 1;
year = 2009;

doy = getday(day, month, year);

// "doy" is returned as a zero for "Sunday"

```

Yes, I've researched it on Google and found "Zeller's Congruence" and those "First day of 2000 was" things, but NONE OF THEM WORK!!!

I've tried everything I could find, wrote the code in both GWBASIC and C and they simply don't work!

SOMETIMES, the right day is returned, but just when I think "ah-ha THIS one works", another test case fails! :confused:

I've even thought it might be some kind of rounding problem, so I've tried floats and integers... NOTHING works!

Currently, I'm doing it with a brute force lookup table of total days in each year from 2000 to 2029 (with leap years), a table of days in each month (Feb=28 ) and then adding day, month and year up, then doing a "doy = sum modulo 7" on the result.

This works, but it's a kludge.

Is there an ALGORITHM I can use that actually works?

If so, please post it for me (or point me to a link). I'm at my wits end and I'm almost out of hair to rip out!  :)

P.S. I'll take the algorithm in C or BASIC or anything else... I can translate it!

Thanks!

-- Roger

(edit to add): Here's how I'm doing it now:


```

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; days since year 2000 (including leap year)
; covers years 2000 to 2029 (crazy, huh?)
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

y2k     dc.w    1,366,731,1096,1462
        dc.w    1827,2192,2557,2923,3288
        dc.w    3653,4018,4384,4749,5114
        dc.w    5479,5845,6210,6575,6940
        dc.w    7306,7671,8036,8401,8767

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; how many days since january (feb=28)
; leap year is accounted for above
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

dim     dc.w    0               ;jan
        dc.w    31              ;feb
        dc.w    59              ;mar
        dc.w    90              ;apr
        dc.w    120             ;may
        dc.w    151             ;jun
        dc.w    181             ;jul
        dc.w    212             ;aug
        dc.w    243             ;sep
        dc.w    273             ;oct
        dc.w    304             ;nov
        dc.w    334             ;dec

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; here we calculate the day of week
; 0 = sunday
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

        ldx     #clkbuf         ;point to raw clock data

        [COLOR="Red"]**ldab    year,x          ;read bcd year**[/COLOR]
        jsr     bcd2dec         ;convert to decimal
        ldy     #y2k            ;point to year table
        aby                     ;index into...
        aby                     ;...table (16 bits)
        ldd     0,y             ;get total days in years
        std     days            ;store it

        [COLOR="Red"]**ldab    month,x         ;get bcd month**[/COLOR]
        jsr     bcd2dec         ;convert to decimal
        decb                    ;normalize to 0
        ldy     #dim            ;point to days in month
        aby                     ;index into...
        aby                     ;...table (16 bits)
        ldd     0,y             ;add in days of months
        addd    days            ;add to memory
        std     days            ;save & update

        clra                    ;clear top of d
        [COLOR="Red"]**ldab    date,x          ;get date**[/COLOR]
        jsr     bcd2dec         ;convert to decimal
        decb                    ;normalize date to 0
        addd    days            ;add in days within month
        subd    #1              ;normalize to 0=sunday

        ldx     #7              ;x = 7 (do "d mod 7")
        idiv                    ;d = d mod x (integer remainder)

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; now we have the day of the week in b as
; 0 thru 6 where 0=sunday, 1=monday, etc...
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

```

---

### Post by felker2 on 2009-01-18
It's already there: the date command, command with the %w format parameter:

>  %w     day of week (0..6); 0 is Sunday

For example:

Day number of today

```
sander@flappie:~$ date +'%w' -d "2009-01-18"
0
sander@flappie:~$
```

So ... Sunday.

Day number of 1982 December 8th:

```
sander@flappie:~$ date +'%w' -d "1982-12-08"
3
sander@flappie:~$
```

So Wednesday, which is correct.


If you don't want to use 'date' itself, you can get the date-source and use it.

---

### Post by lensman3 on 2009-01-18
C/C++ has ctime() function.  The structure that is returned has a day of the week as one of the arguments.  The structure tm is defined in <time.h>.

Do a man on ctime: "man ctime".

Here is a code snippet:

   struct tm *t ;
   struct timeval tp;
   struct timezone tzp;

   gettimeofday( &tp, &tzp );
   t = localtime( &(tp.tv_sec) );

   n->year	 = t->tm_year + 1900;
   n->month	 = t->tm_mon + 1
   n->day	 = t->tm_mday ;
   n->hour	 = t->tm_hour ;
   n->minute	 = t->tm_min ;
   n->second	 = t->tm_sec ;
   n->millisec   = tp.tv_usec  / 1000.;

Hope this helps.

---

### Post by eightmillion on 2009-01-18
I just wrote this bit of python that seems to work for any date after 1752. I based it off the wikipedia page, [Calculating the day of the week]("http://en.wikipedia.org/wiki/Calculating_the_day_of_the_week").

```
#!/usr/bin/env python
import time

months = {1:0,2:3,3:3,4:6,5:1,6:4,7:6,8:2,9:5,10:0,11:3,12:5,13:6,14:2}
daysOfTheWeek = {0:'Sunday',1:'Monday',2:'Tuesday',3:'Wednesday',4:'Thursday',5:'Friday',6:'Saturday'}

def leap(year):
    if year % 4 == 0 and not year % 100 == 0: return True
    elif year % 4 == 0 and year % 100 == 0 and year % 400 == 0: return True
    else: return False

def calcmonth(month,year):
    if leap(year):
        if month == 1 or month == 2: return months[month+12]
        else: return months[month]
    else:return months[month]

def calcday(year,month,day):
    y = (2 * ( 3 - ( year/100 % 4) )) + divmod(year,100)[1] + divmod(year,100)[1]/4
    m = calcmonth(month,year)
    return (y+m+day) % 7

if __name__ == '__main__':
    year, month, day = time.localtime()[:3]
    print "Today is %s" % daysOfTheWeek[calcday(year,month,day)]

```

---

### Post by Krupski on 2009-01-18
> **felker2 said:**
> It's already there: the date command, command with the %w format parameter:


Well, I ultimately want to use the code in Motorola MC68HC11 assembler... so a Linux command (or it's source) isn't going to help much. Thanks anyway!

-- Roger

---

### Post by Krupski on 2009-01-18
> **eightmillion said:**
> I just wrote this bit of python that seems to work for any date after 1752. I based it off the wikipedia page, [Calculating the day of the week]("http://en.wikipedia.org/wiki/Calculating_the_day_of_the_week").

```
#!/usr/bin/env python
import time

months = {1:0,2:3,3:3,4:6,5:1,6:4,7:6,8:2,9:5,10:0,11:3,12:5,13:6,14:2}
daysOfTheWeek = {0:'Sunday',1:'Monday',2:'Tuesday',3:'Wednesday',4:'Thursday',5:'Friday',6:'Saturday'}

def leap(year):
    if year % 4 == 0 and not year % 100 == 0: return True
    elif year % 4 == 0 and year % 100 == 0 and year % 400 == 0: return True
    else: return False

def calcmonth(month,year):
    if leap(year):
        if month == 1 or month == 2: return months[month+12]
    else:return months[month]

def calcday(year,month,day):
    y = (2 * ( 3 - ( year/100 % 4) )) + divmod(year,100)[1] + divmod(year,100)[1]/4
    m = calcmonth(month,year)
    return (y+m+day) % 7

if __name__ == '__main__':
    year, month, day = time.localtime()[:3]
    print "Today is %s" % daysOfTheWeek[calcday(year,month,day)]

```


I can translate this for my needs... I'll try it and see if it works for me. Thanks!!!

-- Roger

---

### Post by eightmillion on 2009-01-18
> **Krupski said:**
> I can translate this for my needs... I'll try it and see if it works for me. Thanks!!!

-- Roger

No problem. You should note that there was a slight bug with the calcmonth function. You should change this:

```
def calcmonth(month,year):
    if leap(year):
        if month == 1 or month == 2: return months[month+12]
    else:return months[month]
```

to this:

```
def calcmonth(month,year):
    if leap(year):
        if month == 1 or month == 2: return months[month+12]
        else: return months[month]
    else:return months[month]
```

---

### Post by Krupski on 2009-01-18
> **eightmillion said:**
> No problem. You should note that there was a slight bug with the calcmonth function. You should change this:

```
def calcmonth(month,year):
    if leap(year):
        if month == 1 or month == 2: return months[month+12]
    else:return months[month]
```

to this:

```
def calcmonth(month,year):
    if leap(year):
        if month == 1 or month == 2: return months[month+12]
        else: return months[month]
    else:return months[month]
```

Yeah... I saw that. You're indexing into the "months" table the last 2 entries if it's a leap year and January or February. Thanks!

-- Roger

(p.s. I'm working on writing some 6811 assembler code to do this... luckily it's all integers!)

---

### Post by eightmillion on 2009-01-18
This is just an update for if anybody else is looking at this.  I don't really know why I used dictionaries when lists would work just a well. I'm not sure why I used divmod when all I needed was the modulus. ](*,)

```

#!/usr/bin/env python
import time

months = [ 0,3,3,6,1,4,6,2,5,0,3,5,6,2 ]
daysOfTheWeek = [ 'Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday' ]

def leap(year):
    if year % 4 == 0 and not year % 100 == 0: return True
    elif year % 4 == 0 and year % 100 == 0 and year % 400 == 0: return True
    else: return False

def calcmonth(month,year):
    if leap(year) and month < 3: return months[month+11]
    else: return months[month - 1]

def calcday(year,month,day):
    y = (2 * ( 3 - ( year/100 % 4) )) + (year % 100) + (year % 100)/4
    m = calcmonth(month,year)
    return (y+m+day) % 7

if __name__ == '__main__':
    year, month, day = time.localtime()[:3]
    print "Today is %s" % daysOfTheWeek[calcday(year,month,day)]

```

---

### Post by eightmillion on 2009-01-21
Just for fun, I implemented an algorithm in one line to calculate the day of the week. This one is based on Zeller's congruence

```
In [129]: days = ['sun', 'mon', 'tues', 'weds', 'thurs', 'fri', 'sat']

In [130]: calcday = lambda y,m,d: int(((d + (((([m,m+12][m<3] + 1)*26))/10) + ([y,y-1][m<3] % 100) + (([y,y-1][m<3] % 100)/4) + ([y,y-1][m<3]/400) + (5 * ([y,y-1][m<3]/100))) - 1 ) % 7)

In [131]: days[calcday(1980,5,27)]
Out[131]: 'tues'

In [132]: days[calcday(2054,6,19)]
Out[132]: 'fri'

In [133]: days[calcday(1783,9,18)]
Out[133]: 'thurs'

In [134]: days[calcday(1982,4,24)]
Out[134]: 'sat'
```

---

### Post by Krupski on 2009-01-21
> **eightmillion said:**
> In [130]: calcday = lambda y,m,d: int(((d + (((([m,m+12][m<3] + 1)*26))/10) + ([y,y-1][m<3] % 100) + (([y,y-1][m<3] % 100)/4) + ([y,y-1][m<3]/400) + (5 * ([y,y-1][m<3]/100))) - 1 ) % 7)

Ouch! I don't understand that line (well parts of it anyway).

Could you show me what you did... but in C?

What really has me stumped are the things like "[m,m+12]"... no clue here.

Thanks!

-- Roger

---

### Post by eightmillion on 2009-01-21
> **Krupski said:**
> Ouch! I don't understand that line (well parts of it anyway).

Could you show me what you did... but in C?

What really has me stumped are the things like "[m,m+12]"... no clue here.

Thanks!

-- Roger

I'm not so good with C, but I think I can explain what's going on in that line. I'm mostly playing with how python interprets True and False, and how it indexes lists in place of if...else constructs. In python, like most languages, 0 is False and 1 is True. What's cool is that you can use that as an index for a list. So in the parts like, "[m,m+12][m<3]" if m is less than 3, then that statement m<3 evaluates to True or 1, so you can think of that as "[m,m+12][1]". In that case m+12 is returned. It's just a shorthand way of writing this:
```
if m < 3:
    return m + 12
else:
    return m
```

I had to use those because in Zeller's congruence, January and February are treated as the 13th and 14th month of the previous year so I had to use "[y,y-1][m<3]" also to roll the year back if I'm trying to calculate a day for January or February. The rest of it is just integer math.

It's even possible to get the function itself to return the actual day all by itself instead of an integer like this:

```
In [77]: calcday = lambda y,m,d: 'Sunday Monday Tuesday Wednesday Thursday Friday Saturday'.split()[int(((d + (((([m,m+12][m<3] + 1)*26))/10) + ([y,y-1][m<3] % 100) + (([y,y-1][m<3] % 100)/4) + ([y,y-1][m<3]/400) + (5 * ([y,y-1][m<3]/100))) - 1 ) % 7)]

In [79]: calcday(2009,1,21)
Out[79]: 'Wednesday'
```

---

### Post by Krupski on 2009-01-21
> **eightmillion said:**
> What's cool is that you can use that as an index for a list. So in the parts like, "[m,m+12][m<3]" if m is less than 3, then that statement m<3 evaluates to True or 1, so you can think of that as "[m,m+12][1]". In that case m+12 is returned. It's just a shorthand way of writing this:
```
if m < 3:
    return m + 12
else:
    return m
```

I had to use those because in Zeller's congruence, January and February are treated as the 13th and 14th month of the previous year so I had to use "[y,y-1][m<3]" also to roll the year back if I'm trying to calculate a day for January or February. The rest of it is just integer math.


OK I understand it now.

One thing I have to ask... have you "extensively" tested that algorithm?

I wrote several versions of Zeller's congruence in BASIC, C and Motorola assembler.

All of them did the same thing (that is, they worked for many cases, but failed once in a while).

Oh well... now that I understand what your code is doing, I'm going to try it again. *Maybe* I got something ordered wrong in my previous attempts...

Thanks for the quick reply! I'll let you know how it turns out.

-- Roger

---

### Post by eightmillion on 2009-01-21
> **Krupski said:**
> OK I understand it now.

One thing I have to ask... have you "extensively" tested that algorithm?

I wrote several versions of Zeller's congruence in BASIC, C and Motorola assembler.

All of them did the same thing (that is, they worked for many cases, but failed once in a while).

Oh well... now that I understand what your code is doing, I'm going to try it again. *Maybe* I got something ordered wrong in my previous attempts...

Thanks for the quick reply! I'll let you know how it turns out.

-- Roger

This doesn't test every date, but it tests 261052 dates and returns no incorrect dates. I'd consider that pretty extensive.

```
for y in range(1752,2500):
    for m in range(1,13):
        for d in range(1,29):
            r = datetime.date(y,m,d)
            if calcday(y,m,d) != 'Monday Tuesday Wednesday Thursday Friday Saturday Sunday'.split()[r.weekday()]: print "Error!"
```

---

### Post by eightmillion on 2009-01-21
I just fixed it so that it tests all the dates between 1752 and 2500 and got no errors. That's 282926 dates.

```
for y in range(1752,2500):
    for m in range(1,13):
        for d in range(1,32):
            try: r = datetime.date(y,m,d)
            except ValueError: continue
            b = calcday(y,m,d)
            a = 'Monday Tuesday Wednesday Thursday Friday Saturday Sunday'.split()[r.weekday()]
            if a != b: print "Error!"
```

EDIT: It looks like it's good until at least the year 10,000. Over 3 million dates.

---

### Post by Krupski on 2009-01-21
> **eightmillion said:**
> I just fixed it so that it tests all the dates between 1752 and 2500 and got no errors. That's 282926 dates.

```
for y in range(1752,2500):
    for m in range(1,13):
        for d in range(1,32):
            try: r = datetime.date(y,m,d)
            except ValueError: continue
            b = calcday(y,m,d)
            a = 'Monday Tuesday Wednesday Thursday Friday Saturday Sunday'.split()[r.weekday()]
            if a != b: print "Error!"
```

EDIT: It looks like it's good until at least the year 10,000. Over 3 million dates.

Well, I just re-did it in C with a primitive date input scheme (just for testing). It seems to be working now. I don't know what I was doing wrong before... :confused:

Anyway, here it is in C:

```

// zeller.c - zeller's congruence (I hope)

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
    if(argc != 4) {
        fprintf(stderr, "error: exactly 3 params required\n");
        fprintf(stderr, "usage: zeller day month year \n");
        fflush(stderr);
        return(-1);
    }

    char *day_name[7]={"Saturday","Sunday","Monday","Tuesday","Wednesday","Thursday","Friday"};

    int day   = atoi(argv[1]); // read day from command line
    int month = atoi(argv[2]); // ditto month
    int year  = atoi(argv[3]); // ditto year

    int q = day; // use same var names as wiki example
    int m = month; // ditto
    if(m < 3) { (m += 12); (year -= 1); } // do the month 13 & 14 thing
    int k = (year % 100); // year of the century
    int j = (year / 100); // the century (i.e. 1995 = 19)

    int h = ((q + ((((m + 1) * 26) / 10) + k + (k / 4) + (j / 4) + (5 * j))) % 7);

    fprintf(stdout, "debug: q=%d, m=%d, k=%d, j=%d\n", q, m, k, j);
    fprintf(stdout, "Calculated day is %s\n", day_name[h]);
    fflush(stdout);

    return(0);
}

```


Even if you don't know C well it should be obvious what's going on here, plus I added comments to help.

Now, I'm going to try running it against a standard "day of week" function in C and see if it matches up through a wide range.

C. C program run. Run program run!  :)

Thanks for your help... I'm making progress!

-- Roger

---

### Post by Krupski on 2009-01-21
> **eightmillion said:**
> I just fixed it so that it tests all the dates between 1752 and 2500 and got no errors. That's 282926 dates.

```
for y in range(1752,2500):
    for m in range(1,13):
        for d in range(1,32):
            try: r = datetime.date(y,m,d)
            except ValueError: continue
            b = calcday(y,m,d)
            a = 'Monday Tuesday Wednesday Thursday Friday Saturday Sunday'.split()[r.weekday()]
            if a != b: print "Error!"
```

EDIT: It looks like it's good until at least the year 10,000. Over 3 million dates.

What is that? A script of some sort?

---

### Post by eightmillion on 2009-01-21
> **Krupski said:**
> What is that? A script of some sort?

It's just a bit of python to run through all those dates and check my function against python's built in datetime module. I just ran your program through the same process, up to the year 10,000 and didn't get any errors.

```
for y in range(1752,10000):
    for m in range(1,13):
        for d in range(1,32):
            try: r = datetime.date(y,m,d)
            except ValueError: continue
            b = 'Monday Tuesday Wednesday Thursday Friday Saturday Sunday'.split()[r.weekday()]
            a = os.popen('./a.out %s %s %s' % (d, m, y)).read().strip()
            if a != b: print "Error!", a, b," : ", y, m, d
```

I just had to modify your program a bit.

```

//    fprintf(stdout, "debug: q=%d, m=%d, k=%d, j=%d\n", q, m, k, j);
    fprintf(stdout, "%s", day_name[h]);

```

---

### Post by Krupski on 2009-01-21
> **eightmillion said:**
> It's just a bit of python to run through all those dates and check my function against python's built in datetime module. I just ran your program through the same process, up to the year 10,000 and didn't get any errors.


Neat! Now one last question if I may... how do I run your Python code? Is it a script?

Thanks again... and thanks for testing my code!

-- Roger

---

### Post by eightmillion on 2009-01-21
> **Krupski said:**
> Neat! Now one last question if I may... how do I run your Python code? Is it a script?

Thanks again... and thanks for testing my code!

-- Roger

No problem. I've just been running my python code through the interactive shell, but you could just as easily throw it in a text with a hash bang at the top and an "import datetime, os" and run it that way. Like this:
```

#!/usr/bin/env python
import datetime,os

for y in range(1752,10000):
    for m in range(1,13):
        for d in range(1,32):
            try: r = datetime.date(y,m,d)
            except ValueError: continue
            b = 'Monday Tuesday Wednesday Thursday Friday Saturday Sunday'.split()[r.weekday()]
            a = os.popen('./a.out %s %s %s' % (d, m, y)).read().strip()
            if a != b: print "Error!", a, b," : ", y, m, d
```

---

### Post by Krupski on 2009-01-21
> **eightmillion said:**
> No problem. I've just been running my python code through the interactive shell, but you could just as easily throw it in a text with a hash bang at the top and an "import datetime, os" and run it that way. Like this:
```

#!/usr/bin/env python
import datetime,os

for y in range(1752,10000):
    for m in range(1,13):
        for d in range(1,32):
            try: r = datetime.date(y,m,d)
            except ValueError: continue
            b = 'Monday Tuesday Wednesday Thursday Friday Saturday Sunday'.split()[r.weekday()]
            a = os.popen('./a.out %s %s %s' % (d, m, y)).read().strip()
            if a != b: print "Error!", a, b," : ", y, m, d
```

Thank you for all the help. I ultimately arrived at what I was shooting for... the Zeller code in assembler.

FYI, and for anyone who may be able to make use of it, here it is:



```

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; zeller's congruence in motorola 68hc11 assembler
; 68hc11 implementation (c) 2009 roger a. krupski
; <krupski@acsu.buffalo.edu>
; this code is hereby released to public domain
;
; last update: wed 23 sep 2009
;
; load up registers as follows:
;     acca = month (01-12)
;     accb = day (01-31)
;     ix = year (4 digit year)
;
; returns:
;     day of week in accb (0-6 where 0=sunday, 1=monday, etc...)
;     accb is modified, all other registers are preserved.
;
; see <http://en.wikipedia.org/wiki/Zeller's_congruence> for
;     more information on the zeller's congruence algorithm.
;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;
;                      (**) zeller's congruence
;
;      /    |(m+1)*26|       | y |       | y |   | y |    \
; h = | q + |--------| + y + |---| + 6 * |---| + |---| - 1 | mod 7
;      \    |   10   |       | 4 |       |100|   |400|    /
;
; (**) note we subtract 1 before the mod-7 calculation
; to make sunday = zero as is standard.
;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

; stack storage offsets

        offset  0

mn      ds.w    1               ;month (word)
dy      ds.w    1               ;day (word)
yr      ds.w    1               ;year (word)
tmp     ds.w    1               ;intermediate (word)

tmpsiz  equ     *-mn            ;size of temp stack area

astack  ds.b    1               ;incoming month (byte)
bstack  ds.b    1               ;incoming day / outgoing result (byte)
xstack  ds.w    1               ;incoming year (word)
ystack  ds.w    1               ;save y (word)


;;;;;;;;;;;;;;;;;;;; code starts here ;;;;;;;;;;;;;;;;;;;;;;

zeller  pshy
        pshx
        pshb                    ;will get modified
        psha                    ;save registers

; allocate temp storage on the stack

        clra                    ;a=0
        ldab    #tmpsiz         ;storage count

alloc   psha                    ;allocate stack
        decb                    ;more?
        bne     alloc           ;yes do rest

        tsy                     ;stack->y (points to temp storage)

        clra                    ;zero top of d
        ldab    astack,y        ;get month
        std     mn,y            ;store month

        clra                    ;zero top of d
        ldab    bstack,y        ;get day
        std     dy,y            ;store day

        ldd     xstack,y        ;get year
        std     yr,y            ;store year (word)

        ldd     #-1             ;d=-1
        std     tmp,y           ;(**) -1 makes sunday=0


; this does "month 13 and 14" correction

        ldd     mn,y            ;get month
        cpd     #2              ;jan or feb?
        bhi     zel2            ;no

        addd    #12             ;yes, add a year
        std     mn,y            ;store updated month
        ldd     yr,y            ;get year
        subd    #1              ;correct year (yr=yr-1)
        std     yr,y            ;store updated year

zel2    ldd     mn,y            ;m
        addd    #1              ;(m+1)
        ldaa    #26             ;26
        mul                     ;d=(m+1)*26
        ldx     #10             ;divisor 10
        idiv                    ;x=((m+1)*26)/10
        xgdx                    ;x->d
        addd    tmp,y           ;add in intermediate
        std     tmp,y           ;update intermediate

        ldd     yr,y            ;year
        ldx     #4              ;divisor 4
        idiv                    ;x=(year/4)
        xgdx                    ;x->d
        addd    tmp,y           ;add in intermediate
        std     tmp,y           ;update intermediate

        ldd     yr,y            ;year
        ldx     #100            ;divisor 100
        idiv                    ;x=(year/100)
        xgdx                    ;x->d
        ldaa    #6              ;a=6
        mul                     ;d=6*(year/100)
        addd    tmp,y           ;add in intermediate
        std     tmp,y           ;update intermediate

        ldd     yr,y            ;year
        ldx     #400            ;divisor 400
        idiv                    ;x=(year/400)
        xgdx                    ;x->d
        addd    tmp,y           ;add in intermediate
        addd    dy,y            ;add day (q)
        addd    yr,y            ;add year
        ldx     #7              ;mod 7
        idiv                    ;x=d/x, quotient to x, remainder to d

        stab    bstack,y        ;(*) store result, return in accb

; deallocate storage on the stack

        ldab    #tmpsiz         ;count

dealloc pula                    ;dealloc stack
        decb                    ;more?
        bne     dealloc         ;yes do rest

; restore registers

        pula
        pulb                    ;(*) day of week was placed here
        pulx
        puly                    ;restore registers

        rts                     ;return with day of week in b



```


The only place I had trouble making it work was in GWBASIC. I solved that problem when I realized that BASIC was doing floating point math. I did INT() of everything and then it worked!

Finally... it works and I'm confident that the algorithm covers all possibilities.

Thank again so much for your help!

-- Roger

---


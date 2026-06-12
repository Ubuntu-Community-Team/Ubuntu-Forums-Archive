---
title: "Help me solve a programming mystery"
date: 2010-12-01
forum: Programming Talk
---

### Post by mormonunderpants on 2010-12-01
I'm a linux c programmer who recently was asked to write a quick program to do something trivial. I told them it would take 2x longer than I knew it would and used it as an opportunity to do learn bash shell scripting, something I had been wanting to do. After a few hours of coding and finding out that bash treats 08 and 09 as octal and every work around was more effort than it was worth, I re-wrote the thing in c. But a mystery remains.

I'm hoping someone can explain to this bash shell newb why the following code fragment behaves the way it does. 

It should be taking in a date in YYYYMMDD format, parsing the year, month, and day into three separate variables, then checking to see if they are a valid calendar date. 

I understand why a date of 20101208 doesn't work- the day of 08 has a preceding 0 which bash interprets as an octal number. But what I can't figure out is why a date of 20100815 works, even though it seems to me that a month of 09 should result in the same issue.

```

#!/bin/bash
while true
do
    printf "\nEnter Start Date (YYYYMMDD): "
    read STARTDATE

    eval $(echo $STARTDATE | sed 's/^\(....\)\(..\)\(..\)/YEAR=\1 MONTH=\2 DAY=\3/')

    cal $MONTH $YEAR 2> /dev/null | grep -w $DAY > /dev/null
    if [[ $? -eq 0 ]] ; then
            echo $STARTDATE" IS THE START DATE"
            break
    else
            echo $STARTDATE" IS AN INVALID DATE"
    fi
done
```

---

### Post by TiBaal89 on 2010-12-01
Well, if you throw 

```
    echo $YEAR 
    echo $MONTH
    echo $DAY
```

in there, you're definitely parsing everything correctly:

> Enter Start Date (YYYYMMDD): 20100808
2010
08
08

As for why 20100815 works, it must have something to do with how 'cal' is programmed... it appears to discard leading zeroes in its input.  All of these result in July of 2010 being display if you type them in the terminal:

```
cal 7 2010
cal 07 2010
cal 007 2010
cal 007 02010
cal 000000007 00000000002010
```

---

### Post by TiBaal89 on 2010-12-01
Then you're trying to grep the calendar to find the day number?  That explains the rest of the problem... 'cal' writes the single digit dates without the leading zero, you're searching for it with the leading zero.

```
$ cal 7 2010
     July 2010
Su Mo Tu We Th Fr Sa
             1  2  3
 4  5  6  7  8  9 10
11 12 13 14 15 16 17
18 19 20 21 22 23 24
25 26 27 28 29 30 31
```

That seems like an awfully strange way of checking a date...

---

### Post by mormonunderpants on 2010-12-01
> **TiBaal89 said:**
> Then you're trying to grep the calendar to find the day number?  That explains the rest of the problem... 'cal' writes the single digit dates without the leading zero, you're searching for it with the leading zero.

I guess that still doesn't make me understand why it accepts a month of 09, but not a day of 09.

> 
25 26 27 28 29 30 31[/CODE]That seems like an awfully strange way of checking a date...

It probably is, I wouldn't really know. This is my first attempt at bash. How would be the best to validate something as a calendar date in bash?

---

### Post by mobilediesel on 2010-12-01
> **mormonunderpants said:**
> I'm a linux c programmer who recently was asked to write a quick program to do something trivial. I told them it would take 2x longer than I knew it would and used it as an opportunity to do learn bash shell scripting, something I had been wanting to do. After a few hours of coding and finding out that bash treats 08 and 09 as octal and every work around was more effort than it was worth, I re-wrote the thing in c. But a mystery remains.

I'm hoping someone can explain to this bash shell newb why the following code fragment behaves the way it does. 

It should be taking in a date in YYYYMMDD format, parsing the year, month, and day into three separate variables, then checking to see if they are a valid calendar date. 

I understand why a date of 20101208 doesn't work- the day of 08 has a preceding 0 which bash interprets as an octal number. But what I can't figure out is why a date of 20100815 works, even though it seems to me that a month of 09 should result in the same issue.

```

#!/bin/bash
while true
do
    printf "\nEnter Start Date (YYYYMMDD): "
    read STARTDATE

    eval $(echo $STARTDATE | sed 's/^\(....\)\(..\)\(..\)/YEAR=\1 MONTH=\2 DAY=\3/')

    cal $MONTH $YEAR 2> /dev/null | grep -w $DAY > /dev/null
    if [[ $? -eq 0 ]] ; then
            echo $STARTDATE" IS THE START DATE"
            break
    else
            echo $STARTDATE" IS AN INVALID DATE"
    fi
done
```

Bash can be weird when leading zeros are involved. The **date** command can actually be used to easily determine if the entered number is a valid date:
```
#!/bin/bash
while true
do
    printf "\nEnter Start Date (YYYYMMDD): "
    read STARTDATE
    if date --date="$STARTDATE" &>/dev/null
    then
        echo $STARTDATE" IS THE START DATE"
    else
        echo $STARTDATE" IS AN INVALID DATE"
    fi
done
```

---

### Post by TiBaal89 on 2010-12-01
> **mormonunderpants said:**
> I guess that still doesn't make me understand why it accepts a month of 09, but not a day of 09.

The month you're feeding to the cal command... I demonstrated that cal works whether its input contains leading zeros or not.

The day you're using for the grep command... grep is text search.  The text '8' that cal puts out is not the same as '08' that you have stored in $DAY.  You're grep'ing for the characters '08' which does not appear in the cal.  Hence, that doesn't work.

There are totally separate reasons why one works and the other doesn't...

---

### Post by mormonunderpants on 2010-12-02
> **TiBaal89 said:**
> The month you're feeding to the cal command... I demonstrated that cal works whether its input contains leading zeros or not.

The day you're using for the grep command... grep is text search.  The text '8' that cal puts out is not the same as '08' that you have stored in $DAY.  You're grep'ing for the characters '08' which does not appear in the cal.  Hence, that doesn't work.

There are totally separate reasons why one works and the other doesn't...

Okay, now I see what I was missing. Thanks. Perhaps I'll rewrite the thing in bash anyway.

---

### Post by saulgoode on 2010-12-02
You can force a number that has preceding zeroes to be interpreted as a decimal number by prepending "10#" to it.

Example:

[INDENT]**echo $(( 010 + 020 ))** yields decimal twenty-four (8 + 16)

**echo $(( 10#010 + 10#020 ))** yields thirty (10+20)[/INDENT]

---

### Post by mormonunderpants on 2010-12-04
> **saulgoode said:**
> You can force a number that has preceding zeroes to be interpreted as a decimal number by prepending "10#" to it.

Example:
[INDENT]**echo $(( 010 + 020 ))** yields decimal twenty-four (8 + 16)

**echo $(( 10#010 + 10#020 ))** yields thirty (10+20)[/INDENT]

This is the best solution. Thanks!

---

### Post by mormonunderpants on 2010-12-04
> That seems like an awfully strange way of checking a date...

I appreciate your answer- you solved the mystery, but your suggested method of using date instead of cal to validate doesn't work quite as nicely. It allows my to enter 00 as a day, and doesn't properly take into account leap days, etc. I suppose this is why cal was recommended to me by a colleague. 

Again, thanks for explaining the reason my code behaved the way it did.

---

### Post by trent.josephsen on 2010-12-04
Really?
```
appalachia% date -d '20100229'
date: invalid date `20100229'
appalachia% date -d '20120229'
Wed Feb 29 00:00:00 CST 2012
appalachia% date -d '20120100'
date: invalid date `20120100'
```

date is the correct tool for this.  cal+grep is an ugly hack.

---


---
title: "How to do a &quot;circular list&quot; in Python"
date: 2007-08-24
forum: Programming Talk
---

### Post by trilobite on 2007-08-24
Hi all - 
 
  I'm wanting to do a simple text-based calendar app in Python (it'll be public-domain).  ( Btw, I'm running Feisty, with Python 2.5.1). 

  I've done a bit of "background thinking" on this, as follows - 
  *** Start of "background notes"  ***
  Any month can be described with a 3-digit code, where the first two digits are the number of days in the month (28-31), and the last digit is the day of the week that the month starts on.  

  So, Jan 2007 is shown by 312 - 31 day, starts on Monday (2). 
( I'll use 1 for Sunday, through to 7 for Saturday). 

  So, the month-structure of 2007 is as follows - 
  Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec
 312, 285, 315, 301, 313, 306, 311, 314, 307, 312, 305, 317. 

  2008 will be as follows - 
  Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec
 313, 296, 317, 303, 315, 301, 313, 316, 302, 314, 307, 312.  

  We can use "clock arithmetic" (also called "modulo arithmetic")  to change the weekdays from year to year. 
  A "clock" with 7 "hours", representing the days of the week. will be used.  This could be done with a "circular list". 
*** End of background notes *** 

  I've already found some very-useful p.d. Python code for doing tables. Now, I just need to do the circular lists and go from there, then merge that code with the table code.  However, I've got a bit of a "mental block" as to how to do a circular list.  

  A good "test-case" is Dec this year (which is a "317") which will then be a "312" next year (as it starts on a Monday). 
(  Leap-year next year, remember.... ;-) ) 
So, there's a good example of the "wrap-around" that I want. 

  So, anyone able to help on doing circular lists?  Many thanks in advance.... bye foe now - 
 - trilobite

---

### Post by aquavitae on 2007-08-24
I can't help with the circular list, but can I ask why you're trying to do it this way - what's the list to be used for?  If you're simply trying to get a way of identifying each month I'd have thought that 200712, 200801, etc would be easier?  Or better yet use a tuple (2007, 12) (2008, 1) etc.

---

### Post by steve.horsley on 2007-08-24
What do ou want to put in the list? The numbers 0-6? I would think that just using modulo arithmetic would be better suited to that. Frinstance, 
6 % 7 = 6
7 % 7 = 0
8 % 7 = 1
etc.

You could do a circular list if you want.

---

### Post by triptoe on 2007-08-24
Edit: whoops. it should be:


> 
if ((week+7) % 7 == 0:
     y = '7'

else:
     y = str((week+x) % 7



Do you mean you are not allowed or can't use the modulo? I am not sure what you meant but here it is with modulo

if (week+x) > 7:
                y = str((week + x) % 7)
        else:
                y = str(week+x)

you could also use a bunch of if statements but that would be tedious...


```

# Returns whether year is leap or not
def isLeap(year):
        if year % 400 == 0:
                return True
        elif year % 4 == 0 and year % 100 != 0:
                return True
        return False
# counts how many times leap year has occurred since 2008 in the year given
def leapCount(year):
        counter = 0
        i = 1
        while i <= (year-2008):
                if isLeap(2008 + i):
                        counter += 1
                i += 1
        return counter
year2008 = ['313','296','317','303','315','301','313','316','302','314','307','312']

#print year2008

year = input("Enter a year greater than 2008: ")

# find how many days should be shifted over
week = (year - 2008) + leapCount(year)
# shift
newYear = []
j = 0
for i in year2008:
        x = int(i[-1])
        if (week+x) > 7:
                y = str((week + x) % 7)
        else:
                y = str(week+x)
        newYear.append(year2008[j].replace(year2008[j], year2008[j][:2] + y))
        j += 1

print newYear

```

---

### Post by trilobite on 2007-08-24
Hi all - 

  Thanks very much aquavitae, steve.horsley, triptoe for your replies!  

  I'm just doing this to get into Python a bit more (and yes, the modulo operator will do the trick - no need for "circular lists"...  :-) )   I should have looked more closely at the Python docs ;-)  
  
  Thanks again - bye for now - 
 -trilobite

---

### Post by slavik on 2007-08-25
circular lists are easily handled by doubly linked lists.

here's an idea of making a circular list in perl:
```

sub getitem {
 my $i = shift;
 return $array[$i%($#array+1)];
}

```

---


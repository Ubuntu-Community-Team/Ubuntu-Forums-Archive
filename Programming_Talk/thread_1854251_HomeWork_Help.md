---
title: "HomeWork Help"
date: 2011-10-04
forum: Programming Talk
---

### Post by maxpol on 2011-10-04
Hi Guys,

Have been trying to get this code going, but I got stuck at where to start at. The project is to make a program that calculates when you are a billion seconds old considering only 30 days in a year and no leap years. It has to be exact to the second. (yy/mm/dd hh:mm:ss) So far Ive got this.
```

yearStr=input("Enter your birth year: ")
monthStr=input("Enter your birth month: ")
dayStr=input("Enter your birth day: ")
hourStr=input("Enter your birth hour: ")
minuteStr=input("Enter your birth minute: ")
secondStr=input("Enter your birth second: ")
year=int(yearStr)
month=int(monthStr)
day=int(dayStr)
hour=int(hourStr)
minute=int(minuteStr)
second=int(secondStr)
print("Your birthday is: " + yearStr + "/" + monthStr + "/" + dayStr + " at " +\
 hourStr + ":" + minuteStr + ":" + secondStr)

#yearTotal=(year+32)
#monthTotal=((month+965)/965)
print("This is when you will be a billion seconds old: ")


```

Any help on how to get started is really appreciated! Thanks!

---

### Post by v1ad on 2011-10-04
well what language that would really help us

---

### Post by kext_kext on 2011-10-04
Python? So only 30 days in the year? Or 30 days per each of the 12 months in a year?

---

### Post by Vaphell on 2011-10-04
yup, description is not too clear.
if you got only 30 days in a year, what a month is? (it is supposed to be there in the output)
does the rule of 24hours in a day still hold? 3600 seconds in an hour? Or hours, minutes and seconds stay the same but the number that a day holds is different?

---

### Post by maxpol on 2011-10-04
Yeah sorry guys, this is in Python. But to make things simple, there are no leap years and only 30 days per month and 12 months in a year. So instead on 365 days there are 360. The rest of the rules like 3600 sec and 24 hours a day still hold true.

---

### Post by Arndt on 2011-10-04
> **maxpol said:**
> Yeah sorry guys, this is in Python. But to make things simple, there are no leap years and only 30 days per month and 12 months in a year. So instead on 365 days there are 360. The rest of the rules like 3600 sec and 24 hours a day still hold true.

If you were asked to compute when you were 1000 seconds old, how would you go about it?

---

### Post by maxpol on 2011-10-04
> **Arndt said:**
> If you were asked to compute when you were 1000 seconds old, how would you go about it?

I would figure out how many minutes and days it is? I think.... then add it to the original date

---

### Post by sisco311 on 2011-10-04
I'd do it the other way around... ;)

---

### Post by maxpol on 2011-10-04
> **sisco311 said:**
> I'd do it the other way around... ;)

Do you mean the original date part or the minutes/days part?

---

### Post by sisco311 on 2011-10-04
I mean, I would convert the date to seconds (since an epoch). Add 1 billon, then convert back the secons to a date.

---

### Post by Vaphell on 2011-10-04
if you don't want to deal with overflows of hours/days/months/years (you know, these exceptions where 28dec+10days being year=year+1 and month=12->1 and day=some other non trivial number) do the reverse.
transform everything to seconds (multiplication is easier than division and addition with overflows), add offset, transform the sum back. You will perform the same operation you'd perform your way on the offset, but here you get the result right off the bat.
To deal with lower numbers you can skip year part of birth day in calculations and apply it at the end. Let's say you were born in 1990 and the result is 33yrs 10months 20 days. 1990+33=2023/10/20

---

### Post by maxpol on 2011-10-04
> **Vaphell said:**
> if you don't want to deal with overflows of hours/days/months/years (you know, these exceptions where 28dec+10days being year=year+1 and month=12->1 and day=some other non trivial number) do the reverse.
transform everything to seconds (multiplication is easier than division and addition with overflows), add offset, transform the sum back. You will perform the same operation you'd perform your way on the offset, but here you get the result right off the bat.
To deal with lower numbers you can skip year part of birth day in calculations and apply it at the end. Let's say you were born in 1990 and the result is 33yrs 10months 20 days. 1990+33=2023/10/20

Just to confirm, "how" are you taking the sum of everything? Are you making the year entered 0 and then calculate from 0 how many seconds to the DOB? I'm trying to visualize it here and you're pointing me in the right direction. Just need more clarification ;)

---

### Post by sisco311 on 2011-10-04
Traditionally, in Unix/Linux January 1, 1970 is the epoch, but 0 should work too. 

[http://en.wikipedia.org/wiki/Epoch_(reference_date)#Computing](http://en.wikipedia.org/wiki/Epoch_(reference_date)#Computing)

---

### Post by maxpol on 2011-10-04
> **sisco311 said:**
> Traditionally, in Unix/Linux January 1, 1970 is the epoch, but 0 should work too. 

[http://en.wikipedia.org/wiki/Epoch_(reference_date)#Computing](http://en.wikipedia.org/wiki/Epoch_(reference_date)#Computing)

Mhmmm....trying to work it out here... I used the example of May 24,1993 at 11:23:45. Converted into seconds (from 0) it is 15074625sec. From there I add a billion? Then I can only get the years in a proper number. How do I get the months and days from that? Sorry for being such a pain, but this is my first project in python... and Im still trying to get the hang of it.

---

### Post by Vaphell on 2011-10-04
you assume some year to be 'the beginning of time' for calculation purposes. Just like sisco said traditionally 1970 is used for that (everything else is number of seconds from that date) but in your example you can take year of birth as '0' - it doesn't really matter. Either way you are sure you won't get negative numbers as time goes only forward.
So you take the leftovers (month/day/hr/min/sec) and transform it to seconds, apply the offset, transform back. The only difference is  that instead of getting full date but using huge numbers in the process (2000 would be over 62*10^9 seconds) you work with smaller numbers but have to add the year back at the end. Let's say your year 0 was 1970 and you got 44 years - 1970+47 is the answer.
It's not really mandatory to do but huge numbers can cause problems (integer overflows and other stuff related to computer architecture and specifics of programming languages) so it's good to tone the numbers down if the problem allows it.

edit:
answer to your question - modulo arithmetic

```
>>> 1000000000/31104000
32
>>> 1000000000%31104000
4672000
>>> 31104000*32+4672000
1000000000
```

% returns the remaining part. 1000000000/31104000 is 32-something so 32 years, but you want to take the leftover and repeat the operation, this time with month-in-seconds. That would be 4672000 in my example. You repeat that with each unit until you get to seconds.
It's not unlike normal numerical system. If you want to know how many hundreds is in 345 you divide by 100. Get 3, take 45 further, divide by 10 to get 4, pass remaining 5 further.

---

### Post by maxpol on 2011-10-05
Awesome! Thanks to all you guys for the help! I think I've got a rough program here that does a calculation. It seems to be right... Thanks a lot for putting up with me! Definitely great help!

---


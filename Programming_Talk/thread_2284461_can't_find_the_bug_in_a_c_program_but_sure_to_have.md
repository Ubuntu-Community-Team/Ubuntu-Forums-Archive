---
title: "can't find the bug in a c program but sure to have a bug"
date: 2015-06-29
forum: Programming Talk
---

### Post by shawon2 on 2015-06-29
I tried to write a program to find the day on a specific date. I wrote this:
Code:
```
#include <stdio.h>
#include <string.h>

int lp_yr(int yr1, int yr2) //to count the leap year(s)
{
    int x = yr1, count = 0;
    while(x <= yr2) {
        if(x % 4 == 0 && x % 100 != 0) {
            count++;
        }
        else if(x % 100 == 0){
            if(x % 400 == 0) {
                count++;
            }
        }
        x += 4 - (x % 4);
    }
    return count;
}
int mnth_day(int mnth) // to count the days. please read the complete code
{
    int x = 1, day = 0;
    for(; x < mnth; x++) {
        if((x <= 7 && x % 2 != 0) || (x > 7 && x % 2 == 0)) {
            day += 31;
        }
        else {
            day += 30;
        }
    }
    if(mnth <= 2) {
        return day;

    }
    return day - 2;
}
int intval(int yr1, int mnth1, int dat1, int yr2, int mnth2, int dat2)
{
    int dur, x;
    x = lp_yr(yr1, yr2);
    if(yr1 == yr2 && mnth1 > 2 && mnth2 > 2) {
        x = 0;
    }
    dur = (yr2 - yr1) * 365 + (mnth_day(mnth2) - mnth_day(mnth1)) + (dat2 - dat1) + x;
    return dur;
}
int main()
{
    int yr1, yr2, mnth1, mnth2, dat1, dat2, x, y, z, dur, m, n, o;
    char week[7][5] = {"sat", "sun", "mon", "tue", "wed", "thu", "fri"};
    char day[5];
    printf("\t:Today:\nDate: ");
    scanf("%d", &dat1);
    printf("Month: ");
    scanf("%d", &mnth1);
    printf("Year: ");
    scanf("%d", &yr1);
    printf("Day : ");
    scanf("%s", day);
    m = yr1, n = mnth1, o = dat1;
    for(y = 0; y < 7; y++) {
        if(strcmp(day, week[y]) == 0) {
            break;
        }
    }
    printf("\n\tReady for input(Enter date = 0 to exit)\n\t\t--------------\n\n");
    while(1) {
        printf("Date: ");
        scanf("%d", &dat2);
        printf("Month: "), scanf("%d", &mnth2);
        printf("Year: "), scanf("%d", &yr2);
        z = 1;
        yr1 = m, mnth1 = n, dat1 = o;
        if(yr2 < yr1) {
            x = yr1, yr1 = yr2, yr2 = x;
            x = mnth1, mnth1 = mnth2, mnth2 = x;
            x = dat1, dat1 = dat2, dat2 = x;
            z = -1;
        }
        else if(yr1 == yr2) {
            if(mnth2 < mnth1) {
                x = mnth1, mnth1 = mnth2, mnth2 = x;
                x = dat1, dat1 = dat2, dat2 = x;
                z = -1;
            }
            else if(dat2 < dat1) {
                x = dat1, dat1 = dat2, dat2 = x;
                z = -1;
            }
        }
        dur = intval(yr1, mnth1, dat1, yr2, mnth2, dat2) - 1;
        x = (7 + (dur % 7) * z + y) % 7;
        printf("%s\n", week[x]);
    }
    return 0;
}
```
So this is the program. some output :
    :Today:
Date: 29
Month: 6
Year: 2015
Day : mon

    Ready for input(Enter date = 0 to exit)
        --------------

Date: 3
Month: 3
Year: 1980
mon
Date: 6
Month: 3
Year: 1980
thu
Date: 31
Month: 12
Year: 1700
sat(WRONG.WHY?)
Date:..........................
Please help me find the damn bug!:mad:

---

### Post by TheFu on 2015-06-29
Why not use the debugger? Step line by line, look at values, when they don't look correct, figure out why.

Or [http://rosettacode.org/wiki/Day_of_the_week#C](http://rosettacode.org/wiki/Day_of_the_week#C)

---

### Post by steeldriver on 2015-06-29
... don't forget that the "right" answer in the final case may depend on your locale - and the calendar that was in effect there in 1700

---

### Post by shawon2 on 2015-06-30
is my algorithm right or wrong?

---

### Post by shawon2 on 2015-06-30
Eureka:pFound the bug at last. I couldn't but share with you.
In function mnth_day the bug was there.
function mnth_day:
```
int mnth_day(int mnth) // to count the days. please read the complete code
{
    int x = 1, day = 0;
    for(; x < mnth; x++) {
        if((x <= 7 && x % 2 != 0) || (x > 7 && x % 2 == 0)) {
            day += 31;
        }
        else {
            day += 30;
        }
    }
    if(mnth <= 2) {
        return day;

    }
    return day - 2;
}
```
and to find the interval the function was:
```
int intval(int yr1, int mnth1, int dat1, int yr2, int mnth2, int dat2)
{
    int dur, x;
    x = lp_yr(yr1, yr2);
    if(yr1 == yr2 && mnth1 > 2 && mnth2 > 2) {
        x = 0;
    }
    dur = (yr2 - yr1) * 365 + (mnth_day(mnth2) - mnth_day(mnth1)) + (dat2 - dat1) + x;
    return dur;
}
```
Now consider we want to find the interval between 31/12/1792 and 1/1/1793, what should be the result?1?
But output for this would be 2, not 1;
Why?
In this case, function intval works like the following:
1.(1793 - 1792) * 365 +;
2.(0-334(not 335!wrong)) +;
3.1 - 31 +;
4.1 +;
sum is 2.
Here mnth_day count 12/1792 as 334 not 335 even it is a leap year.
Now I solved this problem:
```
int mnth_day(int mnth, int yr)
{
    int x = 1, day = 0;
    for(; x < mnth; x++) {
        if((x <= 7 && x % 2 != 0) || (x > 7 && x % 2 == 0)) {
            day += 31;
        }
        else {
            day += 30;
        }
    }
    if(mnth <= 2) {
        return day;

    }
    else if((yr % 4 == 0 && yr % 100 != 0) || (yr % 100 == 0 && yr % 400 == 0  )) {
        return day - 1;
    }
    return day - 2;
}
```
I know it is a very elementary problem in c. But as i am  new to it, it was a challenge for me.
Now solving this, I shared my solution with you, don't take it otherwise.
Thanks for the responses.

---


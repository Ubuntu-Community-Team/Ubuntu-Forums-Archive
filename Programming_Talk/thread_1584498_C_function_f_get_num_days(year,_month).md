---
title: "C function f_get_num_days(year, month)"
date: 2010-09-29
forum: Programming Talk
---

### Post by giuspen on 2010-09-29
Hello,
does anybody know if there's a standard C library that, given year and month, can return the number of days of the month?
Thanks.

---

### Post by giuspen on 2010-09-29
this is not from a library but is tiny and seems to work fine for present and future years:
[PHP]unsigned char  f_get_num_days(unsigned char month, unsigned short year)
{
   unsigned char  ret_val = 0;
   
   switch(month)
   {
      case 1:
      case 3:
      case 5:
      case 7:
      case 8:
      case 10:
      case 12:
         ret_val = 31;
         break;
      case 4:
      case 6:
      case 9:
      case 11:
         ret_val = 30;
         break;
      case 2:
         ret_val = ( (year - 2008) % 4 == 0 ? 29 : 28);
         break;
      default:
         break;
   }
   return ret_val;
}[/PHP]

---

### Post by dwhitney67 on 2010-09-29
You should look up the proper definition of a leap year.  What you have coded is not entirely correct.

IIRC, a leap year is any year that is divisible by 4, but not by 100, unless it is divisible by 400.  I hope that makes sense.

```

int isLeapYear(int year)
{
   return ( ((year % 4 == 0) && !(year % 100 == 0)) || (year % 400 == 0) );
}

```

P.S.  I have not verified the code/logic above.  Good luck!

P.S #2  The year 1900 was NOT a leap year, but the year 2000 was.

---

### Post by worksofcraft on 2010-09-29
The standard library functions mktime and difftime can be used for this. essentially mktime lets you specify a date in an invalid format (like the 10000th of January 2010 and then it "normalizes" it to a proper calendar time and date.

A [thread here]("http://ubuntuforums.org/showthread.php?t=1576739") looked at these functions and some of their problems. You will see that chosing to code it yourself is not an unreasonable thing to do when it's actually a simple algorithm...

but... you can't depend on the many years of scrutiny and testing that standard libraries will have been through and so must put extra effort into ensuring your algorithm is correct ;)

---


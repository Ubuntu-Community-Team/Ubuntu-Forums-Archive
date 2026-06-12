---
title: "difftime() in date"
date: 2008-12-27
forum: Programming Talk
---

### Post by jon zendatta on 2008-12-27
hell0.how to determine the difference between two dates, then convert to number of days i think the problem is i am using wrong format to input 'harvestdate'(end_date)! the objective of this script is to estimate fruit size at harvest date, based on an average daily growth rate. cheers...
```

#include <stdio.h>
#include <time.h>

    int main()
    {
    time_t start, harvestdate;
    double dif;
    int size, days, count;
    time ( &start) ;

    printf("input harvest date\n");
    scanf("%X", &harvestdate); // ??
    printf("input size\n");
    scanf("%d", &size);

    time ( &harvestdate ) ;
    dif = difftime ( harvestdate, start) ;

    days = (int) dif / 86400;
    count = (int) days * 0.72 + size;
    printf("count = %d\n", count);
    return 0;
    }
    
```

---

### Post by dwhitney67 on 2008-12-27
I'm not sure you want the operator to input the harvest date in hexadecimal?  The format in the scanf() seems to imply that.

You also realize that the input, for the difftime() to work, will need to be the number of seconds since 1970/01/01 00:00:00.

I would suggest that you prompt the operator for a calendar date (e.g. 2009/04/22) as a string, and then use strptime() followed by mktime() to convert the input date into the number of seconds since the *nix epoch.  Then you can use difftime().

Your code is very basic in the sense that it performs no error checking; you may want to consider checking the input date to ensure that it is beyond the current date, and that it does not extend beyond the 2038 time-frame, which is the end-date period for *nix time functions.

---

### Post by jon zendatta on 2008-12-27
thanks dwhitney67. yes this program is very simple, as there are plenty of things i want to add once i get difftime() working. that is interesting what you said for calculating difftime & it somewhat contradicts an example given [http://www.cplusplus.com/reference/clibrary/ctime/difftime.htm](http://www.cplusplus.com/reference/clibrary/ctime/difftime.htm).
as i assumed i was just getting total sec's between start & harvest date then dividing by 86400 to get number of days.i will have another look at this & post next problem.
cheers:)

---

### Post by dwhitney67 on 2008-12-28
The link you provided did not work, nevertheless I was able to track down an example at the Cplusplus site.  The example I saw performed a delta calculation between two system time snapshots; in between, the operator was prompted to enter their name.

Here's an example of the steps I suggested you employ (note, that it does not provide any error checking):
[php]
#include <stdio.h>
#include <time.h>

int main()
{
  char date[11] = {0};

  printf("Input the harvest date in the following format YYYY/MM/DD: ");
  fgets(date, sizeof(date), stdin);

  struct tm tm_struct;

  strptime(date, "%Y/%m/%d", &tm_struct);

#ifdef DEBUG
  printf("year  = %d\n", tm_struct.tm_year);
  printf("month = %d\n", tm_struct.tm_mon);
  printf("day   = %d\n", tm_struct.tm_mday);
#endif

  time_t harvest = mktime(&tm_struct);
  time_t diff    = difftime(harvest, time(0));

#ifdef DEBUG
  printf("diff = %d\n", (int)diff);
#endif

  const unsigned int SECS_PER_DAY = 60 * 60 * 24;
  const unsigned int SECS_PER_HR  = 60 * 60;
  const unsigned int SECS_PER_MIN = 60;

  unsigned int days  = diff / SECS_PER_DAY;
  diff = diff % SECS_PER_DAY;
  unsigned int hours = diff / SECS_PER_HR;
  diff = diff % SECS_PER_HR;
  unsigned int minutes = diff / SECS_PER_MIN;
  diff = diff % SECS_PER_MIN;
  unsigned int seconds = diff;

  printf("Time till harvest:  %d days, %02d hours, %02d minutes, and %02d seconds.\n", days, hours, minutes, seconds);

  return 0;
}
[/php]

---

### Post by jon zendatta on 2008-12-28
awesome that will work a treat..as you can see i'm an apple grower not a computer programmer > :KS

---


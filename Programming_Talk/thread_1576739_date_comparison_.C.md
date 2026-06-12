---
title: "date comparison .C"
date: 2010-09-17
forum: Programming Talk
---

### Post by jon zendatta on 2010-09-17
I want to get space between two dates, but it gives wrong answer
```
#include <stdio.h>
#include <time.h>
int main()
{
  int size, harvestsize;
  char  date[11] = {0};
  printf("Input harvest date in the following format YYYY/MM/DD: ");
  fgets(date, sizeof(date), stdin);

  struct tm tm_struct;

  strptime(date, "%Y/%m/%d", &tm_struct);

#ifdef DEBUG
  printf("year  = %d\n", tm_struct.tm_year);
  printf("month = %d\n", tm_struct.tm_mon);
  printf("day   = %d\n", tm_struct.tm_mday);
#endif

  time_t birthday = mktime(&tm_struct);

  time_t diff    = difftime(birthday, time(0));

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
  printf("Input size as an integer\n");
  scanf("%d", &size);

  harvestsize = (int) days * 0.72 + size;
   
  printf("harvest size = %d\n", harvestsize);
  printf("Time till harvest:  %d days, %02d hours, %02d minutes, and %02d seconds.\n", days, hours, minutes, seconds);


  return 0; 
  }
```

---

### Post by Tony Flury on 2010-09-17
> **jon zendatta said:**
> I want to get space between two dates, but it gives wrong answer
```
#include <stdio.h>
#include <time.h>
int main()
{
  int size, harvestsize;
  char  date[11] = {0};
  printf("Input harvest date in the following format YYYY/MM/DD: ");
  fgets(date, sizeof(date), stdin);

  struct tm tm_struct;

  strptime(date, "%Y/%m/%d", &tm_struct);

#ifdef DEBUG
  printf("year  = %d\n", tm_struct.tm_year);
  printf("month = %d\n", tm_struct.tm_mon);
  printf("day   = %d\n", tm_struct.tm_mday);
#endif

  time_t birthday = mktime(&tm_struct);

  time_t diff    = difftime(birthday, time(0));

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
  printf("Input size as an integer\n");
  scanf("%d", &size);

  harvestsize = (int) days * 0.72 + size;
   
  printf("harvest size = %d\n", harvestsize);
  printf("Time till harvest:  %d days, %02d hours, %02d minutes, and %02d seconds.\n", days, hours, minutes, seconds);


  return 0; 
  }
```
Give us some clues - what is the debug output for instance ?

---

### Post by jon zendatta on 2010-09-17
```
Program exited normally.
(gdb) 
```
When I run the code it gives an abnormally high number

---

### Post by spjackson on 2010-09-18
```

struct tm tm_struct;

strptime(date, "%Y/%m/%d", &tm_struct);  

```I think that your main problem is that tm_struct is not properly initialized. strptime only sets those members that are given in the string, leaving other members alone. I suggest you add e.g.

```

memset(&tm_struct, 0, sizeof(tm_struct));

```before calling strptime (and include string.h).

---

### Post by dwhitney67 on 2010-09-18
@ jon zendatta -

I also recommend that you verify the user's input, to ensure that it conforms to the date specifications that you outlined in your prompt.  It also wouldn't hurt to validate the actual date values too.

For your convenience, I threw this together (note that I do not validate the actual year value given; only its size):
```

...

int isValidDate(const char* date)
{
  char year[5], month[3], day[3];

  return (sscanf(date, "%4s/%2s/%2s", year, month, day) == 3 &&
          strlen(year) == 4 && strlen(month) == 2 && strlen(day) == 2 &&
          strcmp(month, "00") > 0 && strcmp(month, "13") < 0 &&
          strcmp(day, "00") > 0 && strcmp(day, "32") < 0);
}

...

int main()
{
...
  char date[12] = {0};  // allow extra space for the newline character

  for (;;)
  {
    printf("Input harvest date in the following format YYYY/MM/DD: ");
    fgets(date, sizeof(date), stdin);

    // check if valid input given.
    if (!strchr(date, '\n') || !isValidDate(date))
    {
      printf("Bad date given; try again...\n\n");

      // flush stdin
      while (getchar() != '\n');

      continue;
    }

    // if we reach here, user input is good.
    break;
  }

...
}

```

---

### Post by jon zendatta on 2010-09-18
Dwhiteney67 cheers. yeah that one was above the skillset of an apple grower:KS

---

### Post by jon zendatta on 2010-09-18
almost there. now conflicting types for 'date'.
line 18 and 48.help please
```
#include <stdio.h>
#include <time.h>
#include <string.h>
#include <stdlib.h>

int isValidDate(const char* date)
{
  char year[5], month[3], day[3];

  return (sscanf(date, "%4s/%2s/%2s", year, month, day) == 3 &&
          strlen(year) == 4 && strlen(month) == 2 && strlen(day) == 2 &&
          strcmp(month, "00") > 0 && strcmp(month, "13") < 0 &&
          strcmp(day, "00") > 0 && strcmp(day, "32") < 0);
}
int main()
{
  int size, harvestsize;
  char date[12] = {0};  
  for (;;)
  {
    printf("Input harvest date in the following format YYYY/MM/DD: ");
    fgets(date, sizeof(date), stdin);

    // check if valid input given.
    if (!strchr(date, '\n') || !isValidDate(date))
    {
      printf("Bad date given; try again...\n\n");

      // flush stdin
      while (getchar() != '\n');

      continue;
    }

    // if we reach here, user input is good.
    break;
  }
  struct tm tm_struct;

  strptime(date, "%Y/%m/%d", &tm_struct);

#ifdef DEBUG
  printf("year  = %d\n", tm_struct.tm_year);
  printf("month = %d\n", tm_struct.tm_mon);
  printf("day   = %d\n", tm_struct.tm_mday);
#endif

  time_t date = mktime(&tm_struct);

  time_t diff    = difftime(date, time(0));

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

  printf("Input current size as an integer\n");
  scanf("%d", &size);

  harvestsize = (int) days * 0.72 + size;
   
  printf("harvest size = %d\n", harvestsize);
  printf("Time till harvest:  %d days, %02d hours, %02d minutes, and %02d   seconds.\n", days, hours, minutes, seconds);

  return 0;  
}
```

---

### Post by worksofcraft on 2010-09-18
> **jon zendatta said:**
> almost there. now conflicting types for 'date'.
line 18 and 48.help please


you define date as char[12] then later as time_t

also I think time_t compiles to a long not an int, so your diagnostics may malfunction with large time differences.

---

### Post by worksofcraft on 2010-09-18
Just an after thought,

If you move your diagnostic printout AFTER the call to mktime in your original program, you would see that it all gets corrupted by incorporating garbage from the uninitialized data fields into the tm_struct.

To avoid this kind of problem, C++ encourages you to define constructors for your objects and you can then make sure that an object will always be constructed only with sensible legitimate values, before it can get used... Here let me give you an example:
```

struct mytime: tm {
	// constructor: The compiler will make sure this is called before
	// you can use a mytime struct.
	mytime() {
		time_t Now; // to hold current time
		time(&Now);
		gmtime_r(&Now, this); // initialize this structure with current time
	}

	// input
	void read(const char * Prompt) {
		char  date[11] = {0};
 		printf(Prompt);
		fgets(date, sizeof(date), stdin);
		strptime(date, "%Y/%m/%d", this); // add your validity checks if you like
		// calling this "normalises" the values anyway, so like 29th Feb
		// is 1st March when it isn't a leap year
		mktime(this);
	}

	// output
	void show() {
		printf("year  = %d\n", tm_year);
		printf("month = %d\n", tm_mon);
		printf("day   = %d\n", tm_mday);
	}
};

int main()
{
  int size, harvestsize;

  mytime tm_struct;
  tm_struct.read("Input harvest date in the following format YYYY/MM/DD: ");

  time_t birthday = mktime(&tm_struct);
  tm_struct.show();

  time_t diff    = difftime(birthday, time(0));
// ...etcetera

```

---


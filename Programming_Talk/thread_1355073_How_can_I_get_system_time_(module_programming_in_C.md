---
title: "How can I get system time ?(module programming in C)"
date: 2009-12-14
forum: Programming Talk
---

### Post by fenerista on 2009-12-14
do_gettimeofday(&tv1)
current_kernel_time()

do_gettimeofday function returns a value like that when the time was about 21:42:  "1260819441.705069"

and current_kernel_time() function returns a value similar to do_gettimeofday's value.

the print code is for tv1:
```
len += sprintf(buf,"%10i.%06i\n",(int) tv1.tv_sec, (int) tv1.tv_usec);
```


I don't know what these functions returns which time. 
[COLOR="SeaGreen"]EDIT: They return seconds  that last from 1.1.1970 to now[/COLOR]
I want to get the time as "21:42"; (sure the time might be as seconds or hour and minute variables)
Is there a function for this ?

---

### Post by MindSz on 2009-12-14
Try this.

```

#include <stdio.h>
#include <string.h>
#include <time.h>

int i, j, AuxInt;
char AuxString1[20];
char AuxString2[20];

time_t fechaTM; // Date since 01-01-1970 00:00:00
struct tm *fecha_actual; // Store current date
	
int main(void)
{
    time(&fechaTM);
    fecha_actual = localtime(&fechaTM);

    strftime(AuxString1, 10, "%x ", fecha_actual);
    strftime(AuxString2, 10, "%X", fecha_actual);

    printf("%s %s\t", AuxString1, AuxString2);
    printf("\n");
  return 0;
}
```

Also, have a look at the strftime() function for more output styles.

---

### Post by fenerista on 2009-12-14
it's working but  I am doing a module there is even no main  or printf function. like below

```
#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/init.h>

static int int1 __initdata = 5;

static int __init start(void)
{
	printk(KERN_WARNING "hello Modul world -2 %d\n", int1);
	return 0;
}
static void __exit finish(void)
{
	printk(KERN_WARNING " bye Modul world -2 %d\n", int1);
}

module_init(start);
module_exit(finish);
```

---

### Post by LKjell on 2009-12-14
There are many ways to do times on.

Here is another
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

struct tm *get_time()
{
	time_t sec = time(NULL);
	struct tm *stime = localtime(&sec);
	return stime;
};

int main()
{
		struct tm *stime = get_time();
		
		printf("%.2d:%.2d:%.2d >", stime->tm_hour, stime->tm_min, stime->tm_sec);

		return EXIT_SUCCESS;
}
```

---

### Post by fenerista on 2009-12-14
please write a module not classic C program.

---

### Post by dwhitney67 on 2009-12-14
Look at this [link]("http://patchwork.kernel.org/patch/35637/") to see if there is anything useful that you can use in your code.

From what it appears, the _offset() function might be what you need to compute the calendar date.  You will need to implement this function within your module code, since it does not appear in the existing kernel.  A better name would also be desirable.

---

### Post by fenerista on 2009-12-14
> **dwhitney67 said:**
> Look at this [link]("http://patchwork.kernel.org/patch/35637/") to see if there is anything useful that you can use in your code.

From what it appears, the _offset() function might be what you need to compute the calendar date.  You will need to implement this function within your module code, since it does not appear in the existing kernel.  A better name would also be desirable.

Yes probably you are right 

1260819441.705069/60 min
/60 hour
/24 day
/~365
=39 years //from 1.1.1970

and __offtime program is making this. I'll try.d

But probably there is a function that does this for us in linux.

---

### Post by fenerista on 2009-12-15
I found the function and header file.

```
#include <asm/rtc.h>

struct rtc_time mytime;

get_rtc_time(&mytime);
	
mytime.tm_hour, mytime.tm_min

//tm_hour, it's UTC time;
```

you can use these in your module.

if you want more resolution you have this variables.
(
struct rtc_time {
	int tm_sec;
	int tm_min;
	int tm_hour;
	int tm_mday;
	int tm_mon;
	int tm_year;
	int tm_wday;*
	int tm_yday;*
	int tm_isdst;*
};


*notused
)

---

### Post by grayrainbow on 2009-12-15
Looks simpler then 'pwd' :)
Btw, do you have some device in mind or just playing?

---

### Post by fenerista on 2009-12-18
Just for a lesson at univercity, I am trying to add functions to keyboard, eaxmple if you press ctrl+h the system print the system time to the logs if you press ctrl+p the system print the process list to the logs.

 and  mapping : changing the keyboard to a different keyboard: if you press 'A' keyboard will write 'S' if oyu press 'D' keyboard will write 'G'...

and these making me very stresful.:(

---


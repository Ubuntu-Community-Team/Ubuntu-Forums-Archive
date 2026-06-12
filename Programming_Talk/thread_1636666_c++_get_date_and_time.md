---
title: "c++ get date and time"
date: 2010-12-03
forum: Programming Talk
---

### Post by Woody1987 on 2010-12-03
In my app I need to get the date and time and put them together into a string. I can basically do this but with one problem. The year instead of displaying as 2010, displays as 2,010. How do I remove this comma?

```

string getDate()
{
	string dateTime;

	time_t calender_time;
	struct tm today;
	calender_time = time(NULL);
	today = *localtime(&calender_time);

	stringstream out;

	out << (today.tm_year + 1900);
	dateTime = out.str();
	out.str("");
	dateTime += "/";

	out << (today.tm_mon + 1);
	dateTime += out.str();
	out.str("");
	dateTime += "/";

	out << (today.tm_mday);
	dateTime += out.str();
	out.str("");
	dateTime += " ";

	out << (today.tm_hour);
	dateTime += out.str();
	out.str("");
	dateTime += ":";

	out << (today.tm_min);
	dateTime += out.str();
	out.str("");
	dateTime += ":";

	out << (today.tm_sec);
	dateTime += out.str();
	out.str("");

	return dateTime;
}
```

It should return:
2010/12/3 17:35:9

Instead it returns:
2,010/12/3 17:35:9

Also any suggestions on shortening this code would be appreciated.

---

### Post by dwhitney67 on 2010-12-03
My suggestion -- don't reinvent the wheel.
```

// To build:
//   g++ datetime.cpp -lboost_date_time
//
#include <boost/date_time/posix_time/posix_time.hpp>
#include <locale>
#include <string>
#include <sstream>
#include <iostream>

int main()
{
   using namespace boost::posix_time;
   using namespace std;

   // get the current time
   ptime       now   = second_clock::local_time();

   // define current locale
   time_facet* facet = new time_facet("%x %X");
   locale      loc   = locale(locale("en_US.UTF-8"), facet);

   // put the date/time into our locale's format
   stringstream ss;
   ss.imbue(loc);
   ss << now;

   cout << ss.str() << endl;
}

```


P.S.  If you want to do it your way, at least employ the use of the stringstream to its fullest capability:
```

stringstream out;

out << (today.tm_year + 1900)
    << "/"
    << (today.tm_mon + 1)
    << '/'
    << ...;


```

---

### Post by Woody1987 on 2010-12-03
Thats great. One slight problem though, it displays PM after the time. How do I remove this and get it to display 24 hour time?

---

### Post by dwhitney67 on 2010-12-03
> **Woody1987 said:**
> Thats great. One slight problem though, it displays PM after the time. How do I remove this and get it to display 24 hour time?

Employing a little research, I've determined that you require:
```

time_facet* facet = new time_facet("%Y/%m/%d %H:%M:%S");

```
If you are interested in developing code, you better develop an interest in Googling for documentation (and hence answers) too.  Reference the Boost documentation if you intend to use it.

---

### Post by Arndt on 2010-12-03
> **dwhitney67 said:**
> Employing a little research, I've determined that you require:
```

time_facet* facet = new time_facet("%Y/%m/%d %H:%M:%S");

```
If you are interested in developing code, you better develop an interest in Googling for documentation (and hence answers) too.  Reference the Boost documentation if you intend to use it.

I would guess that selecting a different locale from en_US should also do it, but I haven't tried.

---

### Post by dwhitney67 on 2010-12-03
> **Arndt said:**
> I would guess that selecting a different locale from en_US should also do it, but I haven't tried.

It was a few weeks ago (maybe slightly longer) that I figured out how to determine which locales are installed on my system, and of course, how to add other ones.  Now, that knowledge is has evaporated.

The OP seems to reside in the UK, so if I could figure out how to add his locale, then perhaps I could have presented something better.

---

### Post by worksofcraft on 2010-12-03
> **dwhitney67 said:**
> It was a few weeks ago (maybe slightly longer) that I figured out how to determine which locales are installed on my system, and of course, how to add other ones.  Now, that knowledge is has evaporated.

The OP seems to reside in the UK, so if I could figure out how to add his locale, then perhaps I could have presented something better.

Have you tried:
```

sudo locale-gen en_GB.UTF-8

```

... also if one IS going to be using locales, then one might want to consider how to internationalize the string fragments that are fed to string streams. Personally I prefer to use formats because they are much more manageable and flexible for the translators.

---


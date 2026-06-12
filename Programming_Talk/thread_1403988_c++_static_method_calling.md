---
title: "c++ static method calling"
date: 2010-02-10
forum: Programming Talk
---

### Post by marshmallow1304 on 2010-02-10
Date.h
```

...
class Date
{
    public:
      Date();
      Date(int day, int month, int year) throw (logic_error);
    ...
    static int daysInMonth(int month, int year);
    ...
}

```
Date.cc
```

#include "Date.h"
...
Date::Date(int day, int month, int year) throw (logic_error)
{
	if ((day < 1) || (day > daysInMonth(month, year))) // error line
	{
		throw logic_error("Invalid day.");
	}

	if ((month < 1) || (month > 12))
	{
		throw logic_error("Invalid month.");
	}

	if (year < 1)
	{
		throw logic_error("Invalid year.");
	}
}
...
static int daysInMonth(int month, int year)
{
	if (month == 2)
	{
		if (isLeapYear(year))
		{
			return 29;
		}
		else
		{
			return 28;
		}
	}
	else if ((month == 9) || (month == 4) || (month == 6) || (month == 10))
	{
		return 30;
	}
	else
	{
		return 31;
	}
}
...

```


It compiles fine, but when running, it gives
> undefined reference to `Date::daysInMonth(int, int)'

---

### Post by kahumba on 2010-02-11
I can only see the declaration of Date::daysInMonth(), where's the definition? Maybe the problem's there.

---

### Post by marshmallow1304 on 2010-02-11
> **kahumba said:**
> I can only see the declaration of Date::daysInMonth(), where's the definition? Maybe the problem's there.

Oops, I left that out.  I've now added it in the first post.

---

### Post by marshmallow1304 on 2010-02-11
I fixed it.  I guess I'm not supposed to preface the function with 'static' after it's already been declared as such.  I changed
```
static int daysInMonth(int month, int year)
{
...
}
```
to
```
int Date::daysInMonth(int month, int year)
{
...
{

```



c++ is not my first language.

---

### Post by kahumba on 2010-02-11
> **marshmallow1304 said:**
> This post can be deleted.
Thread or post (?)

Anyway.
The definition seems to miss "Date::" like this
```

int Date::daysInMonth(int month, int year) {
//code
}

```Btw, I didn't repeat the "static" word since afaik it's only needed in the header file.

> 
c++ is not my first language.

Same here.

---

### Post by dwhitney67 on 2010-02-11
> **kahumba said:**
> 
Btw, I didn't repeat the "static" word since afaik it's only needed in the header file.

That is correct, but to be more correct, it is only needed within the class declaration.

---

### Post by marshmallow1304 on 2010-02-11
Thank you both.

---


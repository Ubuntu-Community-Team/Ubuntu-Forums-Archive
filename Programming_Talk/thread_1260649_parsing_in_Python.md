---
title: "parsing in Python"
date: 2009-09-07
forum: Programming Talk
---

### Post by filifunk on 2009-09-07
caveat: I'm a beginner.

So I took some historical data from yahoo! finance.  I figured out how to separate out just the dates into x.

so, I figured I'd try and parse it out using strptime.  A while ago someone mentioned using the datetime module, but I'll figure that out later because I have a book that shows how to use strptime.

so I've put the dates into x.  The dates look like this: 

```


In [7]: x
Out[7]: 
array(['2009-09-04', '2009-09-03', '2009-09-02', '2009-09-01',
       '2009-08-31', '2009-08-28', '2009-08-27', '2009-08-26',
       '2009-08-25', '2009-08-24', '2009-08-21', '2009-08-20',
       '2009-08-19', '2009-08-18', '2009-08-17', '2009-08-14',
etc....

```

Theres about a years worth of dates in there, so I wrote this code to parse it:

```


In [8]: for i in enumerate(x):
   ...:         strptime(i, '%Y-%m-%d')
   ...: 


```

I get this:

TypeError: expected string or buffer


but when I do it like this working on a single data point it's fine

```


In [10]: strptime('2008-09-09', '%Y-%m-%d')
Out[10]: time.struct_time(tm_year=2008, tm_mon=9, tm_mday=9, tm_hour=0, tm_min=0, tm_sec=0, tm_wday=1, tm_yday=253, tm_isdst=-1)


```

how do I make this work?

---

### Post by croto on 2009-09-07
enumerate(list) returns the pairs [(0,el1), (1,el2), etc] where el1, el2, ... are the elements of list.

what you want is simply:
```

In [8]: for i in x:
   ...:         strptime(i, '%Y-%m-%d')
   ...:

```

check it out!

---

### Post by filifunk on 2009-09-07
hehe silly me.  Thanks =)

---


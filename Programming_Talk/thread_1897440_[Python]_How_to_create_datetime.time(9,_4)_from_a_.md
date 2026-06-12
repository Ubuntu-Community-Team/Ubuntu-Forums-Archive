---
title: "[Python] How to create datetime.time(9, 4) from a string?"
date: 2011-12-19
forum: Programming Talk
---

### Post by kramer65 on 2011-12-19
Hello,

With the help of the psychopg2 adapter I am getting some information from a postgresql database, of which one thing is a time in the following format: *datetime.time(9, 4)*

I now want to do an if statement to compare whether the time is equal to (for example) '09:04:00' (which in this case would be true). In order to do this I have to create a time from a string. I tried this with [datetime.strptime](http://docs.python.org/library/datetime.html#datetime.datetime.strptime)  and [time.strptime](http://docs.python.org/library/time.html#time.strptime). So to see if either of them worked I wrote the following:
```

# I first get a list of times from the DB and print it here to see what's in there
print(time_list_from_db)

datetime_strptime = datetime.strptime('09:04:00', '%H:%M:%S')
print(datetime_strptime)
time_strptime = time.strptime('09:04:00', '%H:%M:%S')
print(time_strptime)

if datetime_strptime in time_list_from_db:
    print('datetime.strptime works')
elif time_strptime in time_list_from_db:
    print('time.strptime works')
else:
    print('none of them work')
```
The result is as follows:
```
[datetime.time(9, 4), datetime.time(9, 5), datetime.time(9, 6)]
1900-01-01 09:04:00
time.struct_time(tm_year=1900, tm_mon=1, tm_mday=1, tm_hour=9, tm_min=4, tm_sec=0, tm_wday=0, tm_yday=1, tm_isdst=-1)
none of them work
```
So the problem is that I cannot compare either of these two to the time I get from the DB.

Does anybody know of a way that I can convert a string to a struct_time like this: *datetime.time(9, 4)* so that I can compare it to the times I get from the database? All tips are welcome!

---

### Post by simeon87 on 2011-12-19
Why not convert the datetime.time to a string and compare strings?

```
>>> str(datetime.time(9, 4))
'09:04:00'
```

---


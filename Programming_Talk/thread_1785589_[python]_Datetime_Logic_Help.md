---
title: "[python] Datetime Logic Help"
date: 2011-06-18
forum: Programming Talk
---

### Post by Pyro.699 on 2011-06-18
Hey,

So every now and then i run into a scenario where i have to handle datetime objects across many timezones and things start to become confusing for me. I have a bit of code that is pythonicly sound, but i need someone to help me verify that it is logically sound.

```

user@server:~/path$ date
Sat Jun 18 08:19:06 PDT 2011

```[php]
>>> import datetime
>>> datetime.datetime.now()
datetime.datetime(2011, 6, 18, 8, 19, 24, 214510)
[/php]Going from a datetime.datetime/datetime.date object to a unix time integer. This is the value that is stored on the server and returned to the user. The users timezone is saved as an integer valued -14 to 12.
[php]
def to_unix_time(dt_in, tz_off=0):
    import time, datetime
    with_timezone = dt_in + datetime.timedelta(hours=tz_off)
    create_tuple = with_timezone.timetuple()
    create_time = time.mktime(create_time) 
    return int(create_time)
[/php]Thanks for any help
~Cody

---

### Post by Arndt on 2011-06-18
> **Pyro.699 said:**
> Hey,

So every now and then i run into a scenario where i have to handle datetime objects across many timezones and things start to become confusing for me. I have a bit of code that is pythonicly sound, but i need someone to help me verify that it is logically sound.

```

user@server:~/path$ date
Sat Jun 18 08:19:06 PDT 2011

```[php]
>>> import datetime
>>> datetime.datetime.now()
datetime.datetime(2011, 6, 18, 8, 19, 24, 214510)
[/php]Going from a datetime.datetime/datetime.date object to a unix time integer. This is the value that is stored on the server and returned to the user. The users timezone is saved as an integer valued -14 to 12.
[php]
def to_unix_time(dt_in, tz_off=0):
    import time, datetime
    with_timezone = dt_in + datetime.timedelta(hours=tz_off)
    create_tuple = with_timezone.timetuple()
    create_time = time.mktime(create_time) 
    return int(create_time)
[/php]Thanks for any help
~Cody

I know that some time zones, in Australia and India, for example, are at half hour differences from others.

You may want to deal with daylight saving time, too.

---

### Post by Cheesehead on 2011-06-18
Well, I was taught that a Python timezone-aware datetime object consisted of the datetime tuple (or seconds), plus a 3-part object consisting of the UTC-offset, the time zone name, and the dst offset. Same for both Py2 and Py3: 

```
import datetime

class MyTimeZone(datetime.tzinfo):
   """
   When called, this overrides the tzinfo definitions, which are None for a timezone-naive 
   datetime object anyway, and replaces it with the US Central Daylight Time. 
   A timezone definition consists of three objects:
   The utc offset, the timezone name, and the standard-time/daylight-time flag
   """
   def utcoffset(self, dt):
      return datetime.timedelta(hours=-6)
   def tzname(self):
      return "GMT -6"
   def dst(self, dt):
      return datetime.timedelta(hours=+1)

CDT = MyTimeZone()

current_date = datetime.datetime.now()
print("Timezone-naive datetime object:")
print(current_date)
print(current_date, current_date.tzinfo)
print()

current_date = current_date.replace(tzinfo=CDT)
print("Timezone-aware datetime object:")
print(current_date)
print(current_date,
      current_date.tzinfo.utcoffset(0),
      current_date.tzinfo.tzname(),
      current_date.tzinfo.dst(0))

```

Yeah, it requires a *class* to create the three-part tzinfo object. I think it's a big kludge, but timedelta seems to like it.

I hope that helps, and doesn't confuse the issue.

---


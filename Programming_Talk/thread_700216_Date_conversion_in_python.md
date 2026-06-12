---
title: "Date conversion in python"
date: 2008-02-18
forum: Programming Talk
---

### Post by aquavitae on 2008-02-18
I'm writing a script which involves converting a text timestamp to seconds.  The conversion algorithym is called a few million times and a profile showed that its taking about half the running time of the script.  So I'm looking for ways to optimize it.  So far the fastest I've got is this:
[php]
class timefunc(object):
   ''' convert '2007/11/28', '14:53:23', '0.567354' to seconds. '''

   def __init__(self):
      self.year0 = -1
      #                  J   F   M   A   M   J   J   A   S   O   N   D
      self.monthdays = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
      for i in xrange(1, 12):
         self.monthdays[i] += self.monthdays[i - 1]

   def __call__(self, date, time, micro):
      year, month, day = float(date[:4]), int(date[5:7]), float(date[8:10])
      hours, min, sec  = float(time[:2]), float(time[3:5]), float(time[6:8])
      leapyear = (year * .25) - int(year * .25) < 0.001
      if self.year0 == -1:
         self.year0 = year
      return (hours * 3600) + (min * 60) + sec + float(micro) + \
         ((self.monthdays[month] + day) * 86400) + \
         ((year - self.year0) * (366 if leapyear else 365) * 24 * 3600)


conversion = timefunc()

secs = []
for timestamp in data:
   secs.append(conversion(*timestamp))
[/php]

Any suggestions of how to speed it up further?

---

### Post by cb951303 on 2008-02-18
BTW you might wanna do something like this for Feb. (I don't know python so I'll give an example in C) 

```

int monthdays[12] = {31, 29 - ((year % 4) > 0), 31, ....... }

```

---

### Post by popch on 2008-02-18
I do not know Python all that well, but I would be much surprised if it did not already have a date conversion module that can do what you need.

---

### Post by LaRoza on 2008-02-18
> **popch said:**
> I do not know Python all that well, but I would be much surprised if it did not already have a date conversion module that can do what you need.

There is a time module: [http://docs.python.org/lib/module-time.html](http://docs.python.org/lib/module-time.html)

(I didn't really review the OP or the module, so I don't know how much of it is useful)

---

### Post by aquavitae on 2008-02-18
Um, 29 - bool(year %4) maybe?
But I have noticed that leap years won't be handled properly in any case...  I'll see if I can fix it - anyone got suggestons of how best to do it?

---

### Post by aquavitae on 2008-02-18
Thanks LaRoza - I'm not sure either but I'll have a look.  I know th datetime module doesn't do what I want.

---

### Post by aquavitae on 2008-02-18
module-time does exactly what I want, but it takes five times longer than my method, although my method doesn't do it right yet.

---

### Post by Martin Witte on 2008-02-18
I was able to knock a little off by calculating things only once where possible

[PHP]
import time
def leap(year):
    if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
        return True
    else:
        return False

seconds_in_a_day = 86400
monthdays = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
for i in xrange(1, 12):
    monthdays[i] += monthdays[i - 1]

base = 1900 # take 1/1/1900 as basedate
# accumulate days in years
days_in_year = [0] * 201
days_in_year[0] = 365
for year in range(base + 1, base + 201):
    if leap(year):
        days_in_year[year - base]  += days_in_year[year - base - 1] + 366
    else:
        days_in_year[year - base]  += days_in_year[year - base - 1] + 365


def convert(date, time, micro):
    year, month, day = int(date[:4]), int(date[5:7]), int(date[8:10])
    hour, minute, second  = int(time[:2]), int(time[3:5]), int(time[6:8])
    number_of_days = days_in_year[year - base] + monthdays[month - 2] + day
    if leap(year) and month > 2:
        number_of_days += 1
        
    time_add = hour * 3600 + minute * 60 + second + float(micro)

    return number_of_days * seconds_in_a_day + time_add
    

secs = []
data = [('2007/11/28', '14:53:23', '0.567354')] * 100
start = time.time()
for timestamp in data:      
    secs.append(convert(*timestamp))
stop = time.time()
print stop - start
print secs
[/PHP]

Edit:
Although it seems the class also causes some overhead, when I rewrite my code more in-line with the code of OP performance decreases

[PHP]
import time

class timefunc(object):
    ''' convert '2007/11/28', '14:53:23', '0.567354' to seconds. '''
    def __init__(self):
        self.monthdays = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
        for i in xrange(1, 12):
            self.monthdays[i] += self.monthdays[i - 1]

        base = 1900 # take 1/1/1900 as basedate
        # accumulate days in years
        self.days_in_year = [0] * 201
        self.days_in_year[0] = 365
        for year in range(base + 1, base + 201):
            if leap(year):
                self.days_in_year[year - base]  += self.days_in_year[year - base - 1] + 366
            else:
                self.days_in_year[year - base]  += self.days_in_year[year - base - 1] + 365
        
    def leap(self, year):
        if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
            return True
        else:
            return False

    def __call__(self, date, time, micro):
        year, month, day = int(date[:4]), int(date[5:7]), int(date[8:10])
        hour, minute, second  = int(time[:2]), int(time[3:5]), int(time[6:8])
        number_of_days = self.days_in_year[year - base] + self.monthdays[month - 2] + day
        if leap(year) and month > 2:
            number_of_days += 1
            
        time_add = hour * 3600 + minute * 60 + second + float(micro)

        return number_of_days * 86400 + time_add


convert = timefunc()    
data = [('2007/11/28', '14:53:23', '0.567354')] * 100
secs = []
start = time.time()
for timestamp in data:      
    secs.append(convert(*timestamp))
stop = time.time()
print stop - start
[/PHP]

---

### Post by slash2314 on 2008-02-18
Please correct me if I am wrong, but I think this is a quick way to count the number of seconds since the year 0.
```


import datetime
def convert(timestamp):
	'''Takes a time stamp in iso format "2008-02-18T17:22:53.234534"'''
	#There is 365.25 days in a year so therefore seconds in a year
	YS = 365.25 * 24 * 60 * 60
	date, time= timestamp.split('T')
	year, month,day = date.split('-')
	hour,min,sec = time.split(":")
	ms = float("."+sec.split('.')[1])*1000000
	sec = int(sec.split('.')[0])
	timedelta = (datetime.datetime(int(year),int(month),int(day),int(hour),int(min),int(sec),int(ms)) - datetime.datetime(int(year),1,1))
	seconds = timedelta.seconds + float('.'+str(timedelta.microseconds))
	totalSeconds = seconds + (int(year) - 1) * YS
	return totalSeconds
	
print convert(datetime.datetime.now().isoformat())


```

---

### Post by aquavitae on 2008-02-18
Martin: Thanks, that's kinda where I got to last night also, but not quite as fast.  Don't quite understand what you mean about the performance of class vs functions though?  Which is better?  It doesn't matter which I use - just whatever's fastest.  I notice you've used a baseyear of 1900 as a constant, isn't it possible that larger dates will cause an overflow? 

Slash:  I did try something like that, using dattime, but I found the builtin functions were considerably slower than anything I wrote.  I think its because they take things into consideration which don't affect me - like DST and timezone info.

EDIT: Ok, just done a quick calc - I see using 1900 won't cause an overflow - great!

---

### Post by Martin Witte on 2008-02-19
> **aquavitae said:**
> Martin: Thanks, that's kinda where I got to last night also, but not quite as fast.  Don't quite understand what you mean about the performance of class vs functions though?  Which is better?  It doesn't matter which I use - just whatever's fastest.  I notice you've used a baseyear of 1900 as a constant, isn't it possible that larger dates will cause an overflow? 

EDIT: Ok, just done a quick calc - I see using 1900 won't cause an overflow - great!

I'm not at my Ubuntu box, so I write this from memory. I tested three versions: 1) your code, 2) the function approach in my previous post, and 3) the class approach in that post. For 100 evaluations the function approach (2) rans 20% faster than your code (1), my class (3) rans about 10% faster than yours

---

### Post by aquavitae on 2008-02-19
Thanks all, this is the best I've got and I think its as fast as it will go:

[php]
time_year0 = -1
#days to start of J   F   M   A   M    J    J    A    S    O    N    D
time_monthdays =      [0, 31, 59, 90, 120, 151, 181, 212, 243, 273, 304, 334]

def timeToSeconds(date, time, micro):
   global time_year0, time_monthdays
   ''' convert '2007/11/28', '14:53:23', '0.567354' to seconds. '''
   year, month, day = int(date[:4]), int(date[5:7]) - 1, int(date[8:10])
   hours, min, sec  = int(time[:2]), int(time[3:5]), int(time[6:8])
   
   if time_year0 == -1:
      time_year0 = year
      
   total = ((time_monthdays[month] + day) * 86400) + \
           (hours * 3600) + (min * 60) + sec + float(micro)
   
   for y in xrange(time_year0, year):
      #        366 * 86400              365 * 86400
      total += 31622400 if (y % 4) else 31536000
         
   if year % 4 and (month > 1 or (month, day == 1, 29)):
      total += 86400
      
   return total
[/php]
I ended up not using 1900 as the base year because of the loop I have.  For my situation, the data is likely to cover about a month at a time, so the loop should only usually be called once, so it doesn't cost much.

---


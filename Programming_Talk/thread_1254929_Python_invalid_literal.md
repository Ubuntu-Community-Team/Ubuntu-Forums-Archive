---
title: "Python: invalid literal"
date: 2009-08-31
forum: Programming Talk
---

### Post by filifunk on 2009-08-31
part of the script that I'm creating is:

```

for i, day in enumerate(values[:, 0]):
    market_close_time = (int(day[6:]), int(day[:2]), int(day[3:5]), \
        16, 0, 0, 0, 0, 0)


```

when I run it I get this:
  File "stock_charts.py", line 23, in <module>
    market_close_time = (int(day[6:]), int(day[:2]), int(day[3:5]), \
ValueError: invalid literal for int() with base 10: ''


I've seen this value error elsewhere in the case where the code tried to turn a string into an integer.  I'm assuming that this is saying that day*** is being taken as a string?  How do I fix this?  I'm copying it from a book!  Or at least what is the value error telling me?

---

### Post by unutbu on 2009-08-31
If I type
```

int('')
```

into a Python interpreter, I get
```

ValueError: invalid literal for int() with base 10: ''
```

So it seems that day[6:], day[:2], or day[3:5] is '' at some point in the loop.

I notice that you are using numpy indexing: values[:,0].
Cool! May I ask what book are you reading?

---

### Post by Can+~ on 2009-08-31
Wawawawait.

int(day[6:]), int(day[:2]), int(day[3:5]

MM-DD-YY => YY, MM and DD?

That's one awful way to do it, also, what happens when the day is formatted as "5-2-09"?

You should really start looking into the [datetime module (read: strptime)]("http://docs.python.org/library/datetime.html#datetime.datetime.strptime") instead of writing your adhoc parsing.

---

### Post by filifunk on 2009-08-31
> **unutbu said:**
> If I type
```

int('')
```into a Python interpreter, I get
```

ValueError: invalid literal for int() with base 10: ''
```So it seems that day[6:], day[:2], or day[3:5] is '' at some point in the loop.

I notice that you are using numpy indexing: values[:,0].
Cool! May I ask what book are you reading?


Yea!  "Beginning Python Visualization: Crafting Visual Transformation Scripts" by Shai Vaingast.  

Looks like I need to learn more numpy.  The intro said starting at chapter 4 was a good idea, but I obviously need to find the chapter with numpy to understand my issues here!

---

### Post by Greyed on 2009-09-01
If anything we need to know what day is before we can intelligently dig into why the code is choking on it.

I mean if it is as Can surmises, a date like 09-09-09 then it is obvious why the failure is happening, that's a string.  Pulling out 2 parts of a string which happen to contain characters which relate to numbers doesn't change the fact it's still a string.  In that case encapsulating it with int() would help, but not be perfect.

But that's just conjecture as we're guessing what is in day based on the error being tossed.  Not good diagnostic method.

---

### Post by filifunk on 2009-09-01
> **Greyed said:**
> If anything we need to know what day is before we can intelligently dig into why the code is choking on it.

I mean if it is as Can surmises, a date like 09-09-09 then it is obvious why the failure is happening, that's a string.  Pulling out 2 parts of a string which happen to contain characters which relate to numbers doesn't change the fact it's still a string.  In that case encapsulating it with int() would help, but not be perfect.

But that's just conjecture as we're guessing what is in day based on the error being tossed.  Not good diagnostic method.


I don't know if this helps...this is my entire code

```


from pylab import *
import csv
from time import gmtime, mktime

# modify the following to point to your data file
filepath = 'charts.dll'

# read the entire CSV file and store it in an array of lists
# use tab ('\t') as a delimiter
data = []
for row in csv.reader(open(filepath), delimiter='\t'):
    data.append(row)

# split the data to header and values
header = data[0]
values = array(data[1:])

# the first column is date information in a string format
# we transform it to a day of year format
# notice that this will not work over year boundary (need to add 365)
yearday = zeros(len(values[:, 0]))
for i, day in enumerate(values[:, 0]):
    market_close_time = (int(day[6:]), int(day[:2]), int(day[3:5]), \
        16, 0, 0, 0, 0, 0)
    yearday[i] = gmtime(mktime(market_close_time)).tm_yday
    
# plot the data
for i in range(1, 5):
    plot(yearday, values[:, i], label=header[i], linewidth=3)

# annotate the start and end dates
text(yearday[0], values[0, 1], values[0, 0])
text(yearday[-1], values[-1,1], values[-1,0])

grid()
legend()
ylabel('Stock price [USD]')
xlabel('Days from start of the year '+values[0, 0][6:])
title('Nasdaq-100 (IXNDX) Stock price, period %s-%s' % (values[-1,0], values[0, 0]))
savefig('Documents/Programming stockprice.png')


```

the charts.dll file is just the daily stock price action downloaded from Nasdaq.

---

### Post by Arndt on 2009-09-01
> **filifunk said:**
> I don't know if this helps...this is my entire code

```


from pylab import *
import csv
from time import gmtime, mktime

# modify the following to point to your data file
filepath = 'charts.dll'

# read the entire CSV file and store it in an array of lists
# use tab ('\t') as a delimiter
data = []
for row in csv.reader(open(filepath), delimiter='\t'):
    data.append(row)

# split the data to header and values
header = data[0]
values = array(data[1:])

# the first column is date information in a string format
# we transform it to a day of year format
# notice that this will not work over year boundary (need to add 365)
yearday = zeros(len(values[:, 0]))
for i, day in enumerate(values[:, 0]):
    market_close_time = (int(day[6:]), int(day[:2]), int(day[3:5]), \
        16, 0, 0, 0, 0, 0)
    yearday[i] = gmtime(mktime(market_close_time)).tm_yday
    
# plot the data
for i in range(1, 5):
    plot(yearday, values[:, i], label=header[i], linewidth=3)

# annotate the start and end dates
text(yearday[0], values[0, 1], values[0, 0])
text(yearday[-1], values[-1,1], values[-1,0])

grid()
legend()
ylabel('Stock price [USD]')
xlabel('Days from start of the year '+values[0, 0][6:])
title('Nasdaq-100 (IXNDX) Stock price, period %s-%s' % (values[-1,0], values[0, 0]))
savefig('Documents/Programming stockprice.png')


```

the charts.dll file is just the daily stock price action downloaded from Nasdaq.

Insert some print statements and run the code.

---

### Post by unutbu on 2009-09-01
Put this with the import statements at the top of the script:
[PHP]
from dateutil.parser import parse[/PHP]

Change
[PHP]
    market_close_time = (int(day[6:]), int(day[:2]), int(day[3:5]), \
        16, 0, 0, 0, 0, 0)
    yearday[i] = gmtime(mktime(market_close_time)).tm_yday
[/PHP]
to
[PHP]
    market_close_time = parse(day).replace(hour=16)
    yearday[i]=market_close_time.timetuple().tm_yday        
[/PHP]
I've (successfully) tested this with charts.dll ([http://www.nasdaq.com/aspx/historical_quotes.aspx?symbol=USD&selected=USD](http://www.nasdaq.com/aspx/historical_quotes.aspx?symbol=USD&selected=USD)) looking like this:
```

Date	Open	High	Low	Close/Last	Volume	
15:37	27.99	29.27	26.65	26.790001	508,743	
08/31/2009	28.30	28.34	27.574	28.28	295,157	
08/28/2009	28.58	29.66	28.2694	28.73	715,608	
08/27/2009	27.01	27.25	26.18	27.17	307,243	
08/26/2009	26.47	27.10	26.45	27.06	281,958	


```

I think the problem might have been that this line:```

15:37	27.99	29.27	26.65	26.790001	508,743	
```
does not get parsed properly by 
```
    market_close_time = (int(day[6:]), int(day[:2]), int(day[3:5]), \
        16, 0, 0, 0, 0, 0)
```
Using dateutil.parser.parse is much more robust.

---


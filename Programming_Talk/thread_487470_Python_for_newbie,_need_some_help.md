---
title: "Python for newbie, need some help"
date: 2007-06-29
forum: Programming Talk
---

### Post by mocqueanh on 2007-06-29
Example for Indexing
```

# Print out a date, given year, month, and day as numbers
months = [
    'January',
    'February',
    'March',
    'April',
    'May',
    'June',
    'July',
    'August',
    'September',
    'October',
    'November',
    'December'
]
# A list with one ending for each number from 1 to 31
endings = ['st', 'nd', 'rd'] + 17 * ['th'] \
        + ['st', 'nd', 'rd'] +  7 * ['th'] \
        + ['st']
year    = raw_input('Year: ')
month   = raw_input('Month (1-12): ')
day     = raw_input('Day (1-31): ')
month_number = int(month)
day_number = int(day)
# Remember to subtract 1 from month and day to get a correct index
month_name = months[month_number-1]
ordinal = day + endings[day_number-1]
print month_name + ' ' + ordinal + ', ' + year

```

I've started with Python, and just know Indexing in Python. This is the example of Indexing that i've copied from my book: beginnig Python.

Something in this code i dont understand. I dont understand the **endings**. Can you define for me ? How to automate the day number ? E.g: 17th, 2nd,....... this **endings** make it, but i cant understand the way of endings does.:o

---

### Post by Ubuntist on 2007-06-29
Endings is just an array.  If day_number is 7, for example, then the variable ordinal is set to '7' + endings[7 - 1], which is equal to '7' + 'th', or '7th'.

---

### Post by smartbei on 2007-07-01
You should remember that when you do ```
17 * ['th']
``` it actually means ```
['th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th']
```
so the whole endings line is (just passed through the python interpreter):
```

endings=['st', 'nd', 'rd', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'st', 'nd', 'rd', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'st']
```

Now, for each number, it will look up its place (-1) so 1 (-1) would be "st", 2 (-1) would be "nd", and 30 (-1) would be "th".

Hope that cleared it up.

---

### Post by dwblas on 2007-07-04
I think that all you have to do is 
endings = [ "st", "nd", "rd" ]
if the day endswith less than 4, use endings, otherwise append a "th".   So 21 endswith a "1", so you would use endings --> int(day[-1]) < 4.  25 endswith a "5" so you would append a "th"

P.S. Check out easygui for simple input stuff like this
[http://www.ferg.org/easygui/](http://www.ferg.org/easygui/)  You would use multenterbox for month, day, year

---


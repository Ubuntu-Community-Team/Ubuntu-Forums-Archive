---
title: "Suffix"
date: 2018-04-07
forum: Programming Talk
---

### Post by mahiaslam on 2018-04-07
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
endings = ['st', 'nd', 'rd'] + 17 * ['th'] \
+ ['st', 'nd', 'rd'] + 7 * ['th'] \
+ ['st']
year = input('Year: ')
month = input('Month (1-12): ')
day = input('Day (1-31): ')
month_number = int(month)
day_number = int(day)
month_name = months[month_number-1]
ordinal = day + endings[day_number-1]
print(month_name + ' ' + ordinal + ', ' + year)


This example is written in a python book, but why 17 and 7. I don't understand this part I am totally new on this. Any kind of help is appreciated.

---

### Post by QIII on 2018-04-07
Down the left side of a piece of paper, write the numbers from 1 to 31.

Then go back, start with one and write the ordinal suffix for each.

See if you catch the pattern.

---


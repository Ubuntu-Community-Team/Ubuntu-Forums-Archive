---
title: "Need help with python re.search"
date: 2021-12-20
forum: Programming Talk
---

### Post by lance bermudez on 2021-12-20
I have to be able to run this program on windows and linux. I need to be able to have it work like grep and show me my match line and the next 3 lines. I get it to show me my first line match but not the next 3 lines with this code below
```

from re import search

with open("/tmp/weathertext5","r") as file:
    for line in file:
        if search('Current conditions', line):
            print(line.strip())

        if search('Temperature:', line):
            print(line.strip())
            
        if search('TODAY', line):
            print(line.strip())

```

How do I get the next 3 lines after my match?

---

### Post by TheFu on 2021-12-20
No need to reinvent this wheel. grep already does it. I'd use 
```
$ egrep -A3 "search-term"  filename-to-search
```

If this is a school assignment, I cannot help directly. Also, I don't know python. 

In perl, I have a reverse counter from each time a matching line was found 3, 2, 1, 0.

The GNU grep program has been ported to Windows for 25+ years, so you can use the grep solution above if this isn't just a python assignment.

---

### Post by lance bermudez on 2021-12-20
Windows does not have grep that is why "reinvent this wheel." Also this is not for school but that is just what a student would say.

---

### Post by TheFu on 2021-12-20
> **lance bermudez said:**
> Windows does not have grep that is why "reinvent this wheel." Also this is not for school but that is just what a student would say.

[http://gnuwin32.sourceforge.net/packages/grep.htm](http://gnuwin32.sourceforge.net/packages/grep.htm)
I've used this since win32s was available. No clue whether that works on Win10/11

---

### Post by spjackson on 2021-12-23
I don't really know why you don't use grep as already suggested. You don't have grep on Windows unless you install it, but then you don't have Python on Windows unless you install it. My suggestion would be, install git for Windows. Git Bash has grep.

But if, for whatever reason, you really do want to write your own code in Python, then there are 3 things you need to do:


[LIST]
[*]Define precisely what you want to happen.
[*]Devise an algorithm.
[*]Code the algorithm in Python.
[/LIST]
 
Which of these steps are you struggling with?

---

### Post by schragge on 2021-12-23
[Cross-posted]("https://www.linuxquestions.org/questions/programming-9/need-help-with-python-re-search-4175705216") to LQ. Don't waste your time on what already was answered elsewhere.

---

### Post by lance bermudez on 2021-12-23
It is a small file. The program is called weather-util([http://fungi.yuggoth.org/weather/](http://fungi.yuggoth.org/weather/)) on linux. It is written in python. I use this on my linux machines to check the weather. I want to also use this on windows but do not have the admin right to install software. I have gotten permission to use the python that can be download but not installed to the computer it comes in a zip file. The weather-util is a command line program so this works good for the python I have been allowed to use.

---

### Post by The Cog on 2021-12-23
I think you can probably do this without re. Something like this perhaps (not tested)?
```
lines_to_print = 0
with open("/tmp/weathertext5","r") as file:
    for line in file:
        if lines_to_print:
            print(line.strip())
            lines_to_print -= 1
        elif 'Current conditions' in line or 'Temperature:' in line or 'TODAY' in line:
            lines_to_print = 4
```

---

### Post by schragge on 2021-12-26
@**The Cog**. Your code won't print the matched line itself. Here is my attempt:
```
lines_to_print = 0
matches = ['Current conditions', 'Temperature:', 'TODAY']

with open('/tmp/weathertext5', 'r') as file:
    for line in file:
        if any(x in line for x in matches):
            lines_to_print = 4
        if lines_to_print:
            print(line.strip())
            lines_to_print -= 1
```

---

### Post by The Cog on 2021-12-26
@schragge Doh! You're right! Should have searched first and used if, not elif. My bad.

> if any(x in line for x in matches):
I like that.

---


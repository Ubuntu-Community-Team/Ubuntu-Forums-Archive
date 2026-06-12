---
title: "Regular expression for different date formats in Python"
date: 2012-11-26
forum: Programming Talk
---

### Post by crashhold on 2012-11-26
Hello Developers,

I am a beginner in python and need help with writing a regular expression for date and time to be fetched from some html documents. In the following code I am walking through the html files in a folder called event and printing the headings with h1 tag using beautifulsoup. These html pages also contains different formats of date and time. I want to fetch and display this information as well. Different formats of date in these html documents are:

21 - 27 Nov 2012
1 Dec 2012
30 Nov - 2 Dec 2012
26 Nov 2012

Can someone help me out with fetching these formats from these html documents ?
Here is my code for walking through the files and fetching h1 from those html files:


  ```
 
    import re
    import os
    from bs4 import BeautifulSoup
    
    for subdir, dirs, files in os.walk("/home/himanshu/event/"):
        for fle in files:
            path = os.path.join(subdir, fle)    
            soup = BeautifulSoup(open(path))
            
            print (soup.h1.string)
           
            #Date and Time detection

```

---

### Post by slickymaster on 2012-11-26
You don't need a regular expression to do this. There's a python library specifically to parse date-time strings in your required format: the handy [iso8601 module]("http://code.google.com/p/pyiso8601/"). Using this module versus a regular expression also saves you the date-time object conversion step:

```
import iso8601
tx = "2012-02-30T00:59:43"
dtm_obj = iso8601.parse_date(tx)
# returns: datetime.datetime(2012, 3, 2, 0, 59, 43, 
# tzinfo=<iso8601.iso8601.Utc object at 0x1016db150>)
```

But if you absolutely must use a regular expression, here it is.

1 - For the date portion and "T":

```
\d\d[-](0[1-9]|1[012])[-](0[1-9]|[12][0-9]|3[01])T
```

2 - For the time portion:

```
^(2[0-3]|[01]?[0-9]):([0-5]?[0-9]):([0-5]?[0-9])$
```

---

### Post by crashhold on 2012-11-27
Thanks a lot for your help slicky

---

### Post by slickymaster on 2012-11-27
Glad to help. Don't forget to mark the thread as solved.

---


---
title: "store Python output information in Mongodb database"
date: 2012-11-27
forum: Programming Talk
---

### Post by crashhold on 2012-11-27
Hello developers,

I have written this code which walks through the html files in a directory and fetches event and date information and print it on screen. I want this data to be stored in a database. I have installed mongodb and pymongo module. How can I insert the output data into the database. 

```
import re
import os
from bs4 import BeautifulSoup

for subdir, dirs, files in os.walk("/home/himanshu/event/"):
    for fle in files:
        path = os.path.join(subdir, fle)    
        soup = BeautifulSoup(open(path))
        
        #print event title
        print (soup.h1.string)
       
        #Date and Time detection
        s=soup.get_text()
        pat=r'\d{1,2} - \d{1,2} \w{3} \d{4}'
        m=re.search(pat,s)
        if m is None:            
            pat1=r'\d{1,2} \w{3} \d{4}'
            m1=re.search(pat1,s)
            if m1 is None:            
                pat2=r'\d{1,2} \w{3} - \d{1,2} \w{3} \d{4}'
                m2=re.search(pat2,s)
                if m2 is None:
                    pat3=r'\w{3} \d{4}'
                    m3=re.search(pat3,s)
                    if m3 is None:
                        print "No date found"
                        
                    else:
                        m3.group(0)
                        print m3.group(0)
           
                else:
                    m2.group(0)
                    print m2.group(0)
           
            else:
                m1.group(0)
                print m1.group(0)
        else:            
            m.group(0)
            print m.group(0)
```

Output is displayed as follows:
```
event1
date1
event2
date2
event3
date3
event4
date4
and so on...

```

Also is there a way to anyhow store all these regular expressions in an array and call them in a loop instead of using if-else for each and every regular expression.

---


---
title: "last (wtmp) parsing script"
date: 2011-03-01
forum: Programming Talk
---

### Post by pacofvf on 2011-03-01
Hello, I made this script, It counts the ocurrences of the logged users, and gives you how much time a user has been logged in. The output of "last" command is somthing like this:

> 
user1               :13              Tue Mar  1 08:17:08 2011 - down                      (06:21)    
user1  pts/5        :20.0            Tue Mar  1 08:07:09 2011 - Tue Mar  1 08:50:39 2011  (00:43)    
user2  :20                           Tue Mar  1 08:04:50 2011 - Tue Mar  1 08:56:01 2011  (00:51)    
user1               :20              Tue Mar  1 08:04:49 2011 - down                      (06:34)  


and the output of my script is something like this:
> 
Username		Session Time(dd/hh/MM)
user1 		0 : 15 : 8
user2 		0 : 14 : 55


and here is my script:
```

#! /usr/bin/env python
import re
import subprocess
import operator

p = subprocess.Popen('last', shell=True, stdout=subprocess.PIPE, stderr=subprocess.STDOUT)
entries = re.split('\n+', p.stdout.read())
entries = [re.split('\\(|\\)| ', entry) for entry in entries][0:-2]
li = []
for entry in entries: #we keep only the username and the session length
  if len(entry) > 6:
    if len(entry[-5]) > 0:
      li.append([entry[0] , entry[-5]])
    else:
      li.append([entry[0] , entry[-6]])
d = dict() # starts an empty dictionary
for entry in li:#sum all ocurrencies
  t = 0
  tS = re.split('\+',entry[1])#
  u = entry[0]
  if len(tS) > 1:
    t = t + int(tS[0]) * 60 * 24
    tS2 = tS[1]
  else:
    tS2 = tS[0]
  tS = re.split('\:',tS2)
  if len(tS) > 1:
    t = t + int(tS[1]) + int(tS[0])*60
    if u in d:
      d[u]= t+d[u]
    else:
      d[u] = t
sorted_x = sorted(d.iteritems(), key=operator.itemgetter(1), reverse=True)
print 'Username\t\tSession Time(dd/hh/MM)'
for i in sorted_x:
  h=int(i[1]/60)
  m=int(i[1]%60)
  d=int(h/24)
  h=int(h%24)
  print i[0],'\t\t',d,':',h,':',m


```
I'm new to python, I think that this could be coded in a more simple and elegant way. I dare you 
:O

---

### Post by LemursDontExist on 2011-03-02
This might be a little tidier:

```
#! /usr/bin/env python

import os
from datetime import timedelta
from collections import defaultdict

with os.popen("last") as f:
    data = f.read()
    
d = defaultdict(timedelta)
for entry in data.split('\n')[:-2]:
    username = entry.split(' ')[0]
    time_str = entry.split('(')[1].split(')')[0]
    if '+' in time_str:
        days, time_str = time_str.split('+')
        days = int(days)
    else:
        days = 0
    hours, minutes = map(int, time_str.split(":"))
    d[username] += timedelta(days=days, hours=hours, minutes=minutes)

max_len = max(map(len, d.keys()) + [8]) + 2

print "%%-%ssSession Time(dd/hh/MM)" % max_len % "Username"
for username in sorted(d.keys()):
    t = d[username]
    hours, minutes = divmod(t.seconds/60, 60)
    print "%%-%ss%%s:%%s:%%s" % max_len % (username, t.days, hours, minutes)
```

I like to avoid regular expressions where simple string operations will do.  The datetime module saves me the trouble of doing a bunch of arithmetic.  

I actually liked your use of the operator module and the 'key' argument to sorted - it makes the code feel very functional (That code would come out very naturally in, say, Haskell), but I felt that sorting the keys alone is more pythonic.

At the bottom, the funky string formatting is just to make sure the columns line up - in your original code the columns didn't line up right always.  Though, it's worth noting that Python 3 totally eliminates this sort of string formatting, so I wouldn't pay it too much heed - I just haven't gotten around to learning whatever the replacement is.

---

### Post by pacofvf on 2011-03-02
Thanks, I used regex because you can compile them and use it repeatedly, saving a lot of processing capacity and time, but split() doesn't work for compiled objects :S, The datetime module simplifies the time formating and now I see that I should use a dictionary since the beginning, and avoid the part where I use a list and then a dictionary. ;)

---

### Post by LemursDontExist on 2011-03-02
> **pacofvf said:**
> I used regex because you can compile them and use it repeatedly, saving a lot of processing capacity and time

Actually, regexes, even when compiled, involve a lot more overhead than simple string operations.  For complex searches, the overhead pays for itself, but for simple operations, the regex will be much slower.

Try the following:

```
import timeit
t1 = timeit.Timer("regex.split(a)", "import re; a='This is a splitting test'; regex=re.compile(' ')")
t2 = timeit.Timer("a.split(' ')", "a='This is a splitting test'")
t1.repeat()
t2.repeat()
```

The timeit.repeat() function runs the setup code once, and the main code 1000000 times (and repeats this process 3 times).  On my machine the string version takes just a little over half as long as the regex version.  

In any case, I feel that string operations tend to be a lot more readable and maintainable which is a lot more important than speed 95% of the time (knowing when you're in the 5% where it matters is of course a fun trick ;)).

---


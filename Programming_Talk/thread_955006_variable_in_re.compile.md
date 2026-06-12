---
title: "variable in re.compile"
date: 2008-10-21
forum: Programming Talk
---

### Post by thirddeep on 2008-10-21
I have seen this asked a couple of times on the net, and found answers.

My problem is, they don't work ... or I am doing them wrong :-)

The problem is simple, use a variable inside the re.compile :

```

for current_log in CHECK_LOG_LIST:
    LOG = open(current_log, "r")
    for current_ip in IP_LIST:
        expr = re.compile(r'%s' % current_ip)
        for LINE in LOG:
            DATA = expr.search(LINE)
            if DATA:
                print DATA.group()
    LOG.close()

```


Using : expr = re.compile("xxx.xxx.xxx.xxx") does work.

Just for clarity, IP_LIST look like : ['xxx.xxx.xxx.xxx', 'xxx.xxx.xxx.xxx'] (although it is dynamically built and not defined).  Putting a print statement in before the expression, shows that current_ip does have a value xxx.xxx.xxx.xxx.

Where am I going wrong then ?

Thd.

---

### Post by ghostdog74 on 2008-10-21
No need regex. Use the "in" operator
```

if current_ip in LINE:

```

---

### Post by slavik on 2008-10-21
> **ghostdog74 said:**
> No need regex. Use the "in" operator
```

if current_ip in LINE:

```

agreed, sort of ... keep in mind that this way, your program has a O(LINE.length * IP_LIST.length) complexity which can grow very quickly.

---

### Post by ghostdog74 on 2008-10-22
> **slavik said:**
> agreed, sort of ... keep in mind that this way, your program has a O(LINE.length * IP_LIST.length) complexity which can grow very quickly.

i think you should propose your solution to OP on how to reduce those complexities.

---

### Post by thirddeep on 2008-10-22
"if current_ip in LINE:" worked, after I moved the "LOG = open(current_log, "r")" down to the next iteration.

Thank you ghostdog74.

But you are right slavik, this does mean that every log file get opened and read IP * LOG.  I was hoping to open the log file just once, and do a "for line in LOG" for every IP, but I have to re-open it every time.  Like : 

```

for current_log in CHECK_LOG_LIST:
    for current_ip in IP_LIST:
        LOG = open(current_log, "r")
        for LINE in LOG:
            if current_ip in LINE:
                print LINE
        LOG.close()

```

At least it works :-)

Thd.

---

### Post by ghostdog74 on 2008-10-22
> **thirddeep said:**
> "if current_ip in LINE:" worked, after I moved the "LOG = open(current_log, "r")" down to the next iteration.

Thank you ghostdog74.

But you are right slavik, this does mean that every log file get opened and read IP * LOG.  I was hoping to open the log file just once, and do a "for line in LOG" for every IP, but I have to re-open it every time.  Like : 

```

for current_log in CHECK_LOG_LIST:
    for current_ip in IP_LIST:
        LOG = open(current_log, "r")
        for LINE in LOG:
            if current_ip in LINE:
                print LINE
        LOG.close()

```

At least it works :-)

Thd.

in your code, you are opening the log for every ip list. Here's my suggestion if the log files are not too big
```

for current_log in CHECK_LOG_LIST:
  LOG = open(current_log).read()
  for ip in ip_list:
      if ip in LOG:
        .....

```

---

### Post by thirddeep on 2008-10-22
What is the difference between : 

A) LOG = open(current_log).read()
and
B) LOG = open(current_log, "r")

I think the difference is that A reads the entire log file into memory that LOG is pointing to.  Whereas B is only the file pointer.  Correct ?

Although this works, it breaks the goal I am trying to achieve (which, if I said from the start would have saved time ... sorry).

So, the idea is simple.  Build list of IP's from log X.  Search for said list of IP's in log Y, Z, etc.  Output found items, including x_count lines before and after.  My next forum post was going to be, is there any equivalent to GNU grep's -B / -A ?

I am forcing myself to learn Python here.  I could have done this in BASH so quick. But learn I must :-)

At what stage does one decide just to use *NIX utilities (grep/sed/awk) inside the Python script ?

Thd.

---

### Post by ghostdog74 on 2008-10-22
> **thirddeep said:**
> 

I think the difference is that A reads the entire log file into memory that LOG is pointing to.  Whereas B is only the file pointer.  Correct ?

yes.

>  My next forum post was going to be, is there any equivalent to GNU grep's -B / -A ?

of course. depends on how you go about doing it. you can get the whole file into a list, go over the list, and if ip is found, use indexing to get the how many lines before and after
eg
```

data=open("file").readlines()
for i in range(len(data)):
  if ip in data[i]:
      print data[i-5] # 5 lines before.

```


> 
At what stage does one decide just to use *NIX utilities (grep/sed/awk) inside the Python script ?

Thd.
usually you don't. Only when you need to call third party external programs that Python doesn't have wrapper/module for.

---

### Post by thirddeep on 2008-10-22
Thank you again, that clears things up.

If I may, a slight discussion on performance.

As all the log files I am working with are currently below 10MB, loading it all into a list should not be of issue.  However, I would like to extend this idea at some point to log files that are well over 100MB (or multiples thereof).

Surely, would grep not be a lot less resource intensive for large log files ?  Loading a couple hundred MB of file into RAM (the list) just to pull a couple of strings (grep -A 5 -B 5) just does not _sound_ right.

Thd.

---

### Post by ghostdog74 on 2008-10-22
> **thirddeep said:**
> I would like to extend this idea at some point to log files that are well over 100MB (or multiples thereof).

yes it should be fine. other methods for big files would be using memory mapping.
an example of reading next 5 lines.
```

import os,mmap
thefile = open( "file" )
length = os.fstat( thefile.fileno() ).st_size
mapping = mmap.mmap( thefile.fileno(), length, mmap.MAP_PRIVATE, mmap.ACCESS_READ )
pos=mapping.find( "pattern" ) #find where the pattern is
mapping.seek(pos)
print mapping.readline().strip() #of course, you can use a loop here.
print mapping.readline().strip()
print mapping.readline().strip()
print mapping.readline().strip()
print mapping.readline().strip()
mapping.close()

```

Check out more on mmap module from the docs


you can find out for yourself, create a very big file, then insert a pattern to search for at the end of the file for example. 
Then at the command prompt, use the time command to see how fast they run. I believe grep would be still a bit faster than Python :)
(unless you can emulate grep's algorithm and implement it in Python, eg extensions )

---

### Post by thirddeep on 2008-10-22
Well, you will be happy to know that works :-)

Now that -A (after the match) is sorted, I am trying to get -B (before the match) working.

Don't tell me yet how ... I first have to struggle and cuss tonight, then I will bother you tomorrow :-)

Thd.

---


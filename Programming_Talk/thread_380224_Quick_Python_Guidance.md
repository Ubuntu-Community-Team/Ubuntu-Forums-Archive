---
title: "Quick Python Guidance"
date: 2007-03-09
forum: Programming Talk
---

### Post by Spr0k3t on 2007-03-09
I'm trying to learn Python and have not had much luck diving in.  I read through examples and books and just can't pick it up.  So here's a favor to ask of any Python developer out there...

I have a log file that I want to see the last few entries (arg length).  Now I want to take the log and trim the useless information and format specific information in the log.  Here's a sample of the log.

MM:DD:YYYY ##:##:## TaskID:Note-Title-App(Comment)Device

Now, I want it to look like this:

Note: Title - App (Comment) Device

And if I can... like this:

<td>Note</td><td>Title</td><td>App</td><td>Comment</td><td>Device</td></tr><tr>

Suggestions and recomendations please.  Input and output through the terminal is all I need.

---

### Post by WW on 2007-03-09
It would help if you included a few actual sample lines from your log file.  It is not clear (to me, anyway) what parts of your sample format are place holders, and what parts are literal strings.  For example, after ##:##:##, is the text literally "TaskID" (probably not) or a number, or some other code?  If "Note", "Title", "App", etc. are place holders for actual data, will this data ever contain a "-" or parentheses?  (I.e. can the dash and the parentheses be used to separate the line into the appropriate fields?)

---

### Post by pmasiar on 2007-03-09
> **Spr0k3t said:**
> I'm trying to learn Python and have not had much luck diving in.  I read through examples and books and just can't pick it up.  So here's a favor to ask of any Python developer out there...

Do you have programming experience in other languages? Which books did you tried? For beginners, i keep wiki: [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart) - I recommend to start IDLE Python shell and try "Instant Hacking" link. Best free online book for beginners I found is linked from that page too - is on wikibooks.

> I have a log file that I want to see the last few entries (arg length).  Now I want to take the log and trim the useless information and format specific information in the log.  

Looping through all lines, using [string methods](http://docs.python.org/lib/string-methods.html). Ckeck also split. Someone may suggest using regular expressions, but my advice is do it using simpler tools first. :-)

```

for line in open('path/file.name'):
    if line.startswith('a string'):
      # do something
    if line.find('something'):
      # do something else

```

that should get you started :-)

---

### Post by Spr0k3t on 2007-03-09
> **pmasiar said:**
> Do you have programming experience in other languages? Which books did you tried? For beginners, i keep wiki: [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart) - I recommend to start IDLE Python shell and try "Instant Hacking" link. Best free online book for beginners I found is linked from that page too - is on wikibooks.

My experience is mainly in Java/C++/C# with some PHP/SQL/REXX skills (I've done VB as well, but hate it with a passion).  The book I tried but couldn't really get into it as it was so dry... ["How to think like a computer scientist" for Python](http://www.ibiblio.org/obp/thinkCSpy/).  Perhaps it's just too biased to the beginner... I need something that will help me jump in up to my ankles head first.  I don't need a whole chapter or two of "this is what a loop does", I need something more along the lines of "if you did {code} in Java, you can do {code} in Python".  One of my jobs I had, I was required to learn C# over a weekend.

As for looping through all of the lines, I only need to `tail -n {int variable}` to achieve what I'm after.

> **pmasiar said:**
> Looping through all lines, using [string methods](http://docs.python.org/lib/string-methods.html). Ckeck also split. Someone may suggest using regular expressions, but my advice is do it using simpler tools first. :-)

I can use split, but it's not needed... tail would be faster since I know I only need X lines from the bottom of the log.  Thanks for the quick infos... I gotta dig further if I'm going to figure this out.  Oh man, don't get me started on RegEx... all the years of programming and I still haven't figured out a good way to remember the syntax from memory.

---

### Post by dwblas on 2007-03-09
You can read the data into a list and then access any record you want forwards or backwards. ```
##fp = open(filename, 'r')
##data = fp.readlines()   ## data = list of individual records
##fp.close()

## simulate file read
data = []
for j in range( 0, 10 ) :
   data.append( "test " + str(j) )

print data[-1]
print data[0]
print data[-5]
print data[5]
```

---

### Post by Spr0k3t on 2007-03-09
Okay, I got it with the help of jdong on IRC.  Here's the gist of what I wanted to do.

```
f = open("<logfile path>")
output = f.readline()[-1:]
f.close()
print output
```

Now I just need to work on formatting a doing multiple lines

---

### Post by Spr0k3t on 2007-03-09
> **dwblas said:**
> You can read the data into a list and then access any record you want forwards or backwards.

Interesting... I'll make note of this and see if I can incorporate this into the script.  Thanks!

---

### Post by pmasiar on 2007-03-09
> **Spr0k3t said:**
> The book I tried but couldn't really get into it as it was so dry... How to think like a computer scientist" for Python ....  I need something more along the lines of "if you did {code} in Java, you can do {code} in Python". 

Python.org website is full of good info. They even have two beginner's pages: non-programmers (no previous experience), and programmers. This one is yours: [http://wiki.python.org/moin/BeginnersGuide/Programmers](http://wiki.python.org/moin/BeginnersGuide/Programmers)

Guido (Python's "father") wrote short tutorial for programmers [http://docs.python.org/tut/](http://docs.python.org/tut/)  and it is also included in with IDLE. One of the Python's mantras is "batteries included" You will hear it often  :-)

[http://diveintopython.org/](http://diveintopython.org/) is good online book, jumping into Python head-first as you want :-)



> As for looping through all of the lines, I only need to `tail -n {int variable}` to achieve what I'm after.

```

lines = open('filename').readlines() # slurps whole file into list 
tail = lines[-20:] # copies last 20 lines to new list

```




>  Oh man, don't get me started on RegEx... all the years of programming and I still haven't figured out a good way to remember the syntax from memory.

Neither did I. I use split(), startswith(), endswith(), find() string methods for 95% of my needs - and ignore the rest :-)

---

### Post by Spr0k3t on 2007-03-09
pmasiar: that was a perfect resource for what I needed.  I was able to learn what I needed to do and I was able to complete the script.  The biggest stumbling block I had was substring... er I mean slice.

Thanks again for your help!

---

### Post by pmasiar on 2007-03-09
FYI with method chaining, you can extract last 20 lines from a file with one (long, but still readable) command:

```

lines = open('filename').readlines()[-20:] # last 20 lines of a file into list 

```

---


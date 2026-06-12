---
title: "Working with strings in Python"
date: 2007-07-26
forum: Programming Talk
---

### Post by tc101 on 2007-07-26
I am building a little web crawler program to learn Python.  Once I read a line of code, and determine that it has http in it using this code:

line = handle.readline()
if "http://" in line:

I then want to strip out the URL contained in that line. 

I don't want you to show me how to do this.  I need to figure it out myself as part of my learning process.  I understand how to do something like this in VB and just need to learn the commands in Python.
I can't find a list of the string commands in Python, or a tutorial showing me how to use them.  Could someone please point me at some documentation.

---

### Post by [h2o] on 2007-07-26
[http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)

---

### Post by ironfistchamp on 2007-07-26
I found this useful when I was learning about string manipulation.

[http://www.devshed.com/c/a/Python/String-Manipulation/](http://www.devshed.com/c/a/Python/String-Manipulation/)

HTH

Ironfistchamp

---

### Post by smartbei on 2007-07-26
Here is a useful feature in python:

Open up the interpreter. Now, try the following code:
```

dir(<>)

```
And replace the <> with whatever you are looking for methods for. So, to find default string methods, try:
```

dir("")

```
For list methods, try:
```

dir([])

```
etc. Another useful command is help which tells you a methods usage. For example, join is a string method.
```

help("".join) #note - no parentheses

```
gives me its usage and parameter list.

---

### Post by dwblas on 2007-07-26
line.find( "http://" ) will return the start position.  Then check out slice, line[5:10].

---

### Post by tc101 on 2007-07-26
Thanks everybody.  With the pointers you've given me I'm going to dig into this tomorrow.

---

### Post by Note360 on 2007-07-26
did u look at the regexp stuff?

---

### Post by tc101 on 2007-07-27
I got it to work using the code below, but I am sure there are better ways.  How would you do it?

```

while line <> "":                        #Scroll down through the lines of the web page
    line = handle.readline()
    if "http://" in line:                   # If "http:// found in line pass it to function Get_URL
        Get_URL(line)

def Get_URL(line):
    x1 = line.find("http://")             # Find position in line of http://
    word1 = line[x1:]                     # Get all of line to the right of that
    x2 = word1.find('"')                  # Find the quote, which will mark the end of the URL
    word2 = word1[:x2]                # Get just that part of the line
    print "from get_url" ,word2      # This prints out a URL
```

---

### Post by tc101 on 2007-07-27
I got it to work with this code, but I am sure there are better ways.  How would you do it?

```


while line <> "":                        #Scroll down through the lines of the web page
    line = handle.readline()
    if "http://" in line:                   # If "http:// found in line pass it to function Get_URL
        Get_URL(line)

def Get_URL(line):
    x1 = line.find("http://")             # Find position in line of http://
    word1 = line[x1:]                     # Get all of line to the right of that
    x2 = word1.find('"')                  # Find the quote, which will mark the end of the URL
    word2 = word1[:x2]                # Get just that part of the line
    print "from get_url" ,word2      # This prints out a URL

```

---

### Post by tc101 on 2007-07-27
Also, how do you delete a message here?  I accidentally posted twice.

---

### Post by smartbei on 2007-07-28
Some minor nitpicks:
I have never seen the <> comparison before. What does it do?

From my testing, it is much faster to go through a file using:
```
for line in handle:
```
and it saves a line in the code as well.

Something a bit more major is the the find returns -1 if it finds nothing. A slice starting with -1 is valid, (it is the last character of a string), and this would mess up the rest of your code in the function. Therefore, something like:
```

def Get_URL(line):
	x1 = line.find("http://")
	if x1 != -1:
		word1 = line[x1:]
		x2 = word1.find('"')
		if x2 != -1:
			word2 = word1[:x2]
			print "from get_url" ,word2

```
Which could be further simplified (though admittedly losting some of tis error-checking:
```

# just for fun: this is also slightly faster - in the range of 0.3 seconds for a million records on my computer.
def Get_URL1(line):
	word=line[line.find("http://"):line.find('"')]
	if len(word) > 1:pass
		print "from get_url" ,word

```

---

### Post by smartbei on 2007-07-28
Crap I just posted twice as well - Can't delete a message apparently.

---

### Post by tc101 on 2007-07-28
> # just for fun: this is also slightly faster - in the range of 0.3 seconds for a million records on my computer.
def Get_URL1(line):

How do you do time calculations in python with fractions of a second?

---

### Post by pmasiar on 2007-07-28
> **smartbei said:**
> 
I have never seen the <> comparison before. What does it do?

<> is obsolete way to say != or "not x == y". <> will go away in Py3K, so don't get used to it :-)

> From my testing, it is much faster to go through a file using:
```
for line in handle:
```
and it saves a line in the code as well.

Correct, "for line in file:" is preferable idiomatic way (and faster too).

Something a bit more major is the the find returns -1 if it finds nothing. 

index() will raise exception if not found. Don't be afraid of exceptions, they are for your use to handle ... well exceptions :-)

---

### Post by smartbei on 2007-07-28
Thanks for the feedback pmasiar. :)

To time things in python I use the time lbrary:
```

from time import time
t1=time()
#Code to time here
t2=time()
print t2-t1

```

There are probably better/more precise ways to do it, but all I am looking for is usually a relative: which-of-these-implementations-is-faster.

BTW - my mistake: The first implementation is faster (see above). Updated to use the index method as suggested by pmasiar:
```

#Again - just for fun -  this is slower (takes roughly twice as long) as the one using finds.
#Correct exception checking can be expensive :)
def Get_URL(line):
	try:
		x1=line[line.index("http://"):]
		x2=x1[:x1.index('"')]
	except ValueError:
		pass

```

---

### Post by pmasiar on 2007-07-28
> **smartbei said:**
> 
this is slower (takes roughly twice as long) as the one using finds.
#Correct exception checking can be expensive :)


Not so.
1) you did not proved that longer time is caused by exceptions. IMHO it is caused by your complicated logic when creating and destroying strings. Yes, creating unneeded object can be expensive. :-)
2) Python will check for exceptions anyway, regardless if you plan to handle it yourself or let it rip (and because of that, I believe it is optimized)

```

# let's do it simple
def Get_URL(line):
	try:
		start_href = line.index("http://")
		end_href = line.index('"', start + 10)
	except ValueError:
		pass

```
Warning: I never tested that code. Possible bug: code will find only first hyperlink in the line, ignoring all others.

---

### Post by dwblas on 2007-07-29
> How do you do time calculations in python with fractions of a second?datetime will do mico-seconds```
import time, datetime
#!/usr/bin/python

import time, datetime

start_time = datetime.datetime.now()
print "start time =", start_time

time.sleep(1.5)
time_now = datetime.datetime.now()
print "stop time  =", time_now, type(time_now)
diff = time_now - start_time
print "difference =", diff, "\t\t", type(diff)
print "As string  =", str(diff), "\t\t", type(str(diff))
print "Difference - seconds =", diff.seconds, "\t\t", type(diff.seconds)
print "Difference - microseconds =", diff.microseconds, "\t", \
                                     type(diff.microseconds)
print time_now.hour, "\t\t\t\t\t", type(time_now.hour)
print time_now.minute
print time_now.second
print time_now.microsecond
```.

---

### Post by smartbei on 2007-07-30
Note that In both mine and pmasiar's examples above the print statements were removed for timing - the results would have been meaningless since the print statements are by far the slowest operation.

As for your response pmasiar:
```

def Get_URL(line):
	try:
		start_href = line.index("http://")
		end_href = line.index('"', start_href + 10)
		s=line[start_href:end_href]
		#print s
	except ValueError:
		pass

```
You cheat (:D) by not creating the s variable that is needed when printing, which I do create in the form of x2. Once I add it, after a million runs the programs are close - with less than 0.1s difference...after a few times it seems mine is faster, but again, this is negligable :).

Besides, I did prove that using the index methods and exceptions is expensive - It is the same logic used in the function with the find methods, so the logic was always complicated :).

---

### Post by tc101 on 2007-07-31
I have a new string question.  How do I check and make sure a string only has ascii characters?  I am working on my web crawler and sometimes I get data from foreign sites that can be printed out but causes problems when I write it to a text file.

---

### Post by tc101 on 2007-07-31
I tried writing to a file using this unicode syntax

```
rec = unicode(urlline,'ascii') + "\n"
f.write(rec)
```

but as soon as it came to the first foreign characters, it just stopped writting to the file, or at least I can't see the data when I open the file with a text editor.

---

### Post by smartbei on 2007-07-31
There has to be a better way to do it, but perhaps you could use the fact that ord() fails on anything but ascii.

For example:
```

print ord('h')
#= 104
print ord('&#1502;') # hebrew character
#Traceback (most recent call last):
#  File "<stdin>", line 1, in <module>
#TypeError: ord() expected a character, but string of length 2 found

```

So you can use exceptions to filter out the non-ascii characters perhaps. Wait 'till pmasiar sees this though - He is better at this than I am.

---

### Post by tc101 on 2007-07-31
That would work but you would have to loop through the whole string, character by character.  I can write a function to do that, but I feel there must already be some function like 

x=isascii(string)

that just returns true of false to tell you if the whole string is ascii or not

I can't find it though

---

### Post by pmasiar on 2007-07-31
you have only 2 places to look
1) built-in functions: [http://docs.python.org/lib/built-in-funcs.html](http://docs.python.org/lib/built-in-funcs.html)
2) string methods: [http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)

All 2-3 clicks from Library reference (as they said: **(keep this under your pillow)** [http://docs.python.org/lib/lib.html](http://docs.python.org/lib/lib.html)

link 1) has function **all( <iterable> )**, but it is still too much work.

link 2) suggests: 3.6.1 String Methods:
isalpha(  	)
    Return true if all characters in the string are alphabetic and there is at least one character, false otherwise.

And yes, your intuition was right - batteries are included :-)

---


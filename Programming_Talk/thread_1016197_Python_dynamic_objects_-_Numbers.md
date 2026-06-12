---
title: "Python dynamic objects? - Numbers?"
date: 2008-12-19
forum: Programming Talk
---

### Post by jacensolo on 2008-12-19
I'm reading a file that has a type and each type has a result. I want to read the file and check if the type has already been found, and if it has then add the result to it. If not, make the type.

I was hoping to have each type an object. Each type is a number, so how do I dynamically name the object?

Or better yet how do I create objects on the go at all?

Edit: Fixed. New problem. 

The lines I am searching for looks like this:
```
/ReqType=2/ReqResult=0
```
So, my regular expression is this:
```
'/ReqType=(?P<reqtype>\d+)/ReqResult=(?P<reqresult>\d+)'
```
This works fine and dandy, and even seems to do what I want it to do. Then, I realize there is a 22 in the log file that is not showing up. What is wrong with my expression? Why isn't it picking up the 22?

Heck, here's the  whole code (sloppy, mind you):
[php]import re
def newtype(type, result):
	req[type] = {result: 1}
expression = re.compile('/ReqType=(?P<reqtype>\d+)/ReqResult=(?P<reqresult>\d+)')
f = open("Doc2.txt")
req = {'null': 0}
for line in f:
	match = expression.search(line)
	if match:
		current_type = match.group('reqtype')
		current_result = match.group('reqresult')
		if current_type in req.keys():
			if current_result in req[current_type]:
				req[current_type][current_result] += 1
			else:
				req[current_type][current_result] = 1
		else:
			newtype(current_type, current_result)
del req['null']
for key in req.keys():
	for k in req[key]:
		print key, "and", k, "shows up", req[key][k], "times"
print req  #for testing
[/php]

---

### Post by kjohansen on 2008-12-19
if i understand you correctly:

if the types are small consecutive numbers, like 1,2,3... etc then you coul have an array and just increment the array entry for the type you are currently reading.

if the numbers are more arbitrary then you could have a hash table that stores an array index based on the type number.  You could test to see if a type is in the hash table and if it is return the index of the array aligned to it, if not then create a hash entry and create an array element.

---

### Post by jacensolo on 2008-12-19
> **kjohansen said:**
> 

if the numbers are more arbitrary then you could have a hash table that stores an array index based on the type number.  You could test to see if a type is in the hash table and if it is return the index of the array aligned to it, if not then create a hash entry and create an array element.

Great minds think alike. I already did that, but I found out he wants to check to see how many times each result has been paired with each request.

So then I had the idea to use oop, then came this thread.

---

### Post by jacensolo on 2008-12-20
<snip> edited it instead.

---

### Post by slavik on 2008-12-20
what language are you using?

in Perl, you could do something like the following:

```

while ($line = <>) {
  if ($line =~ /ReqType=(\d+)\/ReqResult=(\d+)/) {
    push @{ %data{$1} }, $2;
  }
}

```

You will have a hash of arrays where each key into the data hash is an array of the specific ReqType, and the array holds ReqResult.

Is that what you are looking for?

---

### Post by WW on 2008-12-20
> **jacensolo said:**
> 
Edit: Fixed. New problem. 

The lines I am searching for looks like this:
```
/ReqType=2/ReqResult=0
```
So, my regular expression is this:
```
'/ReqType=(?P<reqtype>\d+)/ReqResult=(?P<reqresult>\d+)'
```
This works fine and dandy, and even seems to do what I want it to do. Then, I realize there is a 22 in the log file that is not showing up. What is wrong with my expression? Why isn't it picking up the 22?

Do you still have the problem?  Your code seemed to work for me:

Doc2.txt:
```

/ReqType=2/ReqResult=0
/ReqType=22/ReqResult=0
/ReqType=2/ReqResult=0
/ReqType=22/ReqResult=0
/ReqType=1/ReqResult=3
/ReqType=1/ReqResult=1
/ReqType=22/ReqResult=9
/ReqType=4/ReqResult=22

```

Run your program:
```

$ python logcount.py 
1 and 1 shows up 1 times
1 and 3 shows up 1 times
2 and 0 shows up 2 times
4 and 22 shows up 1 times
22 and 9 shows up 1 times
22 and 0 shows up 2 times
{'1': {'1': 1, '3': 1}, '2': {'0': 2}, '4': {'22': 1}, '22': {'9': 1, '0': 2}}
$

```

Also, if you are interested, here is a more concise version of your program.  The biggest change is to remove the newtype function, and to remove some of the "if/else" statements, by using the "setdefault" dictionary method.

```

import re

expression = re.compile('/ReqType=(?P<reqtype>\d+)/ReqResult=(?P<reqresult>\d+)')
f = open("Doc2.txt")
req = {}
for line in f:
    match = expression.search(line)
    if match:
        current_type, current_result = match.group('reqtype','reqresult')
        counts = req.setdefault(current_type,{})
        counts[current_result] = counts.setdefault(current_result,0) + 1

for key in req:
    for k in req[key]:
        print key, "and", k, "shows up", req[key][k], "times"
print req  #for testing

```

---

### Post by pmasiar on 2008-12-20
> **slavik said:**
> what language are you using?

According to post title, my guess would be - Python :twisted:

so you are fallible after all... :-)

---

### Post by jacensolo on 2008-12-20
> **WW said:**
> Do you still have the problem?  Your code seemed to work for me:

Doc2.txt:
```

/ReqType=2/ReqResult=0
/ReqType=22/ReqResult=0
/ReqType=2/ReqResult=0
/ReqType=22/ReqResult=0
/ReqType=1/ReqResult=3
/ReqType=1/ReqResult=1
/ReqType=22/ReqResult=9
/ReqType=4/ReqResult=22

```

Run your program:
```

$ python logcount.py 
1 and 1 shows up 1 times
1 and 3 shows up 1 times
2 and 0 shows up 2 times
4 and 22 shows up 1 times
22 and 9 shows up 1 times
22 and 0 shows up 2 times
{'1': {'1': 1, '3': 1}, '2': {'0': 2}, '4': {'22': 1}, '22': {'9': 1, '0': 2}}
$

```

Also, if you are interested, here is a more concise version of your program.  The biggest change is to remove the newtype function, and to remove some of the "if/else" statements, by using the "setdefault" dictionary method.

```

import re

expression = re.compile('/ReqType=(?P<reqtype>\d+)/ReqResult=(?P<reqresult>\d+)')
f = open("Doc2.txt")
req = {}
for line in f:
    match = expression.search(line)
    if match:
        current_type, current_result = match.group('reqtype','reqresult')
        counts = req.setdefault(current_type,{})
        counts[current_result] = counts.setdefault(current_result,0) + 1

for key in req:
    for k in req[key]:
        print key, "and", k, "shows up", req[key][k], "times"
print req  #for testing

```

It's working now. I must have changed something without looking. 
For some reason I didn't think python would let me create an empty dictionary.  Thanks for the more concise version.

---

### Post by slavik on 2008-12-20
> **pmasiar said:**
> According to post title, my guess would be - Python :twisted:

so you are fallible after all... :-)
You're under the assumption that I read titles and remember them when answering .... ;)

---

### Post by jacensolo on 2008-12-20
Now I found out the Unix machines do not have python. Is there a portable python interpreter I can use without installing it?

I don't want to learn perl just for this one task.

---

### Post by pmasiar on 2008-12-20
> **slavik said:**
> You're under the assumption that I read titles and remember them when answering .... ;)

I see: now I know the source of your infallibility: bad memory :twisted:

---

### Post by WW on 2008-12-21
> **jacensolo said:**
> Now I found out the Unix machines do not have python. Is there a portable python interpreter I can use without installing it?

I don't want to learn perl just for this one task.

You could grab the Python source tarball (from [http://www.python.org/download/releases/2.6.1/](http://www.python.org/download/releases/2.6.1/)  for 2.6.1 or from [http://www.python.org/download/releases/2.5.3/](http://www.python.org/download/releases/2.5.3/) for 2.5.3), and compile and install it in your home directory.  I just built 2.6.1 on a Mac laptop running OS X 10.4, and it didn't take too long.  I already have a lot of libraries installed from source; if you don't, you might run into missing dependencies when you try to build python.  You could try it and see what happens.

Once you have the tar file in your home directory, you can build python like this:
```

$ tar xvjf Python-2.6.1.tar.bz2 
$ cd Python-2.6.1
$ ./configure --prefix=$HOME/python

```
The ./configure command will figure out how to build python on your system.  The --prefix option tells ./configure that you want python installed in $HOME/python, instead of the usual default location of /usr/local.

If you don't have the appropriate compiler and libraries already installed, ./configure will probably report the problem(s) to you.  If you don't get any errors, you can build python:
```

$ make
$ make install

```
The make command will take several minutes to finish.  Some warnings occur when you run make; these can probably be ignored.  Also, it might not build all the modules if you don't have the appropriate libraries installed.  For example, on the build that I just completed, there were several modules related to audio that were not built.

If the above commands completed successfully, you now have python installed in $HOME/python.  To use it, change your $PATH variable so your shell sees your new python command (assuming you are using the bash shell):
```

$ export PATH=$HOME/python/bin:$PATH

```
Now try running python:
```

$ python

```

---

### Post by ghostdog74 on 2008-12-21
> **jacensolo said:**
> Now I found out the Unix machines do not have python. Is there a portable python interpreter I can use without installing it?

if you can't download Python, use the shell!!  While i don't really understand what will be your output, here's how you can use "dictionaries" using awk/gawk. they are called associative arrays.
```

awk 'BEGIN{ FS="[/=]" }
{
 print "reqtype: ", $3
 print "req_result: " ,$5
 # to count them, put them into associative arrays
 reqtype[$3]++
 reqresult[$5]++
}END{
  for( i in reqtype) print "reqtype: ", reqtype[i],i
  for( j in reqresult) print "req_result: ", reqresult[j],j 
}' file

```

> 
I don't want to learn perl just for this one task.
somehow you gotta learn something. If you think Perl is too much for you, try learning the shell AT LEAST, especially awk/gawk.

---

### Post by jacensolo on 2008-12-21
> **ghostdog74 said:**
> if you can't download Python, use the shell!!  While i don't really understand what will be your output, here's how you can use "dictionaries" using awk/gawk. they are called associative arrays.
```

awk 'BEGIN{ FS="[/=]" }
{
 print "reqtype: ", $3
 print "req_result: " ,$5
 # to count them, put them into associative arrays
 reqtype[$3]++
 reqresult[$5]++
}END{
  for( i in reqtype) print "reqtype: ", reqtype[i],i
  for( j in reqresult) print "req_result: ", reqresult[j],j 
}' file

```

somehow you gotta learn something. If you think Perl is too much for you, try learning the shell AT LEAST, especially awk/gawk.

It's not that I am too inexperienced to learn something new, I am just bit lazy. I suppose it wouldn't hurt to learn something new. Currently I only know python and a bit of c.


y

---


---
title: "[SOLVED] [Python]Pickling stack underflow"
date: 2008-10-22
forum: Programming Talk
---

### Post by fiddler616 on 2008-10-22
Hello,
I'm working on a simple Python program that will act as an address book. It works beautifully the first time 'round, adding and deleting addresses from dictionary 'main' with gusto, and pickling main into addresses.data.
The problem is the second time I run it--it points to this code block:
[PHP]
import cPickle as p
f = file('addresses.data')
line = f.readline()
if len(line) != 0: #If there's something there
	main = p.load(f) #This is line 13
if len(line) == 0: #If it's completely empty
	main = {}
f.close()[/PHP]
and says:
> Traceback (most recent call last):
  File "abook.py", line 13, in <module>
    main = p.load(f)
cPickle.UnpicklingError: unpickling stack underflow

Google was most unhelpful.

Thanks

---

### Post by Paul Miller on 2008-10-22
Try changing
[php]
f.readline()
[/php]
to
[php]
f.readlines()
[/php]

I suspect you're not reading in the entire string because cPickle is writing a binary string that has embedded newlines.

---

### Post by fiddler616 on 2008-10-23
> **Paul Miller said:**
> Try changing
[php]
f.readline()
[/php]
to
[php]
f.readlines()
[/php]


I suspect you're not reading in the entire string because cPickle is writing a binary string that has embedded newlines.
Yay! A response! :)
Hmm...doesn't work--same error...
Just for fun, I added a 
[PHP]print len(line)[/PHP] 
right after I declare/assign 'line', and I was told that len(line) is 10 (and then there was an error shutoff)...

---

### Post by pmasiar on 2008-10-23
don't read the file by readline, let unpickle do the reading

```

main = p.load(file('addresses.data')) 

```

---

### Post by fiddler616 on 2008-10-23
> **pmasiar said:**
> don't read the file by readline, let unpickle do the reading

```

main = p.load(file('addresses.data')) 

```
Thanks! It works!
Would you mind spelling out *why* it works though--I mean, I understand the coding, I just don't understand why your method is valid and the one I tried isn't--because didn't I already define f as file(addresses.data) ?

Two things are still bugging me though:
One is that if addresses.data doesn't exist, all I can think of to do is:
	[PHP]print "You seem to be running abook for the first time--abook has finished setting up, and will now close."
	print "Restart to run it for real."
	sys.exit()[/PHP]
which does not seem Pythonic. Suggestions?

The other one is that when it prints the dictionary, it looks kind of sloppy, but I can't find a way for it to print:
```

key : value
key2 : value2
key 3 : value3
```
it instead just does
```
{'key3': 'value3', 'key2': 'value2', 'key': 'value'}

```
Thanks again!

---

### Post by pmasiar on 2008-10-23
> **fiddler616 said:**
> Thanks! It works!
Would you mind spelling out *why* it works though--I mean, I understand the coding, I just don't understand why your method is valid and the one I tried isn't--because didn't I already define f as file(addresses.data) ?

yes, but you moved the "read pointer" in f using readline(), so my guess is load did not started from the beginning.

To properly initialize you can ie check if file is present, and if not, create empty dict and pickle it so load() has file to work on. Do not read the pickle yourself.

Another thing you may want to try is sqlite, which is SQL-compatible database without the server (just single-user library).

>  when it prints the dictionary, it looks kind of sloppy, 

you can use pprint module (pretty-print), or just print it yourself:

[php]
for kk in main: # main is unpickled dict
    print kk, ':', main[kk]

# or even sorted:
sorted = main.keys()
sorted.sort() # sorts keys in place
for kk in sorted: # main is unpickled dict
    print kk, ':', main[kk]
[/php]

---

### Post by fiddler616 on 2008-10-23
Thank you--solved!

---

### Post by fiddler616 on 2008-10-24
Finished completely!
[http://python.tmac.andrewmin.com/raw/abook.txt](http://python.tmac.andrewmin.com/raw/abook.txt)

---


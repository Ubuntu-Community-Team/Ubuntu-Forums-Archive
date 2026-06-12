---
title: "Saving Dictionary to Disk in Python"
date: 2007-06-01
forum: Programming Talk
---

### Post by TreeFinger on 2007-06-01
Hello all. I just started learning the Python code a few days ago. I am working on a program right now but I am in need of some help. I have only gone through one tutorial which didn't even talk about controls but just Dictionaries, Tuples and Lists; basic things.

Anyways I want to be able to save information in a few dictionaries to disk and have it loaded each time the program is run. I am trying to understand the Python tutorial on python.org but I haven't read through the entire thing yet. I believe I would need to use the pickle module with the dump() and load() functions but I am not sure if this is true. I am going to try and fool around with them in a little while but I am just looking for a definite answer.

Thank you in advance ;)

---

### Post by pmasiar on 2007-06-01
Yes, pickle is good to save whole objects like that

Another option is anydbm and shelve.

Pickle saves object to a file, shelve saves set of objects, each one (accessible by a key) to a DBM database.

---

### Post by AZzKikR on 2007-06-01
Pickling seems to be a good solution. It reminds me of serialization in Java :) I am learning Python myself  too. It seems it can be done like this in a fairly easy way:

```
import pickle

zoit = { "Crud": "No", "Fsck": "Blox"}
file = open("pickle.pck", "w") # write mode
pickle.dump(zoit, file)

print "Written to disk. Deleting 'zoit' now."
del zoit
file.close()
del file
print "Zoit is now deleted. Reading back from file now:"

file = open("pickle.pck", "r") # read mode
narf = pickle.load(file)
print narf

```

---

### Post by pmasiar on 2007-06-01
> **TreeFinger said:**
> save information in a few dictionaries to disk and have it loaded each time the program is run. 

BTW in one app I wrote I used dict as data structure - one big dict in module, editable by user. I did not bothered with pickling - Python parsed it quickly, and saved compiled version for later use. It was convenient that I did not have to repickle changed dict. I was able to edit the dict, relaod module, and continue with current state of the program (it was simple text adventure game I plan to release for a long time :-) ).

Speed is not a problem until it is a problem - found by code profiler! Don't guess where you have problems: measure!

Premature optimization is road to hell.

---


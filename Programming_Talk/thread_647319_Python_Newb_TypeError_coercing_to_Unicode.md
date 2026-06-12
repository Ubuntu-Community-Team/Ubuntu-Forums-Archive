---
title: "Python Newb: TypeError: coercing to Unicode"
date: 2007-12-22
forum: Programming Talk
---

### Post by PartisanEntity on 2007-12-22
I am trying to teach myself Python. Right now, I have a very simple and primitive script which should take a line of text I enter and append it to a file.

However, after submitting my text I get the following error:

> TypeError: coercing to Unicode: need string or buffer, file found

Am I right in assuming that the string I entered needs to be converted to unicode?

Here is the code I have so far (I am sure it is full of mistakes and redundant code):

```
import sys


# First open the file to read(r)
inp = file("data.txt","r")

workoutlog = []

#Show previous workouts?
print "Do you want to read previous workouts?"
pwanswer = raw_input()

if pwanswer == "yes":
	print "Previous workouts:"

# Read the file into a list then print
# each item
	for line in inp:
    		print line.rstrip()  #only strip right hand end

#Show menu?
print "Do you want to enter new workout data? (yes / no)"
wdanswer = raw_input()

if wdanswer == "yes":
	print """ Enter todays workout data in the form: Date, Workout, Sets, Reps, Weight """
else:
	sys.exit()

workout_data = raw_input()

workoutlog.append(workout_data)

# write data to file
FILE = open(inp,"w")
FILE.writelines(workoutlog)
```

What am I doing wrong?
Thank you.

---

### Post by Bachstelze on 2007-12-22
```
FILE = open(inp,"w")
```

should be :

```
FILE = open("data.txt", "w")
```

open() takes a filename as first argument, not an existing file object.

Also, your script will overwrite the contents of the file with the newly added string instead of appending it, but I'll let you sort that out by yourself ;)

---

### Post by PartisanEntity on 2007-12-22
Thanks very much, I get it now, it's working! :)

---

### Post by PartisanEntity on 2007-12-22
> **HymnToLife said:**
> Also, your script will overwrite the contents of the file with the newly added string instead of appending it, but I'll let you sort that out by yourself ;)

Yes I just realised that hehe

After some research I got it to work with:

```
FILE = open("data.txt", "**a**")
```

But new entries are entered on the same line, where would I add the **"\n"** ?

---

### Post by webdr on 2007-12-22
Logically, I'd say:
Pass a line feed with each new entry:?

But I am new to Python as well, so I am not 100% positive.
-Mark Williams

---

### Post by Bachstelze on 2007-12-22
> **webdr said:**
> Logically, I'd say:
Pass a line feed with each new entry:?


Indeed. A way to do that would be to replace

```
workoutlog.append(workout_data)
```

with

```
workoutlog.append(workout_data+"\n")
```

---

### Post by PartisanEntity on 2007-12-22
> **HymnToLife said:**
> Indeed. A way to do that would be to replace

```
workoutlog.append(workout_data)
```

with

```
workoutlog.append(workout_data+"\n")
```

I fixed it using this:

```
FILE = open("data.txt","a")
FILE.writelines('\n')
FILE.writelines(workoutlog)
```

Earlier I had tried this but if failed obviously:

```
FILE.writelines(workoutlog+"\n")
```

Thanks for the tip, yours is much more elegant :)

---


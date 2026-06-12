---
title: "Python CSV For Loop Noob Question"
date: 2006-05-22
forum: Programming Talk
---

### Post by fsgpr on 2006-05-22
I am new to Python and am trying to do some processing with two CSV files that involves looping through the 2nd file for each line in the 1st file.  My program will loop through the the 2nd file only once (with the below code it would print "In Inner Loop" for each line in the inner file, then it prints "In Outer Loop" for the rest of the lines in the outer file.  What I want is "In Inner Loop" X times, then 1 "In Outer Loop" then "In Inner Loop" X times...

Is there a simple step or logic problem or should the below code run correctly?

I found that if I have the line
```

SecondFileCSV = csv.reader(open(SecondFile, "rb"))

```
right before the inner loop, the program works properly, though it does not seem to be the "right" solution...  

```

FirstFileCSV = csv.reader(open(FirstFile, "rb"))
SecondFileCSV = csv.reader(open(SecondFile, "rb"))

for FirstFileLines in FirstFileCSV:
  for SecondFileLines in SecondFileCSV:
    print "In Inner Loop"
  print "In Outer Loop"

```

---

### Post by unbuntu on 2006-05-22
I have to admit I'm not quite following what the program is supposed to do.  As far as the code is concerned, I don't see any problem.  Maybe you'd like to elaborate more...

---

### Post by jstrube on 2006-05-23
Well, yes, after you have read the file once, you are at the end of the file. csv doesn't automatically rewind.
Either you do what you already found that works, or you rewind manually.
```

FirstFileCSV = csv.reader(open(FirstFile, "rb"))
secondFile = open(SecondFile, "rb")
SecondFileCSV = csv.reader(secondFile)

for FirstFileLines in FirstFileCSV:
  secondFile.seek(0)
  for SecondFileLines in SecondFileCSV:
    print "In Inner Loop"
  print "In Outer Loop"

```

---

### Post by thumper on 2006-05-23
Alternatively, if the file is not too large (less than the memory you have available), you could read the second file into memory, and then loop over that.

It would most likely be quicker than rewinding the file.

---

### Post by fsgpr on 2006-05-23
Thanks to both of you, that explains exactly what I was missing.

---


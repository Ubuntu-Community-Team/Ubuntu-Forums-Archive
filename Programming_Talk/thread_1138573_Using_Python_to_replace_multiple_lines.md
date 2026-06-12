---
title: "Using Python to replace multiple lines?"
date: 2009-04-26
forum: Programming Talk
---

### Post by Hidendra on 2009-04-26
Hi,

I have a Java project that I routinely have to copy sections of code from one source file into another. It'd make it much easier to be able to automate it so I figured Python would do the job?

ie, starting from //start and ending at //end and then copying that block to another //start and //end block in another file.


If you could give me a general push in the right direction that'd be awesome :)


Thank you

---

### Post by Martin Witte on 2009-04-26
I would read each file in a string, and then use rfind and replace, see [the documentation]("http://docs.python.org/library/stdtypes.html#string-methods") on details of those methods

---

### Post by dandaman0061 on 2009-04-26
This may be very coarse and I didn't test it... but I think it should give you some direction...

```

with open('file1.txt', 'r') as f:
    # read entire file into file1
    # ASSUMING 'file1.txt' is relatively small...
    file1 = f.read()

with open('file2.txt', 'r') as f:
    # ASSUMING 'file2.txt' is relatively small...
    file2 = f.read()    # read file into file2

# index() will raise an error if not found...
f1_start = file1.index('//start')
f1_end = file1.index('//end', f1_start)     # look for '//end' after '//start'

f2_start = file2.index('//start')
f2_end = file2.index('//end', f2_start)

# replace file2 lines with proper file1 lines
file2[f2_start:f2_end] = file1[f1_start:f1_end]

with open('file2.txt', 'w') as f:
    f.write(file2)

```

Some notes:
 - the 'with' function is relatively new (2.6+ I believe...) it is shorthand for try: open(), finally: close()
 - I also read the entire files into memory... this may be hazardous if the files are huge, but for programming files, they should be fine.
 - I use the 'index' function to raise an error if the '//start' or '//end' lines aren't found.

---


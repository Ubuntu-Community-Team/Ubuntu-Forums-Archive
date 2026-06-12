---
title: "[Python] Opening Multiple Instances of a File"
date: 2010-07-09
forum: Programming Talk
---

### Post by dodle on 2010-07-09
This isn't really a problem, more of a curiosity.  If I want to open and read a text file multiple times, why do I have to re-open the file each time I read it?  It seems like I would only need to open it once, then I could read it as many times as I wanted until I closed it.

Here is the example code.  When I try to get the second line at a different point in my code it's telling me that the file is empty.  It appears that each time the file is read, the variable used to open the file is cleared to an empty string:
[php]# Opening a Single File

file = open("test.txt", "r") # Open a text file

first_line = file.read().split("\n")[0]
second_line = file.read().split("\n")[1]
last_line = file.read().split("\n")[-1]

print "First Line: %s\nSecond Line: %s\nLast Line: %s" % (first_line, second_line, last_line)

file.close()[/php]

This, on the other hand, does work:
[php]# Opening a Single File Multiple Times

file = open("test.txt", "r") # Open a text file to get first line
first_line = file.read().split("\n")[0]

file = open("test.txt", "r") # Open a text file to get second line
second_line = file.read().split("\n")[1]

file = open("test.txt", "r") # Open a text file to get last line
last_line = file.read().split("\n")[-1]

print "First Line: %s\nSecond Line: %s\nLast Line: %s" % (first_line, second_line, last_line)

file.close()[/php]

Like I said, it's not really a problem.  I just want to understand why Python acts this way.

---

### Post by StephenF on 2010-07-09
```
firstline = file.read**line**()
secondline = file.readline()
thirdline = file.readline()
```
Enough said?

---

### Post by schauerlich on 2010-07-09
read reads the entire file, readline reads until the next newline.

---

### Post by DaithiF on 2010-07-10
Hi,
in addition to what the other posters said about reading lines versus the entire file, you should also be aware of the seek method, for when you do want to go back and read a file a second time without reopening it. 

e.g.
```
fh = open('somefile', 'rb')
x = fh.read()
# go back and re-read it later
fh.seek(0)            # put the file pointer back to the 1st byte of the file
y = fh.read()
fh.close()

```

---

### Post by dodle on 2010-07-10
> **DaithiF said:**
> ```
fh = open('somefile', 'rb')
x = fh.read()
# go back and re-read it later
fh.seek(0)            # put the file pointer back to the 1st byte of the file
y = fh.read()
fh.close()

```

Okay, thanks.  That is what I didn't understand.  I didn't know anything about "file pointers".  I thought the variable was being "emptied" after I read it.

---

### Post by schauerlich on 2010-07-10
> **dodle said:**
> Okay, thanks.  That is what I didn't understand.  I didn't know anything about "file pointers".  I thought the variable was being "emptied" after I read it.

Think of it like there's a cursor in the file. As you read things along, the cursor moves to save your place, but there's no reason you can't move the cursor back to the beginning and read it again.

---


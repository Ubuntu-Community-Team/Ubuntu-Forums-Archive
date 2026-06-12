---
title: "Counter Loop In Python?"
date: 2009-08-25
forum: Programming Talk
---

### Post by maldrich12 on 2009-08-25
A regular old counter would be easy, but I need one that increments by bytes in two particular fields, like so:
file1 has -
1,10   (10 bytes)
11,12  (2 bytes)
13,17  (5 bytes)

Now saying I want to move those fields in file1 to these new fields (same number of bytes, same order) in file2:
11,20
21,22
23,27

Same number of bytes per field, just a different starting position. This is what I have so far:
#!/usr/local/bin/python

import sys
import os
import string
import array

myList = []
myLength = []
newFile = file("newData")
oldFile = file("oldData")

def GetPositions():
  for line in oldFile:
    line = line.strip()
    if line.startswith('Start'):
      elem = line.split(',')[6]
      myList.append(elem)
      startNum = (int(myList[-1].strip()) + 1)
  print "Starting record length is:", startNum

def ReplacePositions():
  for line in newFile:
    counter = 0
    if line.startswith('Start'):
      num1 = int(line[42:45])
      num2 = int(line[46:49])
      bytes = num2 - num1 + 1
      counter += bytes
      print counter

GetPositions()
ReplacePositions()

I was hoping to pass GetPositions to ReplacePositions in order to obtain the position to start incrementing. I'm new to python, sorry.

---

### Post by Arndt on 2009-08-25
> **maldrich12 said:**
> 

I was hoping to pass GetPositions to ReplacePositions in order to obtain the position to start incrementing. I'm new to python, sorry.

Do you know some other language better?

---

### Post by maldrich12 on 2009-08-25
> **Arndt said:**
> Do you know some other language better?

I am new to programming.

---

### Post by Arndt on 2009-08-25
> **maldrich12 said:**
> A regular old counter would be easy, but I need one that increments by bytes in two particular fields, like so:
file1 has -
1,10   (10 bytes)
11,12  (2 bytes)
13,17  (5 bytes)

Now saying I want to move those fields in file1 to these new fields (same number of bytes, same order) in file2:
11,20
21,22
23,27

Same number of bytes per field, just a different starting position. This is what I have so far:
#!/usr/local/bin/python

import sys
import os
import string

myList = []
myLength = []
newFile = file("file1")
oldFile = file("file2")
counter = 0

def GetPositions():
  for line in file1:
    line = line.strip()
    if line.startswith('Start'):
      elem = line.split(',')[6]
      myList.append(elem)
      startNum = (int(myList[-1].strip()) + 1)
  print "Starting record length is:", startNum

def ReplacePositions():
  for line in newFile:
    counter1 = 0
    if line.startswith('Start'):
      num1 = int(line[42:45])
      num2 = int(line[46:49])
      start = 606
      bytes = num2 - num1 + 1
      counter1 += bytes
      print counter1 + bytes

GetPositions()
ReplacePositions()

I was hoping to pass GetPositions to ReplacePositions in order to obtain the position to start incrementing. I'm new to python, sorry.

I think you have never run your code. What's file1, for example? And, if newFile is a new file, how is something going to appear in 'line'?

What are those magic numbers 42-45, 606, etc.?

Looking at your problem description, what should the program do if there is already text in position 11? And if "move" is the right word, not "copy", what is to happen at the original positions?

---

### Post by maldrich12 on 2009-08-25
I edited my original code above. newFile contains data I would like to append to oldFile. I will clarify:
oldFile has block of data such as:

#--------------------------------------------------------------------------
#
#--------------------------------------------------------------------------
Line...............................xxx
Line........................xxx
Line..................................xxx
Start, End, Data Type (C,D,F,N)...........604,605,F
Line.....................N
Line............

I am reading through the lines of oldFile, grabbing the last end position (605), adding 1 and would like to start incrementing the newFile data (same sort of blocks) using the number of bytes (num2 - num1 +1).

So far, I can get the number of bytes to add to each block in newFile. I have not tried to actually replace the positions in newFile yet. I am just looking to get the positions right for now. Like I said, totally new...

---

### Post by Arndt on 2009-08-25
> **maldrich12 said:**
> I edited my original code above. newFile contains data I would like to append to oldFile. I will clarify:
oldFile has block of data such as:

#--------------------------------------------------------------------------
#
#--------------------------------------------------------------------------
Line...............................xxx
Line........................xxx
Line..................................xxx
Start, End, Data Type (C,D,F,N)...........604,605,F
Line.....................N
Line............

I am reading through the lines of oldFile, grabbing the last end position (605), adding 1 and would like to start incrementing the newFile data (same sort of blocks) using the number of bytes (num2 - num1 +1).

So far, I can get the number of bytes to add to each block in newFile. I have not tried to actually replace the positions in newFile yet. I am just looking to get the positions right for now. Like I said, totally new...

To me, that's only a little clearer. Can you give an entire example?

---

### Post by maldrich12 on 2009-08-25
> **Arndt said:**
> To me, that's only a little clearer. Can you give an entire example?

oldFile:
#--------------------------------------------------------------------------
# LAST BLOCK IN OLDFILE
#--------------------------------------------------------------------------
Line...............................xxx
Line........................xxx
Line..................................xxx
Start, End, Data Type (C,D,F,N)...........604,605,F
Line.....................N
Line............

newFile:
#--------------------------------------------------------------------------
# 1ST BLOCK IN NEWFILE
#--------------------------------------------------------------------------
Line...............................xxx
Line........................xxx
Line..................................xxx
Start, End, Data Type (C,D,F,N)...........619,626,F
Line.....................N
Line............

#--------------------------------------------------------------------------
# 2ND BLOCK IN NEWFILE
#--------------------------------------------------------------------------
Line...............................xxx
Line........................xxx
Line..................................xxx
Start, End, Data Type (C,D,F,N)...........627,634,F
Line.....................N
Line............

#--------------------------------------------------------------------------
# 3RD BLOCK IN NEWFILE
#--------------------------------------------------------------------------
Line...............................xxx
Line........................xxx
Line..................................xxx
Start, End, Data Type (C,D,F,N)...........635,642,F
Line.....................N
Line............

(and so on, there are many of these blocks and the field length is never the same). The old data end at poisition 605. I need to concatenate the data blocks in newFile to oldFile, changing the positions accordingly. So the 1st block in newFile needs to start at 606 and end at 613 (8 bytes). The 2nd block start at 614 and end at 621 (8 bytes), etc...

Does that make more sense?

---

### Post by Arndt on 2009-08-25
> **maldrich12 said:**
> oldFile:
#--------------------------------------------------------------------------
# LAST BLOCK IN OLDFILE
#--------------------------------------------------------------------------
Line...............................xxx
Line........................xxx
Line..................................xxx
Start, End, Data Type (C,D,F,N)...........604,605,F
Line.....................N
Line............

newFile:
#--------------------------------------------------------------------------
# 1ST BLOCK IN NEWFILE
#--------------------------------------------------------------------------
Line...............................xxx
Line........................xxx
Line..................................xxx
Start, End, Data Type (C,D,F,N)...........619,626,F
Line.....................N
Line............

#--------------------------------------------------------------------------
# 2ND BLOCK IN NEWFILE
#--------------------------------------------------------------------------
Line...............................xxx
Line........................xxx
Line..................................xxx
Start, End, Data Type (C,D,F,N)...........627,634,F
Line.....................N
Line............

#--------------------------------------------------------------------------
# 3RD BLOCK IN NEWFILE
#--------------------------------------------------------------------------
Line...............................xxx
Line........................xxx
Line..................................xxx
Start, End, Data Type (C,D,F,N)...........635,642,F
Line.....................N
Line............

(and so on, there are many of these blocks and the field length is never the same). The old data end at poisition 605. I need to concatenate the data blocks in newFile to oldFile, changing the positions accordingly. So the 1st block in newFile needs to start at 606 and end at 613 (8 bytes). The 2nd block start at 614 and end at 621 (8 bytes), etc...

Does that make more sense?

So, open oldFile for reading, read until the end, looking for lines starting with "Start", and remember the last position. Then close it and reopen it for appending. Open newFile for reading, and read one line at a time and write to oldFile, except that lines starting with "Start" need to have their positions relocated with an amount that you get by subtracting the positions at the first such line from the remembered end position from oldFile.

---

### Post by maldrich12 on 2009-08-25
> **Arndt said:**
> So, open oldFile for reading, read until the end, looking for lines starting with "Start", and remember the last position. Then close it and reopen it for appending. Open newFile for reading, and read one line at a time and write to oldFile, except that lines starting with "Start" need to have their positions relocated with an amount that you get by subtracting the positions at the first such line from the remembered end position from oldFile.

Exactly. Sorry, I am reading 'Dive Into Python' as much as time allows me to. Am I at least on the right track using functions to get the info I need?

---


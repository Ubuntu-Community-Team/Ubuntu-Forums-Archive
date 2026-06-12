---
title: "to find TAB in the source code using script"
date: 2010-10-08
forum: Programming Talk
---

### Post by Blackbug on 2010-10-08
i need to check for TAB in my .h and .cpp files using script.
can anyone help me on this?
 
i am trying to write a small script in python for this 
 
f=open('kk.txt','r+b')
set=[]
counter=0
for line in f:
counter += 1
for e in line:
if e == '\t':
set.append(counter)
f.close()
print set
tmp = set
tempCount=[]
print tempCount
for count in set:
print "tempCount%s"%tempCount
print "count%s"%count
if tempCount == count:
print "tempCount%s"%tempCount
print "count%s"%count
print "multiple spaces at line%s "%count
else:
print "tab space at line%s "%count
tempCount = count
print counter
 
 
Problem with this is that the set has entry of some lines twice as there are multiple tabs in the same line.
 
I want to count the number of spaces in that line and want to print it along with the line number
 
can anyone help?

---


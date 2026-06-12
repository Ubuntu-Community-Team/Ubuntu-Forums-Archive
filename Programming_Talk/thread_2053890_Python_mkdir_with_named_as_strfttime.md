---
title: "Python mkdir with named as strfttime"
date: 2012-09-06
forum: Programming Talk
---

### Post by jaz0nj4ckal on 2012-09-06
Hello everyone.
I need a little assistance on this matter, or any suggestions.

```
# import the follwoing modulars
import datetime
import sys
import os

# yyyy = date.today()
# + '_' + (datetime.month) + '_' + (datetime.day)
# print "The year is"  + yyyy + "!!!"
now = datetime.datetime.now()

# print current date as yyyy_mm_dd
print "current time is: " + now.strftime("%Y_%m_%d-%H%M")

# os.mkdir(now)
raw_input("Press <enter> to continue:")
```I am trying to generate a folder, which has the current date/time stamp; however, I am doing something wrong.

---

### Post by The Cog on 2012-09-06
os.mkdir needs a string, but you are giving it a datetime.datetime object. Try this:
```
now = datetime.datetime.now()
newDirName = now.strftime("%Y_%m_%d-%H%M")
print "Making directory " + newDirName
os.mkdir(newDirName)
```

---

### Post by jaz0nj4ckal on 2012-09-06
@ The Cog
I am still learning and this is my first program language. In addition, I am still learning the difference between an Object and String. I still have a hard time understanding the difference.

However, I do have Magnus Lie Hetland's Beginning Python from Apress publishing, but I am not not deep into yet - having to go back over items.

Thanks again for the help and suggestions.

---

### Post by jaz0nj4ckal on 2012-09-06
> **The Cog said:**
> os.mkdir needs a string, but you are giving it a datetime.datetime object. Try this:
```
now = datetime.datetime.now()
newDirName = now.strftime("%Y_%m_%d-%H%M")
print "Making directory " + newDirName
os.mkdir(newDirName)
```

Would it be best to convert newDirName to a string? I am just trying to learn, so forgive me if it is a stupid question.

```
print 'making directory' + str(newDirName)
```

---

### Post by ofnuts on 2012-09-06
> **jaz0nj4ckal said:**
> @ The Cog
I am still learning and this is my first program language. In addition, I am still learning the difference between an Object and String. I still have a hard time understanding the difference.

However, I do have Magnus Lie Hetland's Beginning Python from Apress publishing, but I am not not deep into yet - having to go back over items.

Thanks again for the help and suggestions.
A String is an Object, but not all Objects are Strings.

The difficult part is understanding the difference between an Object and its "readable representation".  You can create a Date using a string, but the Date and one of the strings that represent it are to different things with different usages (you cannot add days to a string, but you can add them to a date).

---

### Post by The Cog on 2012-09-07
> **jaz0nj4ckal said:**
> Would it be best to convert newDirName to a string? I am just trying to learn, so forgive me if it is a stupid question.

```
print 'making directory' + str(newDirName)
```
Part of programming involves keeping track of and understanding what type of data each of your variables are. In time, this will become second nature to you. Let's go through what we have here.

First you import the datetime module. datetype is therefore of type module:
```
>>> import datetime
>>> datetime
<module 'datetime' from '/usr/lib/python2.7/lib-dynload/datetime.so'>

```

The datetime module appears to contain an object type also called a datetime, and this type has a now method: 
```
>>> datetime.datetime
<type 'datetime.datetime'>
>>> datetime.datetime.now
<built-in method now of type object at 0x175860>
```
The now method, when called, produces a datetime.datetime object that seems to be set to the current time:
```
>>> now = datetime.datetime.now()
>>> now
datetime.datetime(2012, 9, 7, 9, 16, 52, 105944)
>>> type(now)
<type 'datetime.datetime'>

```
and this datetime.datetime object also has a method called strftime which when called returns a string object:
```
>>> now.strftime
<built-in method strftime of datetime.datetime object at 0xb72df650>
>>> newDirName = now.strftime("%Y_%m_%d-%H%M")
>>> type(newDirName)
<type 'str'>
>>> newDirName
'2012_09_07-0916'
```
so now we know that newDirName is already a string, which is the type that os.mkdir needs, so no conversion is needed.

Hope this helps. Understanding what types things are can be confusing, especially when using libraries that other people have written. But when you can follow this post, you pretty-much have it cracked.

---

### Post by jaz0nj4ckal on 2012-09-07
@[[COLOR=#DD4814]**The Cog**[/COLOR]]("http://ubuntuforums.org/member.php?u=437760")
Thank you for breaking the program down for me. I am still learning, so I sort of coded bash (if there is such a thing) to create something other then the exercises I am doing.

I know the exercises are required to understander the processes of coding - as you pointed out with your example.

I really appreciate that time and description of each line item.

Thank you
-JJ

---


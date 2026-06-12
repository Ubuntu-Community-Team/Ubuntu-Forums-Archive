---
title: "Python - Get a substring from between two characters"
date: 2007-02-03
forum: Programming Talk
---

### Post by ironfistchamp on 2007-02-03
Hey all

I would like to know how I could get s substring from between two characters. For example

```

# my first string
myString = "Hello there !bob@"

#my sub string
subString = #whatever i need to do here to return JUST bob


```

If anyone could help me get this I'd be really happy.

Thanks

Ironfistchamp

---

### Post by phansiizwe on 2007-02-03
```
myString[myString.find("!")+1:myString.find("@")]
```

---

### Post by ironfistchamp on 2007-02-03
Thanks for the reply but this produces the output:

```

  File "subsearch.py", line 2
    myString=[myString.find("!")+1:myString.find("@")]
                                  ^
SyntaxError: invalid syntax

```

Here is the code I used

```

myString="Hello there !bob@"
myString=[myString.find("!")+1:myString.find("@")]
print myString

```

What am I doing wrong?

Thanks

Ironfistchamp

---

### Post by phansiizwe on 2007-02-03
Do it like:

```
myString="Hello there !bob@"
mySubString=myString[myString.find("!")+1:myString.find("@")]
print mySubString
```

the [] are indices to the string myString, e.g. myString[0:5] will return the first 5 characters of your string.

---

### Post by ironfistchamp on 2007-02-03
Awesome thanks so much that is brilliant.

Ironfistchamp

---

### Post by rajohns08 on 2011-02-16
> **phansiizwe said:**
> Do it like:
 
```
myString="Hello there !bob@"
mySubString=myString[myString.find("!")+1:myString.find("@")]
print mySubString
```
 
the [] are indices to the string myString, e.g. myString[0:5] will return the first 5 characters of your string.
 
 
what if im searching a html chat log file and i want to return everything that a single person has said. so i would want to return what is between "nameofperson" and "endoftheirsentence" for everytime it occurs. i know the find function finds the first index of what you search for. but is there a way to use this function to move on to the next index after you have found the first one? so that you can "find next" basically?

---

### Post by wmcbrine on 2011-02-16
You probably should be looking at the "re" module.

---

### Post by kurum! on 2011-02-16
> **wmcbrine said:**
> You probably should be looking at the "re" module.

no need to call a module just to do that.

```

for s in mystring.split("endoftheirsentence"):
   if "nameofperson" in s:
      print s.split("nameofperson")[-1]

```

---

### Post by cariboo on 2011-02-16
This thread is 3 years old, I'd suggest you start a new thread with a link to this one. Closed.

---


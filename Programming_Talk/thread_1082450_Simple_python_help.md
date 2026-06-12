---
title: "Simple python help"
date: 2009-02-27
forum: Programming Talk
---

### Post by easybake on 2009-02-27
I found a script to check my emails when called. I would like it to print "One" instead of "1"

```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="myusernamegoeshere"
password="blahblah"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "0 new"
else:
   print str(fc)+" new"
```

I assume I would have to write some sort of key. If someone could help me start one that would be great.

Could I write it as a bunch of if statements?.. like:

if fc==1:
   print "One"
if fc ==2:
   print "Two"

---

### Post by Can+~ on 2009-02-27
[PHP]numwords = {1:"one", 2:"two", 3:"three", ...}

print numwords[1] #returns "one"[/PHP]

I hope you don't want to create a whole dictionary for every number under the sun.

---

### Post by easybake on 2009-02-27
Perfect! Much thanks.

---


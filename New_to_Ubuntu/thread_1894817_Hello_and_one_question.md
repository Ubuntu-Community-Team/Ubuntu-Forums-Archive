---
title: "Hello and one question"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by Time Traveler on 2011-12-13
Greetings all.  After being away from Unix for many years I just decided to get back into it.  Have to say I am impressed with how far it has come.  Ubuntu is an amazing package.

As I've just arrived on the scene I'm not sure where the best place is to ask this question so I'll put it here for now.

I'd like to automate the following process such that I can start it by clicking on a link or a menu item:

  Start Firefox
  Navigate to a particular web page
  (The web page will open a box asking what to do with a file)
   Select open the file with gedit ('alt - o'  followed by 'enter' will suffice)
  Save the file under 'location/filename' 
  Close Firefox and Gedit

Obviously this needs some kind of a script.  Ideas?

---

### Post by HermanAB on 2011-12-13
The tool you need is called 'expect'.  It is in the repos.

However, it can be done much more easily with wget instead of Firefox.

---

### Post by TeoBigusGeekus on 2011-12-13
+1
```
wget -O /path/to/save/the/file/filename.ext "http://www.address.com/full/download/address/of/the/file/filename.ext"
```

---

### Post by Time Traveler on 2011-12-15
Haha, WGET.  I can see I have to adjust my thinking away from Windows and back to Unix.

That was WAY too simple.  Thank you guys!

'Expected' looks interesting too.  

Regards -

---

### Post by hakermania on 2011-12-15
> **Time Traveler said:**
> Haha, WGET.  I can see I have to adjust my thinking away from Windows and back to Unix.

+1 :)
Welcome back!

---


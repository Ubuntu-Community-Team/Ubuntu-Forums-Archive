---
title: "Firefox unable to play java flash videos"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by professorTHC on 2008-06-05
Well ive set up the java installation i have the shockwave player too, i check it in the firefox plugins tab. but for some reason i still cannot play flash videos, it just shows a white screen with ubuntus version of the hourglass, spinny thing. any ideas? thanks in advance guys:confused:

---

### Post by st33med on 2008-06-05
Flash videos are different from shockwave stuff. Java does not help Flash run.

You need to do this in the terminal:
```
sudo apt-get install flashplugin-nonfree
```
Don't worry about the 'non-free' part. It just means it is proprietary software, not monetary.

---

### Post by malathion on 2008-06-05
st33med's advice should work. If it does, please remember to mark your topic solved!

---

### Post by neurostu on 2008-06-05
if it doesn't then you can try installing:

ubuntu-restricted-extras 
by going to Add/Remove programs - selecting All available software and searching.

---


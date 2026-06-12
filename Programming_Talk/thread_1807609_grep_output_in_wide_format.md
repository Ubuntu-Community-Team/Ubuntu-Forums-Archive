---
title: "grep output in wide format"
date: 2011-07-19
forum: Programming Talk
---

### Post by Blackbug on 2011-07-19
I need output of grep in wide format. Similar to 'ls'.
grep usually gives output in vertical lines, I need in wide format.
 
any suggestions?
 
thanks

---

### Post by dethorpe on 2011-07-19
I'm not quite sure what you mean. Grep outputs match lines and the file they are in with a seperate line for each match.
 
If its to get the file name of the matched files in long format could use xargs:
 
```
grep -l pattern files | xargs ls -l
```
 
If you want to join all the match lines into one then would need to redirect to a script to do that (e.g. something in sed, awk or perl). 
 
If need the filename in long listing format and the matched line then don't use -l option in grep and use script to split filename and matched text parts, then use ls -l on filename to get its long listing.
 
If you can post more details of what you are after may be able to help more.

---


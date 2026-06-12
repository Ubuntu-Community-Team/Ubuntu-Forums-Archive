---
title: "evaluate the last character of every line to see if its numeric"
date: 2014-02-21
forum: Programming Talk
---

### Post by peter_brickles on 2014-02-21
I have a long list of urls in a text file which i need to thin out 

I need to keep only the lines where the urls end with a numeric character 

is there any way to accomplist this iwth grep or awk or any other cli tool 

any help would be appreciated 

Pete

---

### Post by The Cog on 2014-02-21
```
grep '[0-9]$' longlist > shortlist
```
should do the trick, reading the file longlist and writing a new file called shortlist.

Edit:
Or an in-place edit using sed if you dare:
```
sed -n -i '/[0-9]$/p' filename
```

---


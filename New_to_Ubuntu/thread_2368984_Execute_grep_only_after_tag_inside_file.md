---
title: "Execute grep only after tag inside file"
date: 2017-08-17
forum: New to Ubuntu
---

### Post by sed_faster on 2017-08-17
Hello folks,

I need to grep inside the file sh but this grep only can affect the lines after the determine tag. For example, I have this text on file .sh:
```

code
code
code
code
code
code
code

##tag
fgdssdsdgsd
dsf
dfg

dsf
dsfgdf
ds
fgsd

```

I need execute grep on this file but I find the way to  execute grep only after tag "##tag". This is possible?
Thanks

---

### Post by TheFu on 2017-08-17
Yes.
Many different ways.  Find the line number with the tag, pass that into tail as the starting line, then use sed.

Or use a real programming language like python, perl, ruby and do whatever you need.

Based on all your other questions here, you really should just switch to python, ruby or perl for this stuff.  They can easily handle any sort of text processing required - with perl being the most capable and fastest - faster than the bash script that is forced to spaw 3 other processes to do the work.

---


---
title: "SHELL Scriptin help needed"
date: 2007-06-06
forum: Programming Talk
---

### Post by gham on 2007-06-06
I'm a complete beginer with Shell Scripting 

How can I use the output of "wc -l" in an arithmatic calculation ?

thanks in advance for any help

---

### Post by bashologist on 2007-06-06
This seems to work:
```
filename="file.txt"
str="$(wc -l $filename)"
echo $((${str%% *} + 1))
```
Edit: Or you could use cut, which might look nicer:
```
filename="file.txt"
str="$(wc -l $filename | cut -d " " -f 1)"
echo $((str + 1))
```

---

### Post by gham on 2007-06-06
Thanks for the help :)

---

### Post by ghostdog74 on 2007-06-06
```

awk 'END{print "Number of lines " NR; print "count plus 1 is " NR+1}' file

```

---


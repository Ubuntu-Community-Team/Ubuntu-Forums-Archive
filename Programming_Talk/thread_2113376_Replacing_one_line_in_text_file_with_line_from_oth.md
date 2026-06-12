---
title: "Replacing one line in text file with line from other file"
date: 2013-02-07
forum: Programming Talk
---

### Post by abraxas334 on 2013-02-07
I have a question regarding replacing line in files.
I want to replace the ith line of replace.dat with the jth line of othertext.dat how can i achieve this?

---

### Post by Vaphell on 2013-02-07
```
i=2; j=2
sed "${i}s/.*/$( sed -n ${j}p overtext.txt)/" replace.dat
```

you can plug numbers directly in ${i} and ${j}'s place
by default sed prints to screen, if you want to save the changes either redirect output to new file with **> output.file** (non-destructive=safer) or with **-i** parameter given to main *sed* command (overwrites source file, so better be sure it works first)

---

### Post by ofnuts on 2013-02-07
```

head -$((i-1)) replace.dat > out.dat
head -$j othertext.dat | tail -1 >>out.dat
tail -n +$((i+1)) replace.dat >>out.dat

```

---

### Post by abraxas334 on 2013-02-08
Thanks for all the replies! This helped alot!

---


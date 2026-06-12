---
title: "A script to delete even-numbered columns?"
date: 2007-10-11
forum: Programming Talk
---

### Post by luca.b on 2007-10-11
Hello.
I have a large tab-delimited file and I would like to delete all the even-numbered fields (columns) because they contain redundant information. Is there a way to do so using shell scripting? I've thought about awk, but my knowledge is not that mcuh.

Thanks a lot!

---

### Post by Horsman on 2007-10-11
in python:
```

f = open("filename")
lines = f.split("\n")

for x in lines:
    thisline = x.split("\t") # you might need to replace split("\t") with split() depending on if there are tabs between every field.
    for y in range(1,len(thisline),2):
        print thisline[y] + "\t"
    print "\n"

```

I'm sure someone here knows a better way to format output in columns (I wouldnt mind a quick example either).

---

### Post by ghostdog74 on 2007-10-11
```

awk '
{
   for(i=1;i<=NF;i=i+2){
	  printf $i" "
   }
   print ""
}

' "file"

```

in python:

```

for line in open("file"):
    line=line.split()
    print '\t'.join(line[0::2])

```

---

### Post by luca.b on 2007-10-13
Wow, very lean. I ended up using python but with somewhat longer code (using the csv module). 
I had completely forgot about stepping with slices. Guess I'll go fix my code... Thanks a lot!

---


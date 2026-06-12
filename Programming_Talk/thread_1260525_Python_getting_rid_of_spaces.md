---
title: "Python: getting rid of spaces"
date: 2009-09-07
forum: Programming Talk
---

### Post by filifunk on 2009-09-07
```


8 : L = open('gdprank.csv').read()

30:
for line in L.splitlines():
    clear_line = [word.strip() for word in line.split()]
    print " ".join(clear_line)


```

This code gets rid of some spaces in a file.  But it doesn't actually change the file.  When I put in "print L" I still get the old file with a lot of spaces.  How do I atleast save the new file without the spaces?

thanks!

---

### Post by DaithiF on 2009-09-07
you never write out to the file, you are only changing the data in memory.

something like (untested)
```
linesin = open('gdprank.csv').readlines()
fileout = open('gdprank.csv', 'w')

for line in linesin:
    clear_line = [word.strip() for word in line.split()]
    fileout.write(" ".join(clear_line) + '\n')
fileout.close()
```

---

### Post by DaithiF on 2009-09-08
just a thought -- is this a part of a larger program, or is the only purpose of this script to remove extra spaces from a file?  if the latter, then an easier way to do it (without needing a scripting language) would be to use tr
```
tr -s ' ' < gdprank.csv > gdprank.new && mv gdprank.{new,csv}

```
the -s parameter to tr squeezes out repeat occurences of a character.

---


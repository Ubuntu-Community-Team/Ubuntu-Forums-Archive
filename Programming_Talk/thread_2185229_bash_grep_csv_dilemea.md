---
title: "bash grep csv dilemea"
date: 2013-11-01
forum: Programming Talk
---

### Post by peter_brickles on 2013-11-01
Hi guys / Gals 

i have a csv file as below and i would like to use a linux command grep/awk ??? to add a comma before the date so it give me another column in the csv 

[HTML]
daryl 1985,09:00,11:05,Movie Mix
a town-called-panic-2009,11:00,12:30,Film4
the-hunchback-of-notre-dame-1982,11:05,13:10,Movie Mix
the-truman-show-1998,11:25,13:25,More4
carry-on-up-the-khyber-1968,12:30,14:15,Film4
the-quiet-man-1952,12:35,15:10,Channel 4
to-walk-with-lions-1999,13:10,15:15,Movie Mix
double-wedding-2010,13:15,15:00,Five USA
the-simpsons-movie-2007,14:15,16:00,Film4
far-from-home-the-adventures-of-yellow-dog-1994,15:15,17:00,Movie Mix

[/HTML]


so the first and every other line should read 

daryl ,1985,09:00,11:05,Movie Mix

any help would be appreciated

---

### Post by steeldriver on 2013-11-01
What exactly is the format? Your first line shows a space between the title and the four digit year field, whereas the rest have a hyphen separator

You could do something like

```
$ sed -r 's/(.)([0-9]{4}),([0-9]{2}:[0-9]{2}),([0-9]{2}:[0-9]{2})/,\2,\3,\4/' *yourfile*
```

which matches any single character (separator) followed by yyyy,hh:mm,hh:mm and replaces the first single character with a comma

```

$ sed -r 's/(.)([0-9]{4}),([0-9]{2}:[0-9]{2}),([0-9]{2}:[0-9]{2})/,\2,\3,\4/' movies.csv
daryl,1985,09:00,11:05,Movie Mix
a town-called-panic,2009,11:00,12:30,Film4
the-hunchback-of-notre-dame,1982,11:05,13:10,Movie Mix
the-truman-show,1998,11:25,13:25,More4
carry-on-up-the-khyber,1968,12:30,14:15,Film4
the-quiet-man,1952,12:35,15:10,Channel 4
to-walk-with-lions,1999,13:10,15:15,Movie Mix
double-wedding,2010,13:15,15:00,Five USA
the-simpsons-movie,2007,14:15,16:00,Film4
far-from-home-the-adventures-of-yellow-dog,1994,15:15,17:00,Movie Mix

```

---

### Post by peter_brickles on 2013-11-01
thanks that worked a treat just what i needed ! :-)

---

### Post by drmrgd on 2013-11-02
That will also match the perl regular expression:

```

perl -pe 's/^(.*\w+[- ])+(\d{4}.*)$/$1,$2/g' csv.txt

```

Not sure if it's the best expression, but this was a nice bit for me to practice on!

---

### Post by vasa1 on 2013-11-03
I came up with:
```
sed -r 's/( |-)([0-9]{4})/,\2/' movies.csv
```

```
[11:20 AM] ~/Desktop $ sed -r 's/( |-)([0-9]{4})/,\2/' movies.csv
daryl,1985,09:00,11:05,Movie Mix
a town-called-panic,2009,11:00,12:30,Film4
the-hunchback-of-notre-dame,1982,11:05,13:10,Movie Mix
the-truman-show,1998,11:25,13:25,More4
carry-on-up-the-khyber,1968,12:30,14:15,Film4
the-quiet-man,1952,12:35,15:10,Channel 4
to-walk-with-lions,1999,13:10,15:15,Movie Mix
double-wedding,2010,13:15,15:00,Five USA
the-simpsons-movie,2007,14:15,16:00,Film4
far-from-home-the-adventures-of-yellow-dog,1994,15:15,17:00,Movie Mix
[11:21 AM] ~/Desktop $ 

```

---

### Post by steeldriver on 2013-11-03
^^^ that's fine, only reason I added more groups (to make the match more specific)

```
,([0-9]{2}:[0-9]{2}),([0-9]{2}:[0-9]{2})
```

was in case there are movie *titles* that have 'yyyy' years in them

---

### Post by vasa1 on 2013-11-03
> **steeldriver said:**
> ...
was in case there are movie *titles* that have 'yyyy' years in them
But won't that be needed only if we do 's/find/replace/**g**'? Otherwise, won't just the leftmost find/replace on each line be done?

---

### Post by steeldriver on 2013-11-03
> **vasa1 said:**
> But won't that be needed only if we do 's/find/replace/**g**'? Otherwise, won't just the leftmost find/replace on each line be done?

the movie title *is* the leftmost field ;)

---

### Post by vasa1 on 2013-11-03
> **steeldriver said:**
> the movie title *is* the leftmost field ;)
True!

---

### Post by vasa1 on 2013-11-03
How about```
sed -r 's/( |-)([0-9]{4},)/,\2/' movies.csv
```
It works on this:
```
daryl 1985,09:00,11:05,Movie Mix
a town-called-panic-2009,11:00,12:30,Film4
the-1954 appearance of the hunchback-of-notre-dame-1982,11:05,13:10,Movie Mix
the-truman-show-1998,11:25,13:25,More4
carry-on-to-2014-1968,12:30,14:15,Film4
the-quiet-man-1952,12:35,15:10,Channel 4
to-walk-with-lions-1999,13:10,15:15,Movie Mix
double-wedding-2010,13:15,15:00,Five USA
the-simpsons-movie-2007,14:15,16:00,Film4
far-from-home-the-adventures-of-yellow-dog-1994,15:15,17:00,Movie Mix

```in which the 3rd and fifth lines have the year in the title. It assumes that the titles won't have a comma in them.

---


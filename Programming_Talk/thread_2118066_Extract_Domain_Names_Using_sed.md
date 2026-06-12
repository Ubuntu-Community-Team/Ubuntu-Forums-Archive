---
title: "Extract Domain Names Using sed"
date: 2013-02-20
forum: Programming Talk
---

### Post by _user on 2013-02-20
I have several large text files with around a million domain names.  I want to create a new text file with only the unique domain names in.

What I've got so far:

```
sed -nr "s|(http://)?(www\.)?([^.]*)\.(.*\.?)*|\3|p" filename
```

Test case:
```
google.com.tk/1/2/3/
www.google.co.uk.se
google.co.au
www.google.co.uk.se/1/2/
m.google.com
http://www.google.com/au

```

Above command produces:

> google
google
google
google
m
google


I want it to produce:

> google.com.tk
google.co.uk.se
google.co.au
google.co.uk.se
m.google.com
google.com


---

### Post by ofnuts on 2013-02-20
```

sed -nr "s|(http://)?(www\.)?([^/]+).*|\3|p" filename

```

---

### Post by steeldriver on 2013-02-20
Sounds like you just want to remove any http[s]:// prefix and any /path suffix? so something like this might be simpler:

```
$ sed -e 's|^[^/]*//||' -e 's|/.*$||' domains 
google.com.tk
www.google.co.uk.se
google.co.au
www.google.co.uk.se
m.google.com
www.google.com

```or even with bash

```
$ while read -r url; do noprefix=${url#*//}; nosuffix=${noprefix%%/*}; echo "$nosuffix"; done < domains
google.com.tk
www.google.co.uk.se
google.co.au
www.google.co.uk.se
m.google.com
www.google.com

```FWIW php has some nice url parsing functions which are likely more robust

EDIT: oops forgot the www portion

```

$ sed -e 's|^[^/]*//||' **-e 's|^www\.||'** -e 's|/.*$||' domains 
google.com.tk
google.co.uk.se
google.co.au
google.co.uk.se
m.google.com
google.com

```

---

### Post by _user on 2013-02-20
Thanks that worked.

---

### Post by The Cog on 2013-02-20
Another solution:
```
sed -e 's|^http://||' -e 's|^www\.||' -e 's|/.*||' filename | sort | uniq
```
Edit: Improved sorting
```
sed -e 's|^http://||' -e 's|^www\.||' -e 's|/.*||' filename | LC_ALL=C sort -u
```

---


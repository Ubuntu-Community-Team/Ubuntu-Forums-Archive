---
title: "[python] regular expressions help needed"
date: 2008-10-04
forum: Programming Talk
---

### Post by days_of_ruin on 2008-10-04
How would I go about getting finding all the groups of alphabetical chunks
in a string?So in "the234Legend/2@#$OfZELDA"
I would want to get "the" "Legend" "OfZELDA".

---

### Post by slavik on 2008-10-04
pardon my perl:
```

#!/usr/bin/perl
use strict;
use warnings;

my $string = 'the234Legend/2@#$OfZELDA'; #string to look in
my $regex = "([a-zA-Z]+)"; #the regular expression
my @matches = (); #the matched words
@matches = $string =~ m/$regex/gisx;

print $_."\n" foreach (@matches);

```

---

### Post by unutbu on 2008-10-04
[PHP]#!/usr/bin/env python
import re
astr='the234Legend/2@#$OfZELDA'
alist=re.split('[^a-zA-Z]+',astr)
print alist

# Output:
# ['the', 'Legend', 'OfZELDA'][/PHP]

---

### Post by imdano on 2008-10-04
```
#!/usr/bin/python
import re
matches = re.findall("([a-zA-Z]+)", "the234Legend/2@#$OfZELDA")
for match in matches:
    print match
```

edit: too slow

---

### Post by ghostdog74 on 2008-10-04
> **days_of_ruin said:**
> How would I go about getting finding all the groups of alphabetical chunks
in a string?So in "the234Legend/2@#$OfZELDA"
I would want to get "the" "Legend" "OfZELDA".
the basic logic that comes to mind, is to go through every character and remove those not of the alphabets. Going with this basic logic, you can easily write your code, without regex.

```

>>> s="the234Legend/2@#$OfZELDA"
>>> for ch in s:
...  if ch in string.letters:
...   sys.stdout.write(ch)
...  else:
...   print " ",
...
the     Legend         OfZELDA

```

---

### Post by slavik on 2008-10-04
> **ghostdog74 said:**
> the basic logic that comes to mind, is to go through every character and remove those not of the alphabets. Going with this basic logic, you can easily write your code, without regex.

```

>>> s="the234Legend/2@#$OfZELDA"
>>> for ch in s:
...  if ch in string.letters:
...   sys.stdout.write(ch)
...  else:
...   print " ",
...
the     Legend         OfZELDA

```
there's a problem with this approach ... what if you want to use said words? like to count them or some such ...

---

### Post by y-lee on 2008-10-04
> **slavik said:**
> there's a problem with this approach ... what if you want to use said words? like to count them or some such ...

Hmm well then ya do this:

```
import string
s="the234Legend/2@#$OfZELDA"
L = reduce(str.__add__,[ch*(ch in string.letters) or " " for ch in s ]).split()
print L
```

Which yields
```

['the', 'Legend', 'OfZELDA']
```

Well on second thoughts hopefully you wouldn't do that and instead you would stick with the regex solution above :D

---

### Post by slavik on 2008-10-04
> **y-lee said:**
> 
```
import string
s="the234Legend/2@#$OfZELDA"
L = reduce(str.__add__,[ch*(ch in string.letters) or " " for ch in s ]).split()
print L
```


Who said that Python was readable? ;)

---

### Post by ghostdog74 on 2008-10-04
> **slavik said:**
> there's a problem with this approach ... what if you want to use said words? like to count them or some such ...
do you think its impossible to solve? :) its only limited by the coder and his understanding of the tools he use.

---


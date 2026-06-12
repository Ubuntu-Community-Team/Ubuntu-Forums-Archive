---
title: "Deleting lines from a text file"
date: 2010-04-09
forum: Programming Talk
---

### Post by jamefarm on 2010-04-09
Hello, I have several text files that I need to clean up.  Here's a few sample lines from the file.

```

HIGHLIGHTS	WEBCASTS	CONFERENCES	SPLITS	IPOs	ECONOMIC EVENTS
SYMBOL	COMPANY	EPS ESTIMATE	EPS ACTUAL	PREV. YEAR ACTUAL	Date/Time (ET)
BAC	Bank of America Corporation	0.09	0.00	0.44	20100416
EVBS	Eastern Virginia Bankshares	0.12	0.00	0.10	20100416
FHN	First Horizon National Corporation	-0.16	0.00	-0.37	20100416
GCI	Gannett	0.41	0.00	0.25	20100416
GE	General Electric	0.16	0.00	0.26	20100416
SYMBOL	COMPANY	EPS ESTIMATE	EPS ACTUAL	PREV. YEAR ACTUAL	Date/Time (ET)
CDL	Taurex Resources plc	0.00	0.00	0.00	20100416- 20100416
CDL	Taurex Resources plc	0.00	0.00	0.00	20100416- 20100416
ACU	Acme United	0.06	0.00	0.01	20100416- 20100416

```

What I need to do is delete the lines that begin with HIGHLIGHTS and SYMBOL (lines 1, 2, and 8 in the example)

I also need to delete all lines after the second instance of SYMBOL etc, such as lines 9, 10, and 11.  These lines end with "<date>- <date>"

Any ideas?

---

### Post by gmargo on 2010-04-09
:P Here's a super simple perl [filter]("http://en.wikipedia.org/wiki/Filter_%28Unix%29").
```

#!/usr/bin/perl -w
use strict;
use warnings;

while (<>)
{
    next if /^HIGHLIGHTS/
         || /^SYMBOL/
         || /\s\d{8}\s*-\s*\d{8}\s*\z/s;
    print;
}

```

---

### Post by diesch on 2010-04-09
Using *egrep* is shorter here:
```
egrep -v '(^HIGHLIGHTS|^SYMBOL)|([0-9]+- [0-9]+$)'
```

---

### Post by drvista on 2010-04-09
sed /HIGHLIGHTS/d textfile.txt

---

### Post by Trumpen on 2010-04-09
Here is a fourth way involving awk:

```
awk '/SYMBOL/{x++} x<2 && !/^(HIGHLIGHTS|SYMBOL)/' file
```

---


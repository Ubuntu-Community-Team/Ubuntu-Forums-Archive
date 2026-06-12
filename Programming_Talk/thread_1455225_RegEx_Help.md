---
title: "RegEx Help"
date: 2010-04-15
forum: Programming Talk
---

### Post by jamefarm on 2010-04-15
Hello, I have several text files that I need to clean up. Here's a few sample lines from the file.

```

BAC	Bank of America Corporation	0.09	0.00	0.44	20100416
EVBS	Eastern Virginia Bankshares	0.12	0.00	0.10	20100416
FHN	First Horizon National Corporation	-0.16	0.00	-0.37	20100416
GCI	Gannett	0.41	0.00	0.25	20100416
GE	General Electric	0.16	0.00	0.26	20100416
CDL	Taurex Resources plc	0.00	0.00	0.00	20100416- 20100416
CDL	Taurex Resources plc	0.00	0.00	0.00	20100416- 20100416
ACU	Acme United	0.06	0.00	0.01	20100416- 20100416

```

What I need to do is delete the second date on all lines that have them, such as lines 6, 7, and 8. These lines end with "<date>- <date>" and I need to remove the dash, space, and the second date.
Here's what the output should look like:
```

BAC	Bank of America Corporation	0.09	0.00	0.44	20100416
EVBS	Eastern Virginia Bankshares	0.12	0.00	0.10	20100416
FHN	First Horizon National Corporation	-0.16	0.00	-0.37	20100416
GCI	Gannett	0.41	0.00	0.25	20100416
GE	General Electric	0.16	0.00	0.26	20100416
CDL	Taurex Resources plc	0.00	0.00	0.00	20100416
CDL	Taurex Resources plc	0.00	0.00	0.00	20100416
ACU	Acme United	0.06	0.00	0.01	20100416

```



Any ideas?

---

### Post by MindSz on 2010-04-15
I'd use getline() and parse it like a C-style string. That way you can do whatever you want with the individual characters(e.g. if you find the "- " (dash-space) combination, then erase all remaining characters).

---

### Post by MadCow108 on 2010-04-15
cat file.txt | sed -e "s/\- [0-9]\{8\}$//"

---

### Post by Bachstelze on 2010-04-15
> **MadCow108 said:**
> cat file.txt | sed -e "s/\- [0-9]\{8\}$//**g**"

We want to remove all of them. ;)

---

### Post by MadCow108 on 2010-04-15
sed is a line based tool and according to op there is only one date at the end so the g should not be necessary (it wouldn't make much sense with the at line end operator $ anyway)

---

### Post by jamefarm on 2010-04-15
Thanks a bunch MadCow108, it worked like a charm!

---


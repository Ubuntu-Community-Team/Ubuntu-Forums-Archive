---
title: "sed / awk:  how to delete lines that DON'T match a pattern?"
date: 2010-07-22
forum: Programming Talk
---

### Post by negativ on 2010-07-22
I have a file that looks like this:

```
192.168.10.123 blah blah text
192.168.10.123
192.168.10.10 more text
192.168.10.10
192.168.10.12
192.168.10.9 yet more text
```

How can I delete the lines that are only IP addresses, and leave the lines that are IPs with the text after them?

---

### Post by trent.josephsen on 2010-07-22
> **negativ said:**
> I have a file that looks like this:

```
192.168.10.123 blah blah text
192.168.10.123
192.168.10.10 more text
192.168.10.10
192.168.10.12
192.168.10.9 yet more text
```

How can I delete the lines that are only IP addresses, and leave the lines that are IPs with the text after them?

```
$ grep -v '^[\.[:digit:]]*$' <myfile
```

That matches all lines that contain nothing but a string of dots and digits.  Might not be 100 percent effective.  For that matter, you could

```
$ grep ' ' <myfile
```

which would pick out only lines with no spaces in them (the -v flag inverts the test).

---

### Post by DaithiF on 2010-07-22
Hi,
just to show some sed equivalents:

print lines that don't match a pattern, or delete lines that do ... both achieving the same result

```
$ sed -n '/[0-9]$/!p' testfile
192.168.10.123 blah blah text
192.168.10.10 more text
192.168.10.9 yet more text

$ sed '/[0-9]$/d' testfile
192.168.10.123 blah blah text
192.168.10.10 more text
192.168.10.9 yet more text

```

---

### Post by ghostdog74 on 2010-07-23
> **negativ said:**
> I have a file that looks like this:

```
192.168.10.123 blah blah text
192.168.10.123
192.168.10.10 more text
192.168.10.10
192.168.10.12
192.168.10.9 yet more text
```

How can I delete the lines that are only IP addresses, and leave the lines that are IPs with the text after them?

```

$ grep -P -v '^\d{1,3}.\d{1,3}.\d{1,3}.\d{1,3}$' file
192.168.10.123 blah blah text
192.168.10.10 more text
192.168.10.9 yet more text


```

---

### Post by ghostdog74 on 2010-07-23
> **DaithiF said:**
> Hi,
just to show some sed equivalents:

print lines that don't match a pattern, or delete lines that do ... both achieving the same result

```
$ sed -n '/[0-9]$/!p' testfile
192.168.10.123 blah blah text
192.168.10.10 more text
192.168.10.9 yet more text

$ sed '/[0-9]$/d' testfile
192.168.10.123 blah blah text
192.168.10.10 more text
192.168.10.9 yet more text

```


that is, provided OP's data always have an IP address as its first field.

---


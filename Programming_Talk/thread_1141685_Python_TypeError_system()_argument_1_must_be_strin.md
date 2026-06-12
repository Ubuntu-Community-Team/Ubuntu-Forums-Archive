---
title: "Python: TypeError: system() argument 1 must be string without null bytes, not str"
date: 2009-04-28
forum: Programming Talk
---

### Post by dchurch24 on 2009-04-28
Hi all,

I can't seem to find my way around this, I have googled and searched here, but although plenty of people seemingly have the same issue, there appears to be no answer to it.

If I run this line:

os.system("echo -e '\xff\x01\x01' > /dev/ttyUSB0")

The echo executes as it should, but if I run this one (with x00 instead of x01):

os.system("echo -e '\xff\x01\x00' > /dev/ttyUSB0")

I get this error:

TypeError: system() argument 1 must be string without null bytes, not str

I have tried changing the last digit to a string etc... but this happens all the time the last digit in the quotes is not 0.

---

### Post by croto on 2009-04-28
I guess the escaped characters are being interpreted by python. I would try:
```

os.system(r"echo -e '\xff\x01\x01' > /dev/ttyUSB0")

```
to prevent python to interpret the escape characters.

---

### Post by nebffa on 2012-09-10
> **croto said:**
> I guess the escaped characters are being interpreted by python. I would try:
```

os.system(r"echo -e '\xff\x01\x01' > /dev/ttyUSB0")

```
to prevent python to interpret the escape characters.
 
Hi, I made a new account just to say that this worked for me (feedback is essential for people on google looking for solutions).
 
 
Thanks

---

### Post by Bachstelze on 2012-09-11
Why on Earth would you use system() for that?

---


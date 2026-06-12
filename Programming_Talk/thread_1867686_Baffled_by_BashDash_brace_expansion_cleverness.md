---
title: "Baffled by Bash/Dash brace expansion cleverness"
date: 2011-10-23
forum: Programming Talk
---

### Post by ofnuts on 2011-10-23
While tracking what really gets executed when I invoke the native2ascii command in the IBM JDK, I stumbled upon a very short script that contains:
```

#! /bin/sh
exec /usr/lib/j2sdk1.6-ibm/bin/native2ascii ${1+"$@"}

```And I can't figure out what this ${1+"$@"} is trying to achieve (I would have use a plain $@), since I don't see this as a valid brace expansion... but the plot thickness when one notices that the script is run by /bin/sh which is dash and not bash, so brace expansion would not be supported anyway? 

If that makes any difference, /usr/lib/j2sdk1.6-ibm/bin/native2ascii isn't a script (ELF 32-bit LSB executable)

---

### Post by Vaphell on 2011-10-23
${x+y} seems to work in sh just fine.
"script"
```
echo ${1+"x"}
```
```
$ sh params.sh

$ sh params.sh abc def
x

```

I also don't get why would anyone use that. ${1+"$@"} tests if $1 is set and if true, uses the alternate value of "$@" instead which i think is the same as using $@ in the first place.

---

### Post by StephenF on 2011-10-23
> **Vaphell said:**
> I also don't get why would anyone use that. ${1+"$@"} tests if $1 is set and if true, uses the alternate value of "$@" instead which i think is the same as using $@ in the first place.
ls -l -h

is not

ls "-l -h"

and

ls

is not

ls ""

---

### Post by Vaphell on 2011-10-23
that's true but it doesn't make any difference here as far as i can tell

i wrote a script that passes params with both methods to another script that prints the params and their number
```
$ sh params.sh
${1+"$@"}:  / 0
     "$@":  / 0
$ sh params.sh ""
${1+"$@"}:    // 1
     "$@":    // 1
$ sh params.sh "" "" ""
${1+"$@"}:    /  /  // 3
     "$@":    /  /  // 3
$ sh params.sh "a" "" ""
${1+"$@"}:   a /  /  // 3
     "$@":   a /  /  // 3

```

---

### Post by StephenF on 2011-10-23
I did the same and got the same results. I can only imagine that this is compatibility code and some other shell out there does things differently.

---

### Post by gsmanners on 2011-10-23
Yes, nothing like being clever rather than doing a version check explicitly.

---

### Post by Arndt on 2011-10-23
> **gsmanners said:**
> Yes, nothing like being clever rather than doing a version check explicitly.

What would that version test look like?

---

### Post by gsmanners on 2011-10-23
> **Arndt said:**
> What would that version test look like?

Darned if I know, but I tell you one thing: I'd write in Python or C -- not Bash script.

---

### Post by ofnuts on 2011-10-24
Glad to see I'm not the only one baffled :)

---

### Post by sisco311 on 2011-10-25
${1+"$@"} is a parameter expansion, NOT a brace expansion.

BASH:
```
man bash | less +/"^ +Parameter Expansion"
```

DASH:
```
man bash | less +/"^ +Parameter Expansion"
```

POSIX:
[http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_06_02](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_06_02)

Also check out BashFAQ 83 (link in my signature).

---

### Post by gsmanners on 2011-10-25
Oh, I see. This is a case of "cleverness" on the part of Bash, not the coders.

---

### Post by Arndt on 2011-10-25
> **gsmanners said:**
> Oh, I see. This is a case of "cleverness" on the part of Bash, not the coders.

I think this construction predates bash. Some implementations of sh handled arguments somewhat differently than others, and someone came up with this trickiness to be portable. I've never really investigated what it does and why.

---


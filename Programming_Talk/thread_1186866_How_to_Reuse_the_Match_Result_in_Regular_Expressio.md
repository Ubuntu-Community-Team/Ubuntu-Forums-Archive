---
title: "How to Reuse the Match Result in Regular Expression?"
date: 2009-06-13
forum: Programming Talk
---

### Post by huangyingw on 2009-06-13
Hello,
     I have matched out ```
bj2_brcm_1.6
``` from ```
\\STBReleases\releases\bj2_brcm_1.6_Builds\bj2_brcm_1.6_1119\ce_sdk_client_nondebug_bcm7405\package\officialRAG\New\Application_1.6.1119.41.dat
```, using ```
\w{1,10}.\w{1,10}(?=_Builds)
```,
     My next step is to use the ```
bj2_brcm_1.6
``` to match out ```
1119
```, which just behind ```
bj2_brcm_1.6
```.
    How to write such a regular expression, which could reuse the previous part's match result to match out the next goal?

---

### Post by soltanis on 2009-06-13
Use capture groups, and one expression:

```

(\w{1,10}.\w{1,10}).(\d+)

```

I removed part of your expression, because judging by your example, it was useless.

Assuming you're using Perl (or at least, some form of perl compatible regexes), the first capture group (which is in parentheses) is now in $1 and the second capture group (which is the digit group you wanted) is now in $2.

---

### Post by huangyingw on 2009-06-14
> **soltanis said:**
> Use capture groups, and one expression:

Hey, expert, your expression don't meet my needs.
My aim is:
use 
```

\w{1,10}.\w{1,10}(?=_Builds)

```
to match out
```

bj2_brcm_1.6

```
then use 
```

(?=bj2_brcm_1.6)_\d{1,4}

```
to match out
```

1119

```
So, the final one would be like following expression, 
```

(?=(\w{1,10}.\w{1,10}(?=_Builds)))_\d{1,4}

```
But I don't know why it does not work:(...

---

### Post by huangyingw on 2009-06-14
And I think one of my confusion is the one
```

Windows (?=NT|XP)

```
could match out
```

Windows 

```
From 
```

Windows 98, Windows NT, Windows 2000

```
But, this one, 
```

(?=NT_)Windows

```in which I just put the (?=xxxx) in the beginning, 
to try to match this string:
```

NT_Windows

```
does not work, does the (?=xxxx) structure could not take effect when it is used as a prefix?

---

### Post by soltanis on 2009-06-16
I am unfamiliar with this regular expression syntax. I also don't really understand what you are trying to do. If you want to match any pattern of words with some digits behind them, that regex should work.

---

### Post by huangyingw on 2009-06-17
> **soltanis said:**
> I am unfamiliar with this regular expression syntax. I also don't really understand what you are trying to do. If you want to match any pattern of words with some digits behind them, that regex should work.
Yes, still thank you for your guidance at these related threads. I will try more..

---


---
title: "Regex help"
date: 2010-02-08
forum: Programming Talk
---

### Post by Rhiknow on 2010-02-08
Greetings,

I'm writing a Perl script to clean some message forum text.

There are quite a few instances of 

aaaaaaaaaaaaaah
gggggggrrrrrrrr
oooooooooouch
ggoooooooooooooooooogle
etc.

Anyone have any ideas as to how I might regex these out?

I was thinking of something like if the same character appears three times in a row, match the word so it can be deleted.

The insight of any regex expers is much appreciated.

Rhik

---

### Post by Hellkeepa on 2010-02-08
HELLo!

Not sure what RegExp flavour your language supports, but you might try something like this:
```
/([a-z]){3,}/
```
That is, if I've understood your intent correctly?

Happy codin'!

---

### Post by Rhiknow on 2010-02-08
Hi,

Thanks for the message.

That'll match any words greater than length 3. I want it only to match words with a repetition of 3 or more letters.

---

### Post by Trumpen on 2010-02-08
This should remove every word which contains at least one
sequence of three or more characters:

```
$line =~ s/\b\w*(\w)\1{2,}\w*(?:\s|$)//g
```

---

### Post by Rhiknow on 2010-02-09
> **Trumpen said:**
> This should remove every word which contains at least one
sequence of three or more characters:

```
$line =~ s/\b\w*(\w)\1{2,}\w*(?:\s|$)//g
```

**Seriously** well done mate. Never would have been able to figure that one out. My fellow postgrads are very impressed with the line noise on my vim terminal :)

Greetings from emerald Ireland.

---


---
title: "dumping files in hexadecimal with characters in utf8"
date: 2019-04-20
forum: Programming Talk
---

### Post by Skaperen on 2019-04-20
i have written a few programs that dump bytes in hexadecimal form, often with printable/displayable ASCII characters being shown in various formats.  now i want to also support octet/byte streams that include Unicode characters encode in utf8 form.  what i am thinking about right now is what the output should look like.  i would like for it to be clear which octets form the encoding of the one character.  my thought on that was wrapping the octet(s) making up the character in parenthesis just before the character itself.  Unicode also includes character modifiers such as accent marks of various kinds.  perhaps a modified character needs to be treated like a single character wrapping multiple encodings together, separated by a comma.  then i think it might be of help to also show the decoded U+ code number.  but this could end up being hard to read the hexadecimal of the dumb.  perhaps the reader wants to see 2-byte, 4-byte, or 8-byte numbers, maybe signed, and in a specific endian order, and base (decimal, typically).  sometimes numbers are aligned and sometimes not (the architecture might be unknown and the user might be dumping it without knowing to figure out such things).

i'm looking for ideas on what an octet stream dump might look like.

---


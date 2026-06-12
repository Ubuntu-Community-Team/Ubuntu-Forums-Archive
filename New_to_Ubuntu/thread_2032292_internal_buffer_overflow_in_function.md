---
title: "internal buffer overflow in function"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by tristein on 2012-07-23
Hi,

I've been working with a Russian parser that has many components. It seems to work fine as long as I feed pretty clean text into it. But when I try giving it larger, messier text files, it aborts with the following message:

    reading parameters ...
Value of <HANDLE> construct can be "0"; test with defined() at ./lemmatiser.pl line 167.
    tagging ...
3000Use of uninitialized value $pos in concatenation (.) or string at ./lemmatiser.pl line 122, <STDIN> line 3549.
9000
ERROR: Internal buffer overflow in function tag_token
aborted.

Can anyone give me some guidance on understanding what the problem is?

Thanks!

---


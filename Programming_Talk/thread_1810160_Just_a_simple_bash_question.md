---
title: "Just a simple bash question"
date: 2011-07-22
forum: Programming Talk
---

### Post by FuturistCorporation on 2011-07-22
I am doing arithmetic operations in the shell, just to try it out, and I was confused by the output I got for one operation:

If you input:

echo $((2**62))

You get 4611686018427387904, which is correct. But, if you input

echo $((2**63))

You get -9223372036854775808, which would be correct, EXCEPT THE VALUE IS NEGATIVE! Why did this happen?

Furthermore, if you input any value higher than this, i.e.,

echo $((2**64))

You get a value of 0, (rather than a memory error or something). Can anyone explain this to me?? I'm assuming the wrong answer on the last operation has something to do with UTF-8 character encoding (possibly?). But the negative value for $((2**63)) is what I really can't get my head around. Thoughts?

---

### Post by ziekfiguur on 2011-07-23
Value overflow, bash does not support arbitrarily large numbers. apparently 64bit signed integers are used, which means the maximum value for an int is 2 ** 63 - 1 and the minimum is 2 ** 63. If you want to know how that works exactly, see [https://secure.wikimedia.org/wikipedia/en/wiki/Twos_complement](https://secure.wikimedia.org/wikipedia/en/wiki/Twos_complement)

---

### Post by FuturistCorporation on 2011-07-23
Just what I was looking for--thank you!

---


---
title: "Error Correcting Codes"
date: 2011-12-04
forum: Programming Talk
---

### Post by vandorjw on 2011-12-04
Hey everyone, I am working with linear block codes  and I don't understand how the generator matrix is created.

example:
For a (6,3) code, the generator matrix G is:

1 0 0 | 1 0 1 
0 1 0 | 0 1 1
0 0 1 | 1 1 0

The first part is the identity matrix, but I have no idea where the last bits come from. (Parity bits)

For a (7,4) code, the generator matrix G is:
1 0 0 0 | 0 1 1
0 1 0 0 | 1 0 1
0 0 1 0 | 1 1 0
0 0 0 1 | 1 1 1

Is there a pattern for the last part of the matrix? The part after the identity?

Thanks

---

### Post by 11jmb on 2011-12-05
It depends on the code. Each parity bit will be a check on a certain number of data bits. It is spelled out pretty well here:

[http://en.wikipedia.org/wiki/Hamming(7,4)](http://en.wikipedia.org/wiki/Hamming(7,4))

Except that your generator matrix is for a **systematic** Hamming (7, 4). The matrix in the link is slightly different, because the parity bits are interspersed among the data bits, where you code has the parity bits at the end of the codeword. The rules for building the matrix are the same, though.

---


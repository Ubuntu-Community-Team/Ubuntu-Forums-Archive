---
title: "Python help about opening .vmg  file .."
date: 2012-12-07
forum: Programming Talk
---

### Post by prismctg on 2012-12-07
Hi , i have some .vmg files , i can open this file using "cat" but not with "nano" , but my question is how can i open this using python ? i try open() method ... but it gives me some numbers not the actual message :(

---

### Post by Tony Flury on 2012-12-07
I think you will need to open it in binary mode i think, as it contains null characters. 

if i were doing this i would read it into a bytearray type in python, split it up into it's various fields, and convert those fields back to strings, ints etc.

The reason that cat can read the data is it probably ignores the non-ascii printable and null characters.

---

### Post by prismctg on 2012-12-07
Thank u so much :)

---


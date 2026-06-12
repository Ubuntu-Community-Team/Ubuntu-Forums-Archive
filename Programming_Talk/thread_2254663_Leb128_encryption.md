---
title: "Leb128 encryption"
date: 2014-11-29
forum: Programming Talk
---

### Post by jhay2 on 2014-11-29
hi does someone here know the leb128 (signed or unsigned) encryption?

can you explain how does the leb128 (uleb128 or sleb128) actually works using hex not a binary . i saw some examples on google but the explaination is not clear enough to understand . 

how to encrypt and decrypt leb128 to/from hex ?  

thank you

---

### Post by ofnuts on 2014-11-30
leb128 is a not an encrytion, it is a compact representation.

hex and binary are just completely equivalent representation of the data. Since leb128 move bits, an explanation using hex would not help much... What isn't clear enough in [this example]("http://en.wikipedia.org/wiki/LEB128#Unsigned_LEB128")?

---


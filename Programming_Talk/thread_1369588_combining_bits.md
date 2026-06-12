---
title: "combining bits"
date: 2010-01-01
forum: Programming Talk
---

### Post by OgreProgrammer on 2010-01-01
How are two 64 bit numbers combined to simulate a 128 bit number?

I've always wondered ever since my 16 bit 286+ recorded scores in 32 ranges.

Solve my 20+ year quest?

---

### Post by scragar on 2010-01-01
[http://gmplib.org/](http://gmplib.org/)

It's often a better idea to use just a dedicated library for such things, that way upgrading the library as things change is easy, as opposed to strugling to find your own answers and keep them efficient/up to date.

---

### Post by OgreProgrammer on 2010-01-01
Thank you. 

I agree, but its purely about *knowing*. 

It is nosiness drives me to program.

---

### Post by Arndt on 2010-01-01
> **OgreProgrammer said:**
> How are two 64 bit numbers combined to simulate a 128 bit number?

I've always wondered ever since my 16 bit 286+ recorded scores in 32 ranges.

Solve my 20+ year quest?

How do you mean, "how"? You take two 64-bit numbers, A and B, and you say that A is the higher 64 bits and B is the lower 64 bits of the 128 bit number. Then you implement the arithmetic operations accordingly.

---

### Post by OgreProgrammer on 2010-01-01
> **Arndt said:**
> How do you mean, "how"? You take two 64-bit numbers, A and B, and you say that A is the higher 64 bits and B is the lower 64 bits of the 128 bit number. Then you implement the arithmetic operations accordingly.

I know that from registers in assembler, but I am looking for information on how they catch overflow digits in multiplications and whatnot.

---

### Post by scragar on 2010-01-01
> **OgreProgrammer said:**
> I know that from registers in assembler, but I am looking for information on how they catch overflow digits in multiplications and whatnot.

I don't actually think that's what is done in most libraries, I assume they simulate the process by manipulating binary using the same rules that your processor would do for the same calculation, for example addition would work something like(psuedocode):
```
function add(BigInt one, BigInt two){
  BigInt retObj;
  bool overflow = 0;
  char tmp;
  for(int i = one.bits.length - 1; i >= 0; i--){
    tmp = one.bits[i] + two.bits[i] + overflow;
    retObj.bits[i] = tmp%2;// only the odd data
    overflow = (tmp >= 2);
  }
  retObj.overflow = overflow;
  return retObj;
}
```
Obviously this code is both inefficient and takes some shortcuts, but I trust you can work that out on your own. I also don't fully understand the mechanism for converting these numbers back into decimal, I imagine that would be a rather hard goal.

EDIT: in my code I keep note of my own overflow flag for warning the user, this in C++ would be very inefficient in terms of space unless you used char types for your binary data, rather than an array of ints(or better still, an array of bools. that way you can specify a nice working size to go with the excess bool)

---

### Post by MadCow108 on 2010-01-01
> **OgreProgrammer said:**
> I know that from registers in assembler, but I am looking for information on how they catch overflow digits in multiplications and whatnot.

you either don't (e.g. standard 64 bit integers on 32 bit systems)
or you check for overflow on each operation and increase the size of your number.
To reduce operations you can represent your number in a high base thus reducing the number of basic types needed to represent a single number.

---

### Post by OgreProgrammer on 2010-01-01
Thanks scragar and madcow108. That function is excellent and the idea of encoding in some high base is very novel too. I can now see how it would be done.

Thanks everyone. I got a little bit from you all. And thats a lot.

Maybe now the nightmares wont come.... :D

---


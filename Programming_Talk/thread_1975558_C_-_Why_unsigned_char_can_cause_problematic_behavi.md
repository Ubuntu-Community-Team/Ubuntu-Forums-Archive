---
title: "C - Why unsigned char can cause problematic behaviour"
date: 2012-05-07
forum: Programming Talk
---

### Post by stamatiou on 2012-05-07
I have read in "C Programming - A modern approach" that some compilers treat char types as a signed character. It also says that if ch is ever used in a contxt that requires the compiler to convert it into an int there will be likley trouble and the resulting integer will be negative. But I can not understand why :/

---

### Post by 11jmb on 2012-05-07
You shouldn't have much problem converting between unsigned char and int (signed or unsigned).

When casting from a signed char to a signed int, I know for gcc, that the sign bit remains, but I don't think that is explicitly in the C standard.

For example, take the byte represented in hex as 0xC8. As an int or unsigned char, this value is interpreted to be the decimal number 200. For a signed char, it would be interpreted to be the decimal number -56. If this signed char were cast to an int, I think it would vary from compiler to compiler whether the int value would be -56 or 200.

As I mentioned earlier, with gcc, it would be -56.

---

### Post by Bachstelze on 2012-05-08
> **11jmb said:**
> 
When casting from a signed char to a signed int, I know for gcc, that the sign bit remains, but I don't think that is explicitly in the C standard.

It is. The standard says that when converting between integer types, if the value can fit in the new type, it is retained. Since int is guaranteed to be at least as large as char, no problem.

---

### Post by 11jmb on 2012-05-08
It's not a matter of size. It is a matter of whether the cast would copy bit 7 from the signed char into bit 31 or bit 7 of the signed int.

I don't think this behavior is standardized, but in my experience on this board, you're more of an authority on C than me :)

---

### Post by Bachstelze on 2012-05-08
> **11jmb said:**
> It's not a matter of size. It is a matter of whether the cast would copy bit 7 from the signed char into bit 31 or bit 7 of the signed int.

I don't think this behavior is standardized, but in my experience on this board, you're more of an authority on C than me :)

You seem to be under the impression that a cast between integers just copies bits. That is not true, it copies the value (if possible, which means always in this case*).

*EDIT:* To even talk about bits in the first place is a typical mistake: to care too much about the internal representation of things. When you have a char with value n and cast it to an int, it will give you an int with value n. Period. It absolutely does not matter how the value n is represented in either type.

*EDIT2:* * Unless int and char have the same width, in which case of course some unsigned char values are impossible to convert into signed int (0x80 to 0xFF).

---

### Post by 11jmb on 2012-05-08
When discussing the internals of a language, it can be useful to discuss internal representations. I see your point though. 

Correct me if I'm wrong, but you're saying that the standard defines a cast as a mapping between two sets of values, rather than a bitwise operation? (which therefore implies that if an element is in both sets, there must be a defined mapping) I've never looked at type casting in this light, but it certainly makes a lot of sense when terminology such as "value" is used.

Thanks for the clarification.

P.S. Your sig reminded me of an uphill battle I had a few months ago to convince a phb-type to ditch an architecture that was a square peg in a round hole for our problem set. We would have had to write a ton of code to interface (poorly) with this library. It was only when I clicked the link that I realized what your sig was actually about. It's funny how similar a bad manager can be to lobbyists who push so hard to keep their buggy whips relevant :)

---

### Post by Bachstelze on 2012-05-08
> Correct me if I'm wrong, but you're saying that the standard defines a cast as a mapping between two sets of values, rather than a bitwise operation? (which therefore implies that if an element is in both sets, there must be a defined mapping) I've never looked at type casting in this light, but it certainly makes a lot of sense when terminology such as "value" is used.

That is right. It must be stressed that for it to work, the value must be in the set of values of the target type. If it is not, other rules apply. (If the target type is unsigned of width n, the value is reduced modulo 2^n; and if it is signed, the result is undefined.)

Also be careful to not consider that a cast is magic of some sort. It is just a way to explicitly perform type conversions; the actual conversion is performed in the same way whether it results from a cast or from some other action.

As for OP:
> 
I have read in "C Programming - A modern approach" that some compilers treat char types as a signed character.

That is true. More precisely, it is up to the compiler to choose whether the type char is equivalent to signed char or unsigned char. Note that I said "equivalent", not "identical", which basically means identical in every respect except that it is still not actually the same type (same situation as int and long int on x86 machines). If you want to be certain of the signedness, declare your variables as signed char or unsigned char.

> It also says that if ch is ever used in a contxt that requires the compiler to convert it into an int there will be likley trouble and the resulting integer will be negative. But I can not understand why :/ 

It depends what you mean by "trouble", but it is true that if you use a char[] as a buffer to store arbitrary binary data (obtained with e.g. read()), you might have some surprises. This is why good practice dictates to always use unsigned char[] for arbitrary data, and reserve char[] for strings of ASCII characters. Virtually no one uses any character type to store integers for arithmetic purposes, even though they are integer types.

---

### Post by Bachstelze on 2012-05-08
while I'm at it, what the standard guarantes about integer types is that:

* The set of signed char values is a subset of the set of short int values, and so on with int, long int and long long int, in that order. A corollary is that a conversion for example from signed char to int is guaranteed to preserve the value.

* The same is true for unsigned integer types (unsigned char, unsigned short, unsigned, unsigned long, unsigned long long, in that order).

* The set of non-negative values of a signed type is a subset of the set of all values of the corresponding unsigned type.

All those subsets need not be proper, as illustrated by the fact that they are equal for int and long int on x86 machines.

---

### Post by Arndt on 2012-05-08
> **stamatiou said:**
> I have read in "C Programming - A modern approach" that some compilers treat char types as a signed character. It also says that if ch is ever used in a contxt that requires the compiler to convert it into an int there will be likley trouble and the resulting integer will be negative. But I can not understand why :/

An example of a situation which can give problems is if you use an expression of char type to index an array. If chars are unsigned, it will likely work as you expect. If chars are signed, it will not.

---

### Post by Bachstelze on 2012-05-08
> **Arndt said:**
> If chars are signed, it will not.

Specifically?

*EDIT:* I am not implying that it's okay to use char values to subscript arrays. Like I said above, no one uses any character type for arithmetic purposes, which is what array subscripting is. But if one knows what they are doing, it will not lead to unexpected results (even though it is still a bad idea).

---


---
title: "Questions on C types"
date: 2009-03-30
forum: Programming Talk
---

### Post by James_Lochhead on 2009-03-30
Hi everyone,

I have been self-teaching myself a bit of C and have a few questions on the ins and outs of integer types.

1) My book makes no mention of the type "char" being a synonym of either "signed char" or "unsigned char", however there is a reference to "char" in a table of min/max values saying having a look at signed/unsigned char. Can be char be used by itself (while still complying to standards) or is the reference in the table just misleading?

2) In the same min/max value table as question 1 there is a reference to int/unsigned int being two OR four bytes. How does it work? Is it dependant on the compiler or the machine? Is this something I should be wary of when trying to develop cross platform code?

3) In the same table again four byte int and four byte unsigned int are listed as having the same maximum value (2,147,483,647). How can this be? Surely this defeats the point of having an unsigned int.

Please don't pull any blows: I am comfortable with binary numbers and C is not my first programming language.

---

### Post by Simian Man on 2009-03-30
Basically it is all implementation dependent.  C was originally meant to be a portable assembly language so the basic types represent exactly the basic types on the underlying architecture you are using.

If you are using char to represent an ASCII value (we'll leave wide chars out - that's a whole nother mess), just use 'char'  it will default to something appropriate.  If you are using char to store a small integer, use either 'signed char' or 'unsigned char' depending on your needs.

If you need to do bit manipulation and must know how large the values are, use typedefs in order to make your code easily portable.  Better yet you can use an existing library for this.  I know SDL has this, but I'm sure there are others.

If you need to store integers that are on the order of 2^32, you shouldn't really be using any basic type, but a library for large numbers such as the GNU MPL.

---

### Post by James_Lochhead on 2009-03-30
Ok thanks. That makes more sense.

---


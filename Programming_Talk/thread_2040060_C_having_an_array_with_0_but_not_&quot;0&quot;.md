---
title: "C having an array with 0 but not &quot;\0&quot;"
date: 2012-08-10
forum: Programming Talk
---

### Post by scorpious on 2012-08-10
I'm trying to create a maze that has a zero in it but C confuses this with the null byte so instead of getting a maze like this
#####
#0 # . S
# . #  .#
# .  .  . #
#####

I get a maze like this
#####
## . S
# . # . #
# .  .  . #
#####

Is there a way to get C to insert a zero as an int instead of a null bite?

I don't think using '0' will help as the next step is to find the number and increase it by 1.

---

### Post by dwhitney67 on 2012-08-10
A zero and a NULL-byte are not the same.  If you want to insert a 0 character into your array, use '0', not '\0' (which is the NULL-byte).

---

### Post by albandy on 2012-08-10
printf("%d",integer_variable); This will print the integer value.

As said before, an integer and an ascii char are different things, but in fact both are integers.

For example, the character 0 is an integer (well really a char) of value 48.

---

### Post by scorpious on 2012-08-10
Thanks for the quick reply. however I don't want to insert a 0 *character*, I want to insert a 0 *int*.

EDIT: Turns out that I can add and subtract to char's as if they were ints. Didn't know that. I'll use chars from now on.

Thanks

---

### Post by albandy on 2012-08-10
> **scorpious said:**
> Thanks for the quick reply. however I don't want to insert a 0 *character*, I want to insert a 0 *int*.

You have to work with it adding and substracting the value of '0'

---

### Post by Bachstelze on 2012-08-10
A 0 integer and a null byte are the same thing. Post code.

*EDIT:* And describe more precisely what you want to do.

---

### Post by lisati on 2012-08-10
> **Bachstelze said:**
> A 0 integer and a null byte are the same thing. Post code.

And has already been noted, a char '0' is different. A \0 or any other int isn't always suitable for sending directly to the display.

---

### Post by Bachstelze on 2012-08-10
> **lisati said:**
> And has already been noted, a char '0' is different.

OP has made clear that he wants to store an integer 0, not a char '0'.

> A \0 or any other int isn't always suitable for sending directly to the display.

And how do you know that the data is sent "directly to the display"? This is why I asked for some code.

---

### Post by nvteighen on 2012-08-10
If you're dealing with strings, the best you can do is to stick to ASCII characters, i.e enclose everything between single quotation marks. Otherwise, printf and all other I/O functions will interpret 0 as '\0', thus yielding weird results that I believe that you don't want. Stay coherent and everything will be much easier.

Note: of course a char can hold a 0, even inside a char array... the problem is not derived from the data type (in C types are just length specifications), but the C Standard I/O library, which operates by assuming that 0 is the NULL-terminator.

---

### Post by Bachstelze on 2012-08-10
> **nvteighen said:**
> (in C types are just length specifications)

Not quite. ;) A right bitwise shift will operate differently on a signed and unsigned integer of the same length, for example. Also a pointer, while being an integer internally, is governed by different rules.

---

### Post by Bachstelze on 2012-08-10
But the idea is: if you want to use string I/O functions from the standard library, you can't have a 0 byte in the middle of a string, since a 0 byte by definition represents the end of a string. If you want to have 0 bytes, you will have to cook up your own display function.

---


---
title: "cstring.h question"
date: 2008-02-21
forum: Programming Talk
---

### Post by keeler1 on 2008-02-21
Many of the functions is cstring take a char * and return one as well.

For example strtok takes some char * and returns some tokenization of it.

I am using this function and need to know a couple of things.  Is the char * returned dynamically allocated or is it just a pointer into the inputted array of characters.  And 2, if it is dynamically allocated will c take care of it since I didnt allocate the memory or do I have to delete it myself

---

### Post by mike_g on 2008-02-21
Its just points to a location within the string, it does not allocate separate space or anything.

---

### Post by Lster on 2008-02-21
I really wasn't sure of this myself, either. I had a look in LibC, though:

> **LibC Manual]&#8212 said:**
> 

But look at this:

[QUOTE=LibC Manual]**Warning: Since strtok and wcstok alter the string they is parsing, you should always copy the string to a temporary buffer before parsing it with strtok/wcstok (see Copying and Concatenation). If you allow strtok or wcstok to modify a string that came from another part of your program, you are asking for trouble; that string might be used for other purposes after strtok or wcstok has modified it, and it would not have the expected value.**

The string that you are operating on might even be a constant. Then when strtok or wcstok tries to modify it, your program will get a fatal signal for writing in read-only memory. See Program Error Signals. Even if the operation of strtok or wcstok would not require a modification of the string (e.g., if there is exactly one token) the string can (and in the GNU libc case will) be modified. 

Here's the link:

[http://www.gnu.org/software/libc/manual/html_node/Finding-Tokens-in-a-String.html#Finding-Tokens-in-a-String](http://www.gnu.org/software/libc/manual/html_node/Finding-Tokens-in-a-String.html#Finding-Tokens-in-a-String)

Hope that helps,
Lster

---


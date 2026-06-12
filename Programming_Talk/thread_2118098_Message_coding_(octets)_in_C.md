---
title: "Message coding (octets) in C"
date: 2013-02-20
forum: Programming Talk
---

### Post by illegal on 2013-02-20
Need a bit of programming help.
I have a message structure with 'n' octets. I have to fill up all octets one by one and after filling an octet, I have to check the value of a byte '*value*' and rewrite that particular octet with the value of '*value*'.

ie, if the first octet is filled as 0 (ie 00000000) and then the value of '*value*' is 1, I have to rewrite 0 as 1 (ie 00000001).

What I am planning to do is, after filling up the octet, move the whole message to a temporary variable, update the last octet with '*value*' and then ORing it with the original message and continue to the next octet.

Hint: I am maintaining the size of the whole message buffer after filling up each octet. Call it msgLenByte.

Could someone give me a logic for this?

---

### Post by ofnuts on 2013-02-20
> **illegal said:**
> Need a bit of programming help.
I have a message structure with 'n' octets. I have to fill up all octets one by one and after filling an octet, I have to check the value of a byte '*value*' and rewrite that particular octet with the value of '*value*'.

ie, if the first octet is filled as 0 (ie 00000000) and then the value of '*value*' is 1, I have to rewrite 0 as 1 (ie 00000001).

What I am planning to do is, after filling up the octet, move the whole message to a temporary variable, update the last octet with '*value*' and then ORing it with the original message and continue to the next octet.

Hint: I am maintaining the size of the whole message buffer after filling up each octet. Call it msgLenByte.

Could someone give me a logic for this?
Looks like homework... or you are inventing a convoluted solution to a simple problem.

---

### Post by illegal on 2013-02-20
> **ofnuts said:**
> Looks like homework... or you are inventing a convoluted solution to a simple problem.

No, not a homework :) I've got some code from somewhere and am trying to do some mods :) The 'value' change looks a bit tricky and I am not really getting any clue how to go ahead. Googling didn't help much...

The idea of copying it to a new buffer and modifying the octet is my simple logic, but don't know how do I implement it. if anyone has any other ideas which could be implemented, kindly let me know :)

If someone could help me with a code snippet, it would be of great help :)

---


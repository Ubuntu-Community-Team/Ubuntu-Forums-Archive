---
title: "Can you recommend a good book about network protocols/programming"
date: 2011-02-09
forum: Programming Talk
---

### Post by schmendrick on 2011-02-09
Hi all,

i think i can say i am quite experienced in using sockets in c, .NET and java i have been writing on and even been inventing small protocols, both privately and for companies,, i am creating my own (i daresay quite sophisticated RPC protocol) and have made SNMP interfaces through APIs, ... but i am lacking the background theories. more than one time i had a "ah, if i had just known THAT before...."

my whole experience is learning-by-doing, i have never been in university to learn anything about networking.

of course, i know have heard about the different layers of OSI and read my parts on wikipedia about UDP, TCP, Headers and all that.

but now i wonder if anyone would know some kind of book that explains different types of networking techniques one can use, advantages and disadvantages of the implementations of different kinds of protocols (not only broadly about TCP vs. UDP)... or something like a guidebook where what parts of a protocol belong to, eg. how error handling can be done (i dont find a better explanation).

just explaining the different layers of OSI or a picture about which bit in a TCP Header does what is not what i am looking for, for THAT i found some books.

something so i can then say: "ah HA, they used THAT, well thats clever, next time i have that problem i can use that too" or a
"well now i know this approach is better suited for the needs at hand"

i hope i could make myself clear what i am searching for.


any suggestions?


thanks in advance,

schmendrick

---

### Post by juancarlospaco on 2011-02-09
Also search for IPv6 books, im reading "IPv6 in Action: a *Nixers guide".
*IPv4 is dead anyways...*

---

### Post by Simian Man on 2011-02-09
[Tanenbaum's "Computer Networks"]("http://www.amazon.com/Computer-Networks-4th-Andrew-Tanenbaum/dp/0130661023") is the standard for graduate level networking classes.  It sounds perfect for you in that explains not only how things like TCP and UDP work, but also gives insight into why they were designed a certain way and older, or alternative, ideas.

---

### Post by schmendrick on 2011-02-11
> **Simian Man said:**
> [Tanenbaum's "Computer Networks"]("http://www.amazon.com/Computer-Networks-4th-Andrew-Tanenbaum/dp/0130661023") is the standard for graduate level networking classes.  It sounds perfect for you in that explains not only how things like TCP and UDP work, but also gives insight into why they were designed a certain way and older, or alternative, ideas.


i took a look at it and it really seems what i am looking for! i am currently ordering the 2010 edition.

thanks!

---


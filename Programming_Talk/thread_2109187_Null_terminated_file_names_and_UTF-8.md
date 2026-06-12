---
title: "Null terminated file names and UTF-8"
date: 2013-01-26
forum: Programming Talk
---

### Post by bird1500 on 2013-01-26
Hi,
Afaik at the lowest level all solutions (Java, C, Python etc) get the file names of a dir from dirent->d_name which is a null terminated string.

Afaik, in UTF-8 only like the first few hundred chars that directly correspond to ASCII can be null terminated, true? I mean, to represent non-ASCII chars UTF-8 often requires 2 or more bytes, and since some of them (probably) might have a null byte as the first or second byte of a 2-byte char you can't rely on the fact that a null char is only at the end of the file name.

So how does this work that we get null terminated file names yet they can represent any UTF-8 strings? Is there some en/decoding going on at runtime?

---

### Post by Bachstelze on 2013-01-26
> **bird1500 said:**
> I mean, to represent non-ASCII chars UTF-8 often requires 2 or more bytes, and since some of them (probably) might have a null byte as the first or second byte of a 2-byte char you can't rely on the fact that a null char is only at the end of the file name.


Instead of saying "probably", how about you do some reading about it? Here for UTF-8: [http://en.wikipedia.org/wiki/UTF-8#Description](http://en.wikipedia.org/wiki/UTF-8#Description)

---

### Post by bird1500 on 2013-01-26
Any ideas?

---

### Post by xb12x on 2013-01-26
> **bird1500 said:**
> Any ideas?

Yes, here is an idea: 

Follow the link that Bachstelze took the time to find for you.

---

### Post by bird1500 on 2013-01-26
There's a lot of baffle gab I didn't get the point and which part is the answer.

---

### Post by Bachstelze on 2013-01-26
The point is that contrary to your assumption, the null byte cannot occur in any other character than the null character.

---

### Post by bird1500 on 2013-01-26
> **Bachstelze said:**
> The point is that contrary to your assumption, the null byte cannot occur in any other character than the null character.
Now that's an answer, thanks for this one. Just pointing to RFCs for the answer implies there should be no (programming) forums, because any question can be solved by telling people to read such and such book, RFC or what not.

---

### Post by Bachstelze on 2013-01-26
> **bird1500 said:**
> Now that's an answer, thanks for this one. Just pointing to RFCs for the answer implies there should be no (programming) forums, because any question can be solved by telling people to read such and such book, RFC or what not.

That wasn't a RFC, that was Wikipedia. Also, forums are usually for questions that involve more discussion than a mere statement of fact.

---

### Post by bird1500 on 2013-01-26
I didn't say only RFC, "... or what not", and don't try to treat people's statements literally. Links are meant for additional clarification, especially if there's low level jargon that few programmers need to understand.
From my experience in participating in forums, replying to a thread from the get go "read that and figure out" is about the worst suggestion, but helpful, just like sending to the arctic for ice.

---

### Post by lisati on 2013-01-26
Please! Let's not digress into name calling, otherwise this thread might get closed.

I see not so much a "Read the fabulous manual' but 'here is a link that might be helpful'.

---

### Post by bird1500 on 2013-01-26
> **lisati said:**
> Please! Let's not digress into name calling, otherwise this thread might get closed.

I see not so much a "Read the fabulous manual' but 'here is a link that might be helpful'.
True, but look how he answers, instead of just telling what's the matter he insults ("how about you do some reading about it?") and puts a link to low level stuff.
When I was in bad mood and kind of a moron I used to do this type of "help"  (on another forum) by slightly insulting them and to make people's life harder by giving a loose answer (usually a link to read on their own, something low level and borring) while appearing to help them on the surface and if someone complains - there's plenty of room to brag about and pick words, it's ok to close this thread.

---


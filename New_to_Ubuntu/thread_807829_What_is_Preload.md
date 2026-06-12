---
title: "What is Preload"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-26
Hello, 
I am 'ok' with my Ubuntu current responsiveness but since I just come to know about Preload feature, why not! if i try. What is this thing actually. IN XP, there is Prefetch thing, it is available in Ubuntu as well. Is Preload deserve a try? Btw this is my sys spec;Pentium M 1.83Ghz, 1GB RAM and 1.29GB SWAP Partition

---

### Post by Xiong Chiamiov on 2008-05-26
You'll have to be a bit more specific what it is you're asking about.  What is this Prefetch, and what does it do?

---

### Post by twright on 2008-05-26
preload, the package

it can make some things open quicker but the difference is not that noticeable

---

### Post by sayakb on 2008-05-26
Yes, preload is like prefetch in XP. It would show noticable outcomes only if you have a handsome amount of RAM (not much you get on a 1GB RAM). It caches the applications you mostly use on the disk so that they can be quickly loaded on further execution.

---

### Post by wariskampar on 2008-05-26
@Xiong Chiamiov; how more specific should i be? 
@LinuxIsInnovation; in that case i have to hold myself from using Preload until I upgrade my RAM. However, can I set Ubuntu to cache my favorite program in SWAP Partition instead of physical RAM because I see Ubuntu only use a bit of SWAP capacity (show 0% in Conky). 
ps: that arises another question, how does SWAP function:)NVM, i'll google it

---

### Post by sayakb on 2008-05-26
Preload caches on the disk itself, just like prefetch. You might use preload, but it will not show any drastic changes. You might also increase the "swappiness" that would increase swap usage. Since your Hard drive is much slower than your RAM, increased swap usage will decrease system performance. So if swap is 0%, its a good thing that most of the processes are being handled by the RAM itself.

---


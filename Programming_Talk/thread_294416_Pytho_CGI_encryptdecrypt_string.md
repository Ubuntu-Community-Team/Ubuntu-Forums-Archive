---
title: "Pytho CGI encrypt/decrypt string"
date: 2006-11-06
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-06
Hey all

Another Python thing. Thought I would start a new thread to get this noticed. It is a different question after all.

Anyway getting into it. Is it possible to encrypt a string, send it through a URL (I can do that part) and decrypt it to reveal the string on another page. It's my own idea for keeping track of people logged in. It doesn't need to be fool proof as this is not a real project but one for a piece of coursework. Just need to have some screens and say how it works basically.

Can anyone help?

Thanks

Ironfistchamp

---

### Post by Joe_CoT on 2006-11-06
You can certainly uuencode the data and pass it in the query string, but you're probably better off just implementing sessions and storing the data locally.

python doesn't support sessions natively. You'd basically need to create a cookie on their system with an id number, which matches an id for the data you store locally.

Or, if you don't care about them changing the data (which you can't possibly, if you're sending it in the url), you can store it in a cookie on the client machine.

---

### Post by ironfistchamp on 2006-11-07
Interesting ideas. I shall research them. Just out of curiosity, how would I go about encrypting and decrypting a string?

Thanks

Ironfistchamp

---

### Post by Joe_CoT on 2006-11-07
[Encode and decode uuencode files](http://docs.python.org/lib/module-uu.html). That's encoding, not encrypting.

As for encrypting, there's numerous toolkits, libraries, etc available. Try [Googling](http://www.google.com/search?q=python+encrypt) for it.

---

### Post by ironfistchamp on 2006-11-07
Thanks for the reply I shall follow that up.

---


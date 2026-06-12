---
title: "Making a GPG certificate"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Sydius on 2008-08-15
I'm a bit confused.  When I do:

```
$gpg --export -a *name* > *file*
```

Am I making a GPG/PGP certificate? If not, how do I?  I'm not sure if, when the documentation says "key" if it implies the certificate that holds the key, or just the key.

Also, is it possible to associate arbitrary data with a key? I put my short name (Chris) on my key, and I'd like to also have on it my long name (Christopher), for example.

---

### Post by Sydius on 2008-08-15
To answer the second part of my question, I was able to add a second name to the key by doing:

```

$ gpg --edit *name*
Command> adduid
*... fill in details ...*
Command> save

```

But I am still wondering about the first part of my question.

---

### Post by Sydius on 2008-08-18
Bump.  Maybe hints of where to look?

---


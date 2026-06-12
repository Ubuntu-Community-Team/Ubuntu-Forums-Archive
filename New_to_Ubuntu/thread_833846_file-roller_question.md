---
title: "file-roller question"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Primefalcon on 2008-06-19
I do have one question though about file-roller, I used use 7-zip when I was using windows, great program, a lot better than the rar and zip formats.

However I when I first set up Ubuntu I installed 7-zip and was surprised that it just rolled this support into file-roller instead of being stand alone with the 7-zip window. Anyhow My questions are....


**1.** Is it possible to use different compression ratio's rather than just the default? if so, how?

**2.** Is it possible to password these compressed archives? if so, how?

Thank you

---

### Post by Primefalcon on 2008-06-19
If it's not possible just a no will do :-)

---

### Post by Kingsley on 2008-06-19
I know file-roller can set a password for the archive by going into the 'Edit' menu.

---

### Post by Simon-v on 2008-07-04
> **Primefalcon said:**
> I do have one question though about file-roller, I used use 7-zip when I was using windows, great program, a lot better than the rar and zip formats.

However I when I first set up Ubuntu I installed 7-zip and was surprised that it just rolled this support into file-roller instead of being stand alone with the 7-zip window. Anyhow My questions are....


**1.** Is it possible to use different compression ratio's rather than just the default? if so, how?

**2.** Is it possible to password these compressed archives? if so, how?

Thank you


Regarding the first question, one way is to open **gconf-editor**, navigate to ***/apps/file-roller/general*** and set ***compression_level*** to "*maximum*", changing the default behavior.

---


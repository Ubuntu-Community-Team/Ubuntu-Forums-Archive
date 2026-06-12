---
title: "set default keyring password"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by soxs on 2008-10-12
Hi, though I got very used to linux, I got over a question the sounds simple but is really driving me nuts.

Where can I set the default keyring password??

---

### Post by spiderbatdad on 2008-10-12
This is set when the key is generated...it can't be recovered if lost. You can set preferences in seahorse Accessories>Passwords and Encryption Keys to unlock the keyring when you login, or change the passphrase. Otherwise you will be requested for a password when one is needed.
Similarly thunderbird-enigmail offers you a password prompt when needed.

---

### Post by roger_1960 on 2008-10-12
Hi

I think it can be done in "system-preferences-encryption&keyrings" then select the login item in the window and select "change/unlock password"

---

### Post by soxs on 2008-10-12
> **roger_1960 said:**
> Hi

I think it can be done in "system-preferences-encryption&keyrings" then select the login item in the window and select "change/unlock password"

There is a somewhat folder-like-structure. But don't see anything being related to login.

This is like it looks when I do what <spiderbatdad> suggested, but this requires me to know my old passphrase which I DO NOT HAVE.

---

### Post by soxs on 2008-10-12
- removed -

---

### Post by spiderbatdad on 2008-10-12
> **soxs said:**
> There is a somewhat folder-like-structure. But don't see anything being related to login.

This is like it looks when I do what <spiderbatdad> suggested, but this requires me to know my old passphrase which I DO NOT HAVE.

You will need to generate a new key. AFAIK the passphrase cannot be recovered if lost.

---

### Post by vakis on 2009-08-03
i had the same problem 
try deleting login and default from Accessories>Passwords and Encryption Keys (paswords) it is the last tab
and make new ones

---


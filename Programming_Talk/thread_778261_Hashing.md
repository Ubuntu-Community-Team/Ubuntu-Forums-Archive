---
title: "Hashing?"
date: 2008-05-01
forum: Programming Talk
---

### Post by cartisdm on 2008-05-01
I have my final exam tomorrow and I'm going through my study guide and my teacher says we need to know what a "hashing routine" is.  I don't have that in the index or glossary of my book anywhere AND I googled it and didn't get any decent results.  Could someone please point me in the direction of what the heck my prof. is talking about?

(My class is about Visual Basic btw)

---

### Post by ibuclaw on 2008-05-01
Hashing is a way of encrypting data with salt.

But for your exam, I'm sure all you need to know is that MD5 and SHA are algorithms to salt the hash.

Look [here]("http://www.obviex.com/samples/hash.aspx") for an example VB.NET code (and some pointers).

Uses of hashing include checksums and password encryptions.

Regards
Iain

---

### Post by cartisdm on 2008-05-01
> **tinivole said:**
> Hashing is a way of encrypting data with salt.

But for your exam, I'm sure all you need to know is that MD5 and SHA are algorithms to salt the hash.

Look [here]("http://www.obviex.com/samples/hash.aspx") for an example VB.NET code (and some pointers).

Uses of hashing include checksums and password encryptions.

Regards
Iain

That's really weird, I've never even come across that before.  I wonder why my prof. would bring it up for the exam.  I'll look more into it though, thanks for the link!!

---

### Post by CptPicard on 2008-05-01
Hashing in the general case doesn't necessarily have anything to do with encryption, although hashes are used among other things in such applications.

[http://en.wikipedia.org/wiki/Hash_function](http://en.wikipedia.org/wiki/Hash_function)

It's just a way to map data into a number, which can then be used in various ways, most importantly as an index into a hashtable data structure.

> **cartisdm said:**
>  I wonder why my prof. would bring it up for the exam.

Because tinivole's sense of the word is most probably not what your prof. has in mind. :)

---

### Post by cartisdm on 2008-05-02
> **CptPicard said:**
> Hashing in the general case doesn't necessarily have anything to do with encryption, although hashes are used among other things in such applications.

[http://en.wikipedia.org/wiki/Hash_function](http://en.wikipedia.org/wiki/Hash_function)

It's just a way to map data into a number, which can then be used in various ways, most importantly as an index into a hashtable data structure.

That makes a little more sense.  I'm sure he means for us to apply it in the sense of arrays etc.](*,)

---

### Post by MaindotC on 2008-05-02
And don't forget Rainbow Tables!

---

### Post by tamoneya on 2008-05-02
if he is relating it with arrays you should probably look into hash maps.  They can be thought of as arrays combined with hashes.

---

### Post by Jessehk on 2008-05-02
[http://eternallyconfuzzled.com/tuts/algorithms/jsw_tut_hashing.aspx](http://eternallyconfuzzled.com/tuts/algorithms/jsw_tut_hashing.aspx)

One of my favourite websites. :)

---


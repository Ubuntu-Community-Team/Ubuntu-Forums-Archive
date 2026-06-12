---
title: "New encryption app available"
date: 2010-11-11
forum: Programming Talk
---

### Post by interval1066 on 2010-11-11
I've written an application for encrypting individual files or directories of files; I've designed it to be easy to use with the Gnome desktop. Distributed with full source, of course. I'm not looking to displace TrueCrypt, that wasn't my goal (that was actually to teach myself some aspects of autotools I wasn't clear about.) This is just easy to use encryption on individual objects that may lie outside of the TrueCrypt need domain.

The project is finished and rather than just toss it I release it into the wild for the hell of it. Grab it here:

[http://tinyurl.com/2fswec6](http://tinyurl.com/2fswec6)

---

### Post by worksofcraft on 2010-11-11
edit: ok problem sorted :)

That's nicely done and all the automake stuff works just as I expected. I managed to encrypt and decrypt several files and got the same result back.

One small improvement might be to make the key a memorable password instead of hexadecimal number. If the algorithm needs a number, perhaps one could just use a checksum of the text password as long as we always use the same algorithm to calculate it.

I can see a use for sending encrypted data through the same "channel" that the plain text would go. e.g. to put an encrypted document on the web that can still transferred and even viewed as text, but intended only for those who know the password.

Thus binary is out because things like utf8 sequences have to remain valid utf8 sequences even if they are changed and some codes have to be excluded... adaptations like that might make this really versatile and even preferable to the standard existing tools!

Thanks for sharing this great start for many new potential projects :)

---

### Post by interval1066 on 2010-11-11
@worksofcraft: Thanks for the good words. I'm confused about one thing though, you should be able to use natural language words for passwords though. One of the modifications I made to Dr. Gladman's code (his oss aes algorithm is the core of the program) was to add a whirlpool hasher that converts words into an acceptable hash. In other words, there's no reason to use hex code, any alpha-numeric-punctuation phrase should work.

---

### Post by interval1066 on 2010-11-11
Oh, this tool will encrypt your porn folder just fine.

---


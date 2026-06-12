---
title: "html iso ascii question"
date: 2010-03-07
forum: Programming Talk
---

### Post by aloprot on 2010-03-07
Greetingz, I didn't knew were to put this post, I hope it's ok here. So I just finished learning html but I have trouble in understanding something. I don't understand what basically is iso, ascii, and what has this to do with my html pages. I read that you use them do display special characters for every language. But I also read that utf8 can display all characters in all languages. So why use iso and ascii anymore. And I don't understand, you need to declare iso ascii or utf8 at the start of the page? What about the lang atribute?
Thank you!

---

### Post by Hellkeepa on 2010-03-07
HELLo!

When you say "ISO" I reckon you mean the ISO-8859-* charsets, and not the organisation itself. ;-)

Anyway, what you're talking about are different charsets (or character encoding sets), they tell the computer/applications how to translate the bits and bytes into readable texts, or characters. Exactly like how you can assign a value to each letter of the alphabet (a=1, b=2, and so forth), and use it to encode text into a string of numbers. The different charsets use different values for different characters, leading to some incompatibilities between them.
ASCII is the basic charset, which contains only 127 characters and is very US-centric. There is no reason to use this charset today, not only because of these limitations (which stems from where space was very limited), but also because most charsets used today are ASCII-compatible. That means that the first 127 characters of the compatible charset is exactly the same as ASCII, with extra characters added after this. Both UTF-8 and ISO-8859-* charsets are ASCII compatible.
The ISO-8859-* charsets, however, are not compatible because some/most characters after the 127th have different values, or not represented at all.

I'd argue that there is no actual reason why to use the ISO-8859-* charsets either, because UTF-8 can represent all of the characters that every single one of the ISO-8859-* charsets can, in a uniform manner. The reason for this is that while the ISO-8859-* charsets only use 1 byte (8 bits, 256 characters), the UTF-8 charset can use up to 4 bytes, (32 bits, 1 114 111 characters).

For what you need to do to use UTF-8 on your web pages, I refer you to this thread:
[http://ubuntuforums.org/showpost.php?p=8907336&postcount=4](http://ubuntuforums.org/showpost.php?p=8907336&postcount=4)

Note that point 2 and 3 are only required if you use a database, point 5 only if you use PHP (or another server side scripting language). Also, you'll need to set your editor to save the documents as UTF-8, naturally enough. ;-)

Read more about the different charsets here:
[http://en.wikipedia.org/wiki/UTF-8](http://en.wikipedia.org/wiki/UTF-8)
[http://en.wikipedia.org/wiki/ASCII](http://en.wikipedia.org/wiki/ASCII)
[http://en.wikipedia.org/wiki/ISO-8859](http://en.wikipedia.org/wiki/ISO-8859)

Happy codin'!

---

### Post by aloprot on 2010-03-07
Thank you, you cleared my mind. Only one thing. I didn't understood this:"Both UTF-8 and ISO-8859-* charsets are ASCII compatible.
The ISO-8859-* charsets, however, are not compatible because"

If the iso 8859-*characters are ascii compatible how they are not compatible?Can you please explain  me?

---

### Post by aloprot on 2010-03-07
Other than that you explication was perfect for me.

---

### Post by Hellkeepa on 2010-03-07
HELLo!

Ah, sorry about that, meant ot write that they weren't compatible with eachother.

Also, "charsets", not "characters". Crucial difference. ;-)

Happy syncin'!

---


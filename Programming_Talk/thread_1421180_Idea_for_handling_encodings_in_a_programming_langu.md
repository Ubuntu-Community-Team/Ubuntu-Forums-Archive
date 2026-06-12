---
title: "Idea for handling encodings in a programming language"
date: 2010-03-03
forum: Programming Talk
---

### Post by PacSci on 2010-03-03
I've been designing a language named Wolf in my head for a while, and what with the big deal everyone's been making about character encodings due to the Python 2/3 switch, I think I came up with a good way to handle encodings.

There are two kinds of strings in Wolf: String and Bytestring. The components are Character and Byte. String is a sequence of Unicode characters (and Character is a code point), while Bytestring is a simple sequence of bytes (so Byte is just a byte). String is always represented internally as Unicode.

Changing a String to a Bytestring is encoding, and changing a Bytestring to a String is decoding. You do this with String's 'encode' method (which returns a Bytestring containing the raw sequence of bytes for the coding) and Bytestring's 'decode' method (which returns a String of the Unicode equivalents for each character in the coding).

To do all this transparently, Strings and Bytestrings have encoding "tags". Whenever a tagged String is encoded and no encoding is specified, the tagged encoding is used to encode it. Whenever a tagged Bytestring is decoded and no encoding is specified, the tagged encoding is used to decode it. And, of course, the 'encode' and 'decode' operations always set the encoding tag on their return value.

Bytestring literals used in the code automatically receive the "ascii" tag, and String literals in the code are tagged with whatever encoding the source file is. Any data received from an external source must be tagged and decoded manually, though file handles let you specify a particular coding to tag read data with.

Do you think this is a good way to handle character encodings? I know character encoding in general is a rather complicated issue, but this is the best way I could think of.

---

### Post by diesch on 2010-03-04
How does one specify the source file encoding ? What do you do if a Bytestring literal includes non-ASCII characters?

If there's a obvious way to specify the source file encoding (like there is in Python) I'd use that encoding for the Bytestring's tag. Or maybe even drop Bytestring literals at all.

For Strings I wouldn't use a encoding tag but derive the needed encoding from the destination if you e.g. write to a Bytestring or a file, and make it an error if no encoding can derived and none is provided.

---

### Post by PacSci on 2010-03-04
> **diesch said:**
> How does one specify the source file encoding ? What do you do if a Bytestring literal includes non-ASCII characters?

If there's a obvious way to specify the source file encoding (like there is in Python) I'd use that encoding for the Bytestring's tag. Or maybe even drop Bytestring literals at all.

I probably should have elaborated that there would be an encoding comment like in Python. Also, I didn't think about non-ASCII characters in bytestrings - the idea behind bytestring literals was that you would use them to express binary or ASCII data. How about, if there are just ASCII characters, it gets the ASCII tag, and if there are non-ASCII characters it gets the source file's tag.

> **diesch said:**
> For Strings I wouldn't use a encoding tag but derive the needed encoding from the destination if you e.g. write to a Bytestring or a file, and make it an error if no encoding can derived and none is provided.

My rationale for String encoding tags is that if you create a String literal and write it somewhere, the Principle of Least Surprise states that all the information in the string should be preserved - thus, the encoding. Also, encodings are a pain in the neck and I would prefer that programmers have to deal with them as little as possible for routine tasks.

I'm not an expert on encodings at the system level, so is there a way you can infer what encoding needs to be used for a particular file?

---

### Post by nmccrina on 2010-03-04
I'm just throwing this out there without thinking it through... :D

What if you just eliminated support for ASCII as such? In other words, make *all* strings UTF-8, and have a 'byte' type for binary data/small numbers?

I'm pretty n00bish when it comes to character encodings, so if that was completely dumb ignore it! (I'd appreciate an explanation of why it wouldn't work, though :) )

---


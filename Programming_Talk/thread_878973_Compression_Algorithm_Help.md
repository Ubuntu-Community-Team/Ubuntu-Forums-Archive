---
title: "Compression Algorithm Help"
date: 2008-08-03
forum: Programming Talk
---

### Post by loganwm on 2008-08-03
Currently I'm messing around with the concept of simple file compression and archival.

Right now the only algorithm that I've worked out to compress files is to (in theory) remove repeated zeros, but track the number of zeros at each offset that are removed so that they may be readded when in decompression.

I suppose it could be done for other repeated chains of bytes and repeated patterns as well, but I don't know how to work that out.

any theories on how to find repeated byte patterns in a file?

---

### Post by GreenN00b on 2008-08-03
You can start here [http://en.wikipedia.org/wiki/Data_compression](http://en.wikipedia.org/wiki/Data_compression)

---

### Post by loganwm on 2008-08-03
> **GreenN00b said:**
> You can start here [http://en.wikipedia.org/wiki/Data_compression](http://en.wikipedia.org/wiki/Data_compression)

More or less, I'm interested in c functions useful for searching for repeated byte patterns.

---

### Post by CptPicard on 2008-08-03
Compression, like encryption, is such a thoroughly researched topic that rolling your own is pointless -- learn the field instead so that you can stand on the shoulders of giants!

Btw, you reinvented Run-Length Encoding.

---

### Post by loganwm on 2008-08-03
> **CptPicard said:**
> Compression, like encryption, is such a thoroughly researched topic that rolling your own is pointless -- learn the field instead so that you can stand on the shoulders of giants!

Btw, you reinvented Run-Length Encoding.

Ha, it came to me in a dream.

Alright then, I suppose it's a bit more productive not to reinvent the wheel :)

Oh well, I suppose I need to work on something else.

---

### Post by Wybiral on 2008-08-03
> **CptPicard said:**
> Compression, like encryption, is such a thoroughly researched topic that rolling your own is pointless -- learn the field instead so that you can stand on the shoulders of giants!

Btw, you reinvented Run-Length Encoding.

I agree. Use zlib or something. It's tested, commonly used, and it already works :)

---

### Post by KingTermite on 2008-08-04
> **CptPicard said:**
> Compression, like encryption, is such a thoroughly researched topic that rolling your own is pointless -- learn the field instead so that you can stand on the shoulders of giants!

Btw, you reinvented Run-Length Encoding.

+1

There have been teams of math PhDs that have worked in this field for years. Unless its an exercise "just to see if you can do it" then just use existing compression libraries that are already out there.

---

### Post by CptPicard on 2008-08-04
Not to mention that being an amateur in either of those fields is dangerous for your data... this again reminds me of PigZip...

[IMG]http://www.hackles.org/strips/cartoon310.png[/IMG]

---

### Post by nvteighen on 2008-08-04
> **CptPicard said:**
> Not to mention that being an amateur in either of those fields is dangerous for your data... this again reminds me of PigZip..

And dangerous for yourself, too. Otherwise, you can end like Preston in [this strip]("http://hackles.org/cgi-bin/archives.pl?request=314")

---

### Post by loganwm on 2008-08-04
It was more of a test to see if I could do it, and I have a semi-successful algorithm for compress/decompress and combine into an archive file, I don't plan on using it, but I'm trying my knowledge of programming.

Thanks for all of the helpful insight and the laughs!

---

### Post by KingTermite on 2008-08-04
> **loganwm said:**
> It was more of a test to see if I could do it, and I have a semi-successful algorithm for compress/decompress and combine into an archive file, I don't plan on using it, but I'm trying my knowledge of programming.

Thanks for all of the helpful insight and the laughs!

If its just an exercise for fun and learning the language than have fun with it....but please don't try to give it to anybody to "use" when you're done.

---

### Post by lisati on 2008-08-04
I had a go at it (writing data compression software) myself a few years ago, a lot of the terminology was over my head! The best I could manage with the half-remembered algorithms I'd seen and could actually understand was a compressed file that was about half the size of the original data. It was, however, still an interesting exercise.

---

### Post by CptPicard on 2008-08-04
When I was at university I implemented as a class project the Burrows-Wheeler transformation (used in bzip2) and then experimented with all sorts of postcompressors... it was interesting, and actually I got pretty close to bzip2 performance on text. But, the fun of it really was based on first having the theory ready... starting from scratch would have sucked. :)

---


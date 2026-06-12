---
title: "How to implement gzip compressor ?"
date: 2012-04-22
forum: Programming Talk
---

### Post by DaviesX on 2012-04-22
I want to implement a data compression algorithm, does anyone know how gzip compress data so fast ?

I have searched some information about Lz77 and Huffman coding, but using original Lz77 cannot achieve such a high performance, what technique does it engaged ?

---

### Post by r-senior on 2012-04-22
Some info on the gzip website ...

[http://www.gzip.org/algorithm.txt](http://www.gzip.org/algorithm.txt)
[http://www.gzip.org/#sources](http://www.gzip.org/#sources)

---

### Post by DaviesX on 2012-04-22
Thanks ! I have spent days to speed up the Lz77 algorithm, but it isn't as fast as the tar.gz. I feel frustrated...

---

### Post by DaviesX on 2012-04-22
[https://skydrive.live.com/?sc=documents&cid=debfb1a1543a0abd#cid=DEBFB1A1543A0ABD&id=DEBFB1A1543A0ABD%21367&sc=documents]("https://skydrive.live.com/?sc=documents&cid=debfb1a1543a0abd#cid=DEBFB1A1543A0ABD&id=DEBFB1A1543A0ABD%21367&sc=documents")

And here is the demo I have made. It can only compress a single file with bad compression ratio.

---

### Post by DaviesX on 2012-04-25
Hi, I have sped up the way to find the duplicated strings by using hash table, but I don't know how to do with that Huffman tree. Can you give some comprehensive explanations ? Thank you ! :)

---


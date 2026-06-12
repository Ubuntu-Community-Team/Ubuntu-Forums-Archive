---
title: "encoding and decoding audio using u-law/ a-law"
date: 2011-03-09
forum: Programming Talk
---

### Post by tesseract4d on 2011-03-09
Hi all,

I am working on a relatively large project in which we are building an application. A small task is to come up with an a program which will take in a buffer of audio data (ideally from the sound card) and encode it using the [u-law]("http://en.wikipedia.org/wiki/%CE%9C-law_algorithm") or [a-law]("http://en.wikipedia.org/wiki/A-law"). Once that is done the data will be sent via the network and will have to be decoded appropriately at the Rx.

I am looking for a library that will provide me the necessary functions for this, and also an example program which would teach me to use those functions. I checked out [libsndfile]("http://www.mega-nerd.com/libsndfile/") which says that is supports u-law and a-law encoding but the issue is that there are functions in its api that do so - or at least I am mistaken.

I've spent a whole day at work googling this with no solid examples. This problem is very probably solved so I don't want to be coding it from the beginning.

Can any one help me out here please ?

regards
tesseract

---

### Post by DuneSoldier on 2011-03-09
It's overkill for your problem, but I use Intel Performance Primitives for working with audio codecs. It's available both under an open-source and commercial license.

It's a bit complex to use, but if you grab the ipp samples it has examples in the Unified Speech Component manual.

---

### Post by tesseract4d on 2011-03-09
Dune Soldier,

The reason I am using libsndfile is because we are already using to get a lot of other work done.
So it would be very convenient to use the same library

regards
tesseract

---

### Post by tesseract4d on 2011-03-11
any help ??

tesseract

---


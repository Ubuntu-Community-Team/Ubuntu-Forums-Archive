---
title: "how would you send/receive parts of a file in a random order?"
date: 2011-09-19
forum: Programming Talk
---

### Post by jobsonandrew on 2011-09-19
Hi,
I was just thinking about how this would be done and wondered if there was anyone here with experience of this :)

If you use a p2p file sharing program like eMule or Bittorrent, the clients are able to download parts of a file in an arbitrary order, and 'build up' the final file from one or more other peers.

How is this achieved? what is the theory behind it?
my thought is:
Does the sender send a byte to the receiver and also tell it which position in the file that byte belongs to.. if so, (im talking about java here) how would you deal with receiving the *last* byte of a file *first*

any advice/thoughts?

---

### Post by Bachstelze on 2011-09-19
Read the protocol specifications. It's somewhere in there. :)

---

### Post by haqking on 2011-09-19
Imagine an envelope addressed to you thats been divided iup into say a grid of 100 pieces, each piece in the grid is numbered and cut out of the orignal, then its jumbled all up and randomly divided amongst your friends who will each at there own disgression return a piece to you.  Eventually you will have all the pieces and using the numbers put it back together again into the letter addressed to you.

wow reading back that sounds really cheesy and simple.

But it is really kind of ;-)....thats the best way i could think of how to describe it

---

### Post by jobsonandrew on 2011-09-19
Thanks for the example, I see what you're saying, but:

all those friends would need a common method of numbering the 100 pieces.. how would you decide on that?

:)

---

### Post by haqking on 2011-09-19
> **jobsonandrew said:**
> Thanks for the example, I see what you're saying, but:

all those friends would need a common method of numbering the 100 pieces.. how would you decide on that?

:)

The torrent protocol
[http://jonas.nitro.dk/bittorrent/bittorrent-rfc.html](http://jonas.nitro.dk/bittorrent/bittorrent-rfc.html)

overview of torrent

[http://en.wikipedia.org/wiki/BitTorrent_%28protocol%29]("http://en.wikipedia.org/wiki/BitTorrent_%28protocol%29")

peer 2 peer RFC
[http://tools.ietf.org/html/rfc5694](http://tools.ietf.org/html/rfc5694)

---

### Post by ofnuts on 2011-09-19
> **jobsonandrew said:**
> Thanks for the example, I see what you're saying, but:

all those friends would need a common method of numbering the 100 pieces.. how would you decide on that?

:)In the case of a file, that would be a matter of sending the offset in the original file of the piece they send. The tough part is to avoid having several of your friends sending you the same part of the file, if *they* decide which part they send you (its definitely easier if *you* decide which part a friend sends you).

---


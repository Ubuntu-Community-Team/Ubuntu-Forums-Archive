---
title: "torrent client with custom chunk selector"
date: 2011-06-05
forum: Programming Talk
---

### Post by miak on 2011-06-05
Hi,

I want to modify a chunk selector of some torrent client to download the torrent from start to end. This is very helpful when downloading movies, you can basically stream the movies.
I was wondering if anyone can help me with selecting a torrent client which would be easy to modify and has documentation.
I was thinking about ktorrent or rtorrent, but I can't seem to be able to find a documentation.
Any ideas?

Thanks,
miak

---

### Post by pyroscope on 2011-06-06
rTorrent had automatic priority for the first / last chunk on certain file types recently added. I guess you could modify it to do that for all chunks in sequence, though that's not good for swarm healthiness.

---

### Post by SledgeHammer_999 on 2011-06-06
> **miak said:**
> I was wondering if anyone can help me with selecting a torrent client which would be easy to modify and has documentation.

And what programming languages do you know or prefer coding to?

---


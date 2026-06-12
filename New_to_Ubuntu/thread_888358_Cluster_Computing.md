---
title: "Cluster Computing"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by AngryNapkin on 2008-08-13
If one had a few old desktops lying around what would they use clustering for? Encoding? Would it increase responsiveness on the host pc? Gaming? Rendering? This is a new concept to me and I didn't realize how accessible  it was until I switched to Linux. So, what are the practical applications of cluster computing?

---

### Post by ds[de] on 2008-08-13
Well, generelly Cluster Computing can be used for any task that desires a lot of computing power.

Think about SETI@Home for example ([http://setiathome.ssl.berkeley.edu/](http://setiathome.ssl.berkeley.edu/)).
By distributing the calculations to hundreds of thousands of computers, calculation can basically be done a *lot* quicker. 

From wikipedia:
> Clusters are usually deployed to improve performance and/or availability over that provided by a single computer, while typically being much more cost-effective than single computers of comparable speed or availability.

[http://en.wikipedia.org/wiki/Computer_cluster](http://en.wikipedia.org/wiki/Computer_cluster)


Regards,
ds[de]

---

### Post by mcduck on 2008-08-13
For encoding & rendering, yes, but definitely not for gaming. The communication between different computers would be too slow, causing too much lag to get any benefits from the increased computing power.

Generally clustering can be used for any tasks that require lots of computing power, and that can be divided into many small pieces that can be sent to individual computers for processing.

So, for example, clustering wouldn't help in encoding a single audio file, but when encoding a full album all the songs could be sent to different machines for encoding.

---

### Post by Cadmus on 2008-08-13
> **mcduck said:**
> So, for example, clustering wouldn't help in encoding a single audio file, but when encoding a full album all the songs could be sent to different machines for encoding.

Thinking about it, if you had a video codec which had trivial concatenation of files (no re-encoding) and you need to encode 2 hours of footage could you not send 30 minutes to each of 4 machines and just concatenate them later?

Of course I don't know any codecs where concatenation is trivial :)

---

### Post by mcduck on 2008-08-13
Well, if there was such a codec then of course that would be possible..

But for example games wouldn't work, as you wouldn't know what's going to happen in the next frame, you'd have to wait and see what the player does before you could send the data to the cluster, through very slow network connection (at least very slow compared to data connections inside one computer). The lag caused by sending data to- and from cluster nodes would be simply horrible. Same applies to most of the normal desktop use.

---


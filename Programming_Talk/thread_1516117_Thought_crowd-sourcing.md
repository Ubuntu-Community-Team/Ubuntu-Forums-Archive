---
title: "Thought crowd-sourcing"
date: 2010-06-23
forum: Programming Talk
---

### Post by DanielWaterworth on 2010-06-23
Does anyone have any idea how this works: [http://www.youtube.com/watch?v=Q-ATtrImCx4](http://www.youtube.com/watch?v=Q-ATtrImCx4) ? (provided it's real). It looks like they're storing points in an exotic data structure that allows constant-time lookup for finding the closest point to a line. Can anyone think of a data structure that could do this? I think it's a hash table with some sort of locality sensitive hash, but what hash function could do that?

---

### Post by Reiger on 2010-06-23
Any linked list can do that if you define order in terms of distance to the given line: that way it is simply a matter of picking the first element. ;)

---

### Post by DanielWaterworth on 2010-06-23
Yes, but for an arbitrary line, you'd have to re-make the list for each lookup which is O(n). Also, for a perspective view the lines aren't parallel.

---

### Post by Reiger on 2010-06-23
Not if you keep track of (store) the distance calculated. Anyway since the data has a clearly defined order anyway; you could do this in a binary search tree or similar structure, too.

---

### Post by DanielWaterworth on 2010-06-23
I know you could do it in O(n log n) with a BSP tree, I'm trying to figure out how to do it in O(1).

---

### Post by DanielWaterworth on 2010-06-23
You could store the points in lots of Quad-trees ordered by 2D projection and interpolate to find distances and hence the nearest. i.e. rotate the points around the centre in many different configurations then take projections orthographically to give you 2D points. And make a Quad-tree for each projection. This would give you O(log n) lookup, but it's O(n log n) insertion/deletion. It's also not very storage efficient.

---

### Post by DanielWaterworth on 2010-06-24
Instead you could store spatial hash-maps of a few projections (less than 20). Where the bucket size is adapted so that there's some constant number of points in each bucket. If there was a quick way to find the nearest point to an arbitrary point in an interpolated projection then this would fill the criteria of constant or near constant time. Insertion/deletion is constant time unless the bucket size has to change in which case it's linear, but crucially moving points is constant time.

One more problem to overcome, if I can work around it then I'll write and share a python script to demonstrate it.

---


---
title: "Uniquely identify files"
date: 2008-05-19
forum: Programming Talk
---

### Post by Xyem on 2008-05-19
I would like to identify files by only their content. This is so a file manager ( of sorts ) that I am writing will be able to retain information about files regardless of what system I am accessing them from.

I imagine that a hash of the file is the best bet, but I am worried about collisions and also the time it would take to hash a large file ( and therefore, retrieve the information for it ).

Does anyone have any suggestions or advice about doing this?

---

### Post by slavik on 2008-05-19
I wouldn't worry about hash collisions, especially when working with something like SHA-1 (SHA-2 start at 256 bit length and can be as big as 1K or bigger).

SHA-1 is 160 bits long, meaning there are 2^160 different hashes. Unless you are hashing at least more than half of that number, I wouldn't worry about collisions (if you do find any though, many people will be interested in the two files).

---

### Post by Xyem on 2008-05-19
I'll make sure if I come across any, I'll post them some-place.

It does appear I didn't think this through very thoroughly anyway. I wanted to be able to tag files ( any file ) with information but if the file ever changed, it would become disassociated from the data held the file manager ( if linked by content/hash ). For some reason, this hadn't actually occurred to me until just now :(

I would imagine the sort of thing I am looking to do would have to be handled at the file-system level.. guess I'll have to stick to making an image/story/video tagging system [ written in Perl and Tcl/Tk ] :)

Thanks for the input!

---


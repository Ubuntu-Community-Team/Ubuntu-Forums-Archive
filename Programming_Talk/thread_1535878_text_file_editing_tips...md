---
title: "text file editing tips.."
date: 2010-07-21
forum: Programming Talk
---

### Post by rockom on 2010-07-21
Hello,

Generally, I'm either read only, or appending to the end of a file.  No problems with that.
My latest task is to edit a file.
I have a steam position saved from a previous read operation.  I use fsetpos() to position the file pointer for the write.  Works great with one exception.  It does not delete the line first, so if my new line is shorter than whats already in the file, I get some leftovers.

I'd appreciate some tips on how I might be able to 'edit' the line of a file without reading the entire file into an array and re-writing it.

I'm using C, not C++.
Standard libraries.

Thanks,
-Rocko

---

### Post by trent.josephsen on 2010-07-21
Most editors don't edit a file in-place; instead, they make a modified copy.  Many tools also use the technique of saving the original to disk with a special suffix or prefix (~ and.bak are common).

Since a file is typically stored as a single long sequence of bytes (I have heard tell of obscure and bizarre file systems that do not do so), there's no good way to delete a string from the middle of a file leaving the rest of the file intact.

---


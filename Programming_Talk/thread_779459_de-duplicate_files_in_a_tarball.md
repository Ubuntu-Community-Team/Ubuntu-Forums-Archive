---
title: "de-duplicate files in a tarball"
date: 2008-05-02
forum: Programming Talk
---

### Post by Daveski on 2008-05-02
I have been looking to find a way to 'deduplicate' files when creating a tarball (although I want the original structure and all duplicated files to be re-created when melted):

[http://ubuntuforums.org/showthread.php?t=777232](http://ubuntuforums.org/showthread.php?t=777232)

A tar file will just be one large data file and so compression systems should use the duplicated data to perform compression, but it seems (zip, 7z etc.) that this works when duplicated chunks are near by, but I am sure that if these large chunks of data are removed first, that the normal compression systems will be more efficient. Does this sound reasonable?

Most of my dupe data is something like 5-10 meg files spread over a number of subdirectories, and the total size of the structure will be a whopping 100Gb or so. (I get this down to 20-50Gb when compressed).

I am toying with the idea of coding something to see if this is the case. I guess I need to work out my own structure, which I guess will preclude using tar - unless anyone can think of a way I can integrate this.

---


---
title: "Multiple Directory Rename"
date: 2007-05-22
forum: Programming Talk
---

### Post by matt95z on 2007-05-22
Thanks in advance for any help.
I am organizing my music collection, and I have sort of a mess.
The music is organized with the artist at the top level of the tree.

The mess comes in with directory names for artists that start with "The".
Some of my directories are "The ARTIST" some are "ARTIST, The".

I would like to make this consistent, there are around 50 or so each way.  The other caveat is I have a couple like this:

Beatles, The
The Beatles

I would like these to consolidate if possible.

I am really having trouble figuring this out.

Any help would be appreciated.

Thanks
Matt

---

### Post by mitch.c on 2007-05-22
I don't know about other music players, but Amarok will do this for you with very little work.

Otherwise, you may have to use something like:
```
# renames 'Beatles, The' to 'The Beatles'
$ rename 's/(.*), (The)/$2 $1/' *
```
But that could get ugly.

Surely some of the GUI file managers (Thunar?) have some sort of batch rename that might help.

-- 
Mitch

---

### Post by matt95z on 2007-05-22
Amarok will do it? I didnt see that feature, any direction on where it is at?

---

### Post by mitch.c on 2007-05-22
From the Collection Browser, right-click an artist, album, or song (or a group of), point to Manage Files, and then click Organize N Files. There are tons of options for renaming folders and songs. You'll have to delete empty folders manually when you are finished.

---


---
title: "GRsync is Not Copying Folder Notes"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Andavane on 2008-07-23
Hello:
I have recently started tagging notes to folders - very useful.
However the notes with the attachment pin are not copying over.
I imagine that this is something to do with ticking the correct option boxes and have attached a picture of my set-up, showing which items are selected:

[image]("http://ubuntuforums.org/album.php?albumid=201&pictureid=1231")

Can someone explain these to me? 

I would like to have this working.

Regards

John

---

### Post by forger on 2008-07-23
Welcome to the wonderful world of manuals :)
grsync is based on rsync, the command used in a terminal/console. You can read the manual here:
[http://samba.anu.edu.au/ftp/rsync/rsync.html](http://samba.anu.edu.au/ftp/rsync/rsync.html)

What you need must have something to do with specials attributes (?) such as the following:
>  -l, --links                 copy symlinks as symlinks
 -L, --copy-links            transform symlink into referent file/dir
     --copy-unsafe-links     only "unsafe" symlinks are transformed
     --safe-links            ignore symlinks that point outside the tree
 -k, --copy-dirlinks         transform symlink to dir into referent dir
 -K, --keep-dirlinks         treat symlinked dir on receiver as dir


 -A, --acls                  preserve ACLs (implies -p)
 -X, --xattrs                preserve extended attributes
 -o, --owner                 preserve owner (super-user only)
 -g, --group                 preserve group
     --devices               preserve device files (super-user only)
     --specials              preserve special files
 -D                          same as --devices --specials

..unless nautilus has a configuration file where it saves the notes for each folder.

Experiment a bit with them, let's hope these command line arguments help :)

---

### Post by Andavane on 2008-07-23
> **forger said:**
> Welcome to the wonderful world of manuals :)
grsync is based on rsync, the command used in a terminal/console. You can read the manual here:
[http://samba.anu.edu.au/ftp/rsync/rsync.html](http://samba.anu.edu.au/ftp/rsync/rsync.html)

What you need must have something to do with specials attributes (?) such as the following:

..unless nautilus has a configuration file where it saves the notes for each folder.

Experiment a bit with them, let's hope these command line arguments help :)
I have been experimenting with ticking the boxes options.
Unfortunately I am virtually ignorant re the command line.
So far no luck in being able to copy over the folder as well as the attached notes.
I have tried googling various combination of words:
'grsync copy folder note'
and varied it with 'properties' etc.
Unfortunately so far no luck.
It is obviously a small file whioch is tagged onto the folder, and I really do need to copy this info as it holds the board unique id of a forum I use.

Not sure what to try next...

:-|

Regards

John

---


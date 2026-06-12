---
title: "ln - can you do this in MSDOS?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by cwmoser on 2008-11-20
I am so oriented to Linux that I think in Linux conventions.

In MSDOS, I have a server (Server2003) and I need to link one directory into another directory.  In Linux we use the ln symbolic link command.  Is there an equivalent in MSDOS?

I know in Windows GUI I can create a "shortcut" but that tags a .lnk extension and it won't work for me.  Basically I have a folder with subfolders by year:
2008
2007
2006
2005

I would like to make a folder (2004) on another drive be liked to the above.

Thanks,

Carl

---

### Post by rpainter on 2008-11-20
Will this do what you need?

[http://bluedragon.blog-city.com/symbolic_links_on_windows_why_and_how.htm](http://bluedragon.blog-city.com/symbolic_links_on_windows_why_and_how.htm)

---

### Post by markjensen on 2008-11-20
Not really a Ubuntu question, is this?

But, for what it is worth, DOS cannot.

However, you might mean something like a Windows 2000 command line?   And Windows NT series (at some point I am not sure of exactly) can do something called an "NTFS junction".   Of course, this is filesystem specific, being an NTFS feature, so cannot be done on a FAT filesystem.

[http://en.wikipedia.org/wiki/NTFS_junction_point](http://en.wikipedia.org/wiki/NTFS_junction_point)

Hope that helps.


EDIT: Arrrrgh!  Second poster is first loser :(

---

### Post by cwmoser on 2008-11-21
Thanks.  The Junction.exe command works like Linux's ln command.

Carl

---


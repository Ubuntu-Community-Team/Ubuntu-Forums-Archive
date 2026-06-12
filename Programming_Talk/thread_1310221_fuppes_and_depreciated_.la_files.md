---
title: "fuppes and depreciated .la files"
date: 2009-11-01
forum: Programming Talk
---

### Post by Shhnap on 2009-11-01
I was looking around at fuppes recently and noticed that it was not longer getting any heavy development but I would really like to see it continue. I tried to compile it and got the following error message:

```
/bin/sed: can't read /usr/lib/libogg.la: No such file or directory
libtool: link: `/usr/lib/libogg.la' is not a valid libtool archive
```

When I went looking for the libogg.la file it was indeed missing and I found out why. Debian asked for it to be removed: [http://lists.debian.org/debian-devel/2009/08/msg00783.html](http://lists.debian.org/debian-devel/2009/08/msg00783.html).

So my question is, how do I recompile the project so that it uses the library that debian wants us to use? Is using libtool for this wrong now? I guess I don't really understand what debian intends us to do now that they have started removing all of the .la files from their projects. And help would be appreciated, thanks in advance.

Edit: This was because the package libsimage-dev relied (wrongly) upon libogg.la being present. Removing libsimage-dev fixed the problem but I hope that it is packaged correctly soon as i want fuppes to work fully again.

---


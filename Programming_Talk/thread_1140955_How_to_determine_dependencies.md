---
title: "How to determine dependencies"
date: 2009-04-28
forum: Programming Talk
---

### Post by galileon on 2009-04-28
Dear all,

I'm writing a program to implement arbitrary tagging of files, and search by tags. I'm using python, and a few modules such as sqlite, wxpython, etc.

My desktop has been in use for a few months, and I have lots of development packages installed. What I'm trying to figure out is what packages I need to tell an eventual user to install before they can use my program.

Is there a quick and dirty way of finding this out, or trial and error? Because then, I'd need to perform a clean install (virtual box?), and try the instructions out?

I seem to remember that back in the days they used something of a chroot jail, but I don't have a feeling for the concept, is that useful here?

Thanks for any feedback,

Galileon.

PS: Here's the program I'm writing: [http://galileon.co.uk/pmwiki/pmwiki.php?n=Main.StickerTag](http://galileon.co.uk/pmwiki/pmwiki.php?n=Main.StickerTag)
It wouldn't work out of the box for you, because there's a lot of hard coded paths, I need to fix that eventually.

---

### Post by Zugzwang on 2009-04-28
> **galileon said:**
> I seem to remember that back in the days they used something of a chroot jail, but I don't have a feeling for the concept, is that useful here?


Yes, see here: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete). There's a section about finding out the true prerequisites of your program. More details can be found here: [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto)

---


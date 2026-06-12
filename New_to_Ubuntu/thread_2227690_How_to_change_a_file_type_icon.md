---
title: "How to change a file type icon?"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by Fausto Arinos Barbuto on 2014-06-03
Hi,

Something that always annoyed me is my inability to successfully associate icons to a specific file type.
For example, I want my Fortran files displaying a neat icon like this one here,
not some other vanilla, senseless icon (or, even worse, no icon at all). Needless to say, that will help me
to tell one file type from the others easily on Nautilus, Dolphin, Thunar or any other file manager.

I have tried several approaches but none worked. My last attempt was to follow the recipe in this
page:

[https://help.ubuntu.com/community/AddingMimeTypes](https://help.ubuntu.com/community/AddingMimeTypes)

but it didn't work.

Assogiate never worked for me either. Where am I goofing? Any hints will be much appreciated.

Xubuntu 14.04 64-bit.

Thanks.

---

### Post by tgalati4 on 2014-06-03
I'm running MATE (a gnome2 fork) and mimetype icons are stored here:  /usr/share/icons/mate/32x32/mimetypes

There is no default FORTRAN mimetype, so you would have to research how to add one to this list so that it gets picked up automatically by your filemanager.

Alternatively, you can add emblems to files so that they stand out, but it is not the same as changing the icon.

The link you provided gets you 90% there.  You need to add the pixmap icons as well, since the scaleable icons are only used for some applications.  Most file managers use pixel maps with small, medium, and large icons and they are stored in the directory I referenced above.  You could use the same pixmap for each size, but then they won't scale when you have lots of files  to display.

---

### Post by Fausto Arinos Barbuto on 2014-06-04
> **tgalati4 said:**
> I'm running MATE (a gnome2 fork) and mimetype icons are stored here:  /usr/share/icons/mate/32x32/mimetypes

There is no default FORTRAN mimetype, so you would have to research how to add one to this list so that it gets picked up automatically by your filemanager.

Alternatively, you can add emblems to files so that they stand out, but it is not the same as changing the icon.

The link you provided gets you 90% there.  You need to add the pixmap icons as well, since the scaleable icons are only used for some applications.  Most file managers use pixel maps with small, medium, and large icons and they are stored in the directory I referenced above.  You could use the same pixmap for each size, but then they won't scale when you have lots of files  to display.

Hi,

Many thanks for your reply.  I know that associating icons to file types is a tough issue.

I found a way to circumvent the problem, though: it's Krusader, a file manager for KDE.  It
makes the association easy as it should have always been.  The only drawback is that the
said file manager must be restarted so that the changes can become effective.  Needless
to say, the association works only on Krusader.  On Thunar, Nautilus, etc, all tasteless
icons remain.

Cheers,

Fausto

---

### Post by yanes on 2014-06-14
What about my new tool?
 [Yanes-GMime]("http://yanescodegeek.blogspot.com/2015/03/yanes-gmime-change-your-mimetypes-names.html")
I coded it to avoid headaches of similar icons for diffrent mimes and to make my IDEs projects (usually XML) to be opened with gedit or scite 
It allow you to assign a specific icon, spec. mime type and choose a default app to open your files  to a specific mime type


[Yanes-GMime]("http://yanescodegeek.blogspot.com/2015/03/yanes-gmime-change-your-mimetypes-names.html")
 [ATTACH=CONFIG]253954[/ATTACH]

---


---
title: "Emacs: save position of the cursor and go to it later"
date: 2010-05-10
forum: Programming Talk
---

### Post by miguelastico on 2010-05-10
Hi,
often, when working on a buffer, I need to go to another location, modify the buffer there, and then jump back where I was working. Is there a way to automate the process of marking the place and jumping back?
I know the existence of bookmarks, but it is a little bit too much overhead (setting the name of the bookmark, go and modify, asking to go back to bookmark-name, write something, then setting again another bookmark, and so on...)
The go to line seems to be a better solution, but still too much overhead

I know that some modes, like ebib, go back to where you started the search when it is done, and in my dreams I would like to have a keyboard shortcut for marking the place and one to go back there.

Any suggestion?

---

### Post by jpkotta on 2010-05-11
I use this: [http://www.emacswiki.org/emacs/VisibleBookmarks](http://www.emacswiki.org/emacs/VisibleBookmarks).  I like it because it's simple and gives a visual indicator.

See also: [http://www.emacswiki.org/emacs/BreadcrumbForEmacs](http://www.emacswiki.org/emacs/BreadcrumbForEmacs)

---

### Post by miguelastico on 2010-05-12
Thanks!
I have to admit that breadcrumb looks really nice, but as I wanted something really really simple I went for visible bookmarks and it works like a charm after 15 secs of configuring.

---


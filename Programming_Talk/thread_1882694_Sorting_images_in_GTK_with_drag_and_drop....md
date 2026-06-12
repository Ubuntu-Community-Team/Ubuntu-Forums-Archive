---
title: "Sorting images in GTK with drag and drop..."
date: 2011-11-17
forum: Programming Talk
---

### Post by ragtag on 2011-11-17
****I'm writing a small plug-in for GIMP using PyGTK. The plug-in is a tool for comic book artists that manages multiple pages of a book. It basically shows the thumbnails of all the pages, and you can open them, add pages, delete pages and so on.

What I'm working on now is re-ordering the pages. I want the user to be able to drag and drop pages around in the window, to change their order. The layout of the pages is as follows:
  1
2 3
4 5
6 7
...and so on. Just like it would be in a book. I'm quite new to GTK, so I'm not sure how to approach this. I've looked at using images in a ListView, with two columns. It supports drag and drop, but I believe it's only for whole rows (e.g. I wouldn't be able to move page 5 to where page 2 is in the above example). And if I get drag and drop working, can I make it scroll the window with the thumbnails, if you drag to the edge of it? If multi-select and drag is possible too, that would be great.

What would be a **smart** approach to this**?**

My current idea is just to make it easy for myself, and do a right click menu with "Move page to..." and have the user enter the page number where they want the page to move to. But it's not particularly slick. :)

---

### Post by crdlb on 2011-11-18
By far, the easiest method I can think of is a gtk.IconView. You can set the number of columns to 2, and I guess you could create an dummy first item to make the pages line up. You can even call set_reorderable to get free DnD support, but you'll probably need to implement that manually to prevent dragging that dummy item.

---

### Post by ragtag on 2011-11-19
Thanks, that seems to do the trick. I've implemented an IconView in my code, and got drag and drop working great for reordering the pages.

I don't mind the extra page at the top, I'll just put a file for the cover of the book there. You can still drag it around, but it's not really a problem as I suspect the end user won't accidentally move his or her cover around, and if they do, it's easy to drag it back. :)

---


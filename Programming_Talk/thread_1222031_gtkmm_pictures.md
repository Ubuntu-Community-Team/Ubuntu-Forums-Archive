---
title: "gtkmm pictures"
date: 2009-07-24
forum: Programming Talk
---

### Post by swappo1 on 2009-07-24
Hello,

I am working through the gtkmm tutorials.  In the buttons tutorial it uses a .xpm file for the picture of an open file that is put on the button. Here is the link: [COLOR="Blue"][http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-button-widget.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-button-widget.html)[/COLOR]
The tutorial provides the file.  Where can I get more files like these?  Do they come with gtkmm?  I quickly looked on my HD but couldn't find anything.  Thanks.

---

### Post by kknd on 2009-07-24
Have you considered using stock icons? They use the current theme icons, or a default set as fallback (i.e: works on Windows too)

You can easily build buttons with the default icons. In the gtk{mm}-demo there's a stock icon browser.

P.S: in the original API, you can build a "stock button" with: gtk_button_new_from_stock("gtk-open"), for example.

---


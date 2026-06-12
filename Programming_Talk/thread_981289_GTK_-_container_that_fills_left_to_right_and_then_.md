---
title: "GTK - container that fills left to right and then top to bottom"
date: 2008-11-13
forum: Programming Talk
---

### Post by Tony Flury on 2008-11-13
I am writing an image browser using Python, and what i would like to develop is a gui which will display a series of thumbnails.

I want the thumbnails to fill the designated areas left to right, and then when it is full horizontally i would like to fill the next row, using scrollbars to be able to move vertical through the set of displayed thumbnails when neccessary

In theory I could do this with a Table, but what i would really like to do is to be able to resize the thumbnail area refills as the window resizes, always refilling left to right and then top to bottom - to do that in a table would be nightmarish i think, as each window resize i would need to explicitly resize and refill the table - is there an easier way ?

---

### Post by days_of_ruin on 2008-11-13
[Use an IconView]("http://www.pygtk.org/docs/pygtk/class-gtkiconview.html")

---

### Post by Tony Flury on 2008-11-13
Ignore that :-)

---

### Post by Tony Flury on 2008-11-13
ok - so i have an icon view - i can post the code if neccessary, although my python is not the best :-)

When i create the window it displays two columns of thumbnails, and i can resize the window vertically to my hearts content. However when i expand the window horizontally - so it can display 3 columns of icons - i can't then shrink the window horizontally smaller again.

I don't do anything to set any minimum widths etc - it seems to be the iconview itself that prevents the resizing - anyone else experienced this ?

---

### Post by days_of_ruin on 2008-11-13
```
iconview = gtk.IconView()
iconview.set_columns(-1)
```

I haven't tried this out but the docs say that will make it use
as many columns as possible.

---

### Post by Tony Flury on 2008-11-14
A quick test shows the following 

a) if you turn off the Horizontal Scrollbar :- scroll.set_policy(gtk.POLICY_NEVER, gtk.POLICY_AUTOMATIC) then you can only expand the width, and never shrink it.

b) if you turn on the Horizontal Scrollbar, then you can expand and shrink the window width, but if for instance your icon view is showing 4 columns of icons, and you expand the window so that 5 columns are displayed, if you then shrink the window again it still shows 5 columns - even if now the there is only screen space for 4, and the horizontal scrollbar appears.

---


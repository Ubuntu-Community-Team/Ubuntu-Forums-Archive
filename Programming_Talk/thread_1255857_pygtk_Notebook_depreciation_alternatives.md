---
title: "pygtk Notebook depreciation alternatives"
date: 2009-09-02
forum: Programming Talk
---

### Post by slumbergod on 2009-09-02
Hi all,

I have some tabs in a notebook. I have them positioned on the left hand side of the notebook. The labels are rotated so they read vertically. I want to expand them so that the three tabs take up the full height of the notebook with vertical text.

My problem is that the set_tab_vborder is being depreciated and I cannot seem to work out how to achieve the same visual appearance without it. 

For months I have kept coming back to this trying to find an alternative. I haven't managed to do it myself nor find an example online. The pygtk documentation is out-of-date so that hasn't helped much either. Has anyone got an insight into how it can be achieved?

notebookExample.set_tab_pos(gtk.POS_LEFT)      
notebookExample.set_tab_vborder(15) # depreciated
exPage1 = gtk.Frame("p 1")
exPage2 = gtk.Frame("p 2")
exPage3 = gtk.Frame("p 3")
tabLabel1 = gtk.Label("tab 1")
tabLabel1.set_angle(90)
tabLabel2 = gtk.Label("tab 2")
tabLabel2.set_angle(90)
tabLabel3 = gtk.Label("tab 3")
tabLabel3.set_angle(90)
notebookExample.append_page(exPage1, tabLabel1)
notebookExample.append_page(exPage2, tabLabel2)
notebookExample.append_page(exPage3, tabLabel3)

---


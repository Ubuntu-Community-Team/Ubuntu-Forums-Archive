---
title: "A menubar inside a notebook?"
date: 2010-05-31
forum: Programming Talk
---

### Post by Axolotl9250 on 2010-05-31
Hi there, I'm building an app which I'm hoping is a joint effort between my uni stats lecturer and some students, anyway I made a start making a frame, and inside that is a notebook, and I want 4 or 5 tabs in it. (I'm making this in Boa Constructor). I've been trying to get a menubar inside the top of each tab of the notebook, as each tab will be for different things, like writing R, or a GUI with buttons for R. and I would like each section to have it's own menu bar. Is this possible or can they only be put on frames? I've been trying for the past hour but with no luck. (I don't necessarily need to know how to do it in Boa, just that it can be done code or otherwise would be a big help). Thanks.

---

### Post by soltanis on 2010-05-31
So you're using wxPython (that's what Boa Constructor is for). I don't know of any method to implement the standard menu bar under anything except a wxFrame, although you could try to use this method:

```

class TabWidget(...):
    # .. initialize other things
    menubar = wx.MenuBar()
    menu1 = wx.Menu()
    menu1.Append(wx.ID_ANY, "item1")
    # .. menu building
    # now you would set the menu bar by using this method:
    self.SetMenuBar(menubar)

```

SetMenuBar sets the menu bar on a widget. Like I said, I've only used it on wxFrame's and not anything else, so there is a good chance most widgets do not support this.

---


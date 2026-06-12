---
title: "Complicated filtered lists (python)"
date: 2008-04-01
forum: Programming Talk
---

### Post by aquavitae on 2008-04-01
I need to create a list class for which each instance returns different items depending on who's requesting it. The structure is something like this:
[php]
class section:
  def __init__(self):
    self.items= []
  #also iterator and access functions

class Master:
  def __init__(self):
    self.sections = [] # list of sections
  def itersections...
  def iteritems... # iterate over all items

master = Master()

class Subset:
  def __init__(self):
    self.master = master
    self.filtersections = fromkeys(master.itersections, True)
    self.filteritems = fromkeys(master.iteritems, True)
[/php]
The first part is easy, I can create a list class which is linked to Master.sections and Subset.filtersections and calls filter() every time __getitem__ is called.  The second part is to do something similar so that a section requested by Subset will only return the filtered items.

Any suggestions as to how I do this?

---


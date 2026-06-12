---
title: "[wxPython] ListCtrl - Retrieving text from columns"
date: 2010-04-20
forum: Programming Talk
---

### Post by dodle on 2010-04-20
I've been having trouble with this one for a while.  I've looked through the [wxPython](http://www.wxpython.org/docs/api/wx-module.html) and [wxWidgets](http://docs.wxwidgets.org/stable/wx_classref.html#classref) reference libraries.  And I haven't been able to find a tutorial that shows how to do it.  I've even looked at the lib.mixins.listctrl module.  

Here's some sample code related to my problem:
[php]# Create a list of people and their ages
self.people = {"Tom": "26", "Sue": "23", "Al": "49", "Alice": "18"}

# Create area to display names and ages
self.mylist = wx.ListCtrl(self, -1, style=wx.LC_REPORT)
self.mylist.InsertColumn(0, "Name", width=150)
self.mylist.InsertColumn(1, "Age", width=150)

# Add names and ages to display area
for person in self.people:
    self.mylist.InsertStringItem(0, person)  #Adds name to column 1
    self.mylist.SetStringItem(0, 1, self.people[person]) #Adds age to column 2[/php]

I can extract a person's name from the list using the following method:
[php]name = self.mylist.GetItemText(0) #Retrieves the name of the first person on the list[/php]But this only retrieves information from the first column.  I have not been able to find any documentation on how to extract the person's age from the second column.  Is there a way to do this?

---

### Post by phrostbyte on 2010-04-20
The parameter to *GetItemText* is the indexed row of the first column?

---

### Post by phrostbyte on 2010-04-20
This post might be interesting to you:
[http://programming.itags.org/python/101160/](http://programming.itags.org/python/101160/)

---

### Post by dodle on 2010-04-20
Ok, I'm going to assume that GetItem() returns a wx.ListItem.  I'll look through the reference some more and see what I can find.  Thanks.

---

### Post by dodle on 2010-04-20
Thanks Phrostbyte, you pointed me in the right direction.  The answer is to get the item first, specifying the row and col, then retrieving the text from it.

So if I wanted to get the age of the first person on the list I would do this:[php]item = self.mylist.GetItem(0, 1) #GetItem(row, col)
age = item.GetText()[/php]Thanks again, very helpful.

Now that I look at the wxPython docs, it does say "GetItem(self, itemId, col)".  That should have been my first hint, but I guess "itemId" threw me off.

---


---
title: "[wx/wxPython] ListCtrl Meta Data"
date: 2010-07-15
forum: Programming Talk
---

### Post by dodle on 2010-07-15
Isn't there a way to set meta data in a wxListCtrl, data that I can access without it actually displaying on the screen?  I thought I read somewhere that I could do this, but I cannot find it.  

For example, I want to store the string path "/home/user/myfile.txt".  But I only want "myfile.txt" to show up in the listctrl.

---

### Post by robots.jpg on 2010-07-15
It sounds like you're looking for wx.ListCtrl.SetItemData / GetItemData.

Edit: I forgot, you'll probably have to create a separate dictionary along with the listctrl to store the strings.  I think it's limited to values of type long.

---

### Post by dodle on 2010-07-15
Yes, you're right.  I could only set the data to type long.  Though I decided to use a different method; I created a list and accessed it by the wxListCtrl indexes.

So the python code looks something like this:
[php]list = wx.ListCtrl(self, -1) # a list to show some files
list.InsertColumn(0, "Data")
list_data = [] # a list where the real paths to the files are stored
...
...
for path in paths:
    list_data.insert(0, path) # insert the actual path into the meta data
    list.Insert(0, os.path.split(path)[1]) # insert just the filename into the listctrl[/php]

---


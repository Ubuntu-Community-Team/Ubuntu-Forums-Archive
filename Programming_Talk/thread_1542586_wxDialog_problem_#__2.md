---
title: "wxDialog problem #  2"
date: 2010-07-30
forum: Programming Talk
---

### Post by Eremis on 2010-07-30
Hi,

I asked a question earlier about a custom dialog problem I had, and I was sure I had it all down, but I still cant figure out how to know which button the user pressed (ok, or close)

Here is the code from the method that calls "Add Movie Dialog"(My custom dialog)
```

dlg = AddMovie(self, wx.ID_ANY, 'Add Movie')
        action = dlg.ShowModal()
        # This does not work, even when OK is pressed...
        if action == wx.ID_OK:
            movie = dlg.GetResponce()
            self.movies.Append(movie)
            self.LoadList()
        dlg.Destroy()

```

Code from the custom dialog:

```

class AddMovie(wx.Dialog):
    def __init__(self, parent, id, title):
        wx.Dialog.__init__(self, parent, id, title = 'Add Movie', size=(300, 180))
        
        wx.StaticText(self, -1, 'ID: ', (10, 10))
        wx.StaticText(self, -1, 'Name: ', (10, 40))
        wx.StaticText(self, -1, 'Genre: ', (10, 70))
        
        self.idBox = wx.TextCtrl(self, id = -1, pos = (60, 10), size = (100, 20))
        self.nameBox = wx.TextCtrl(self, id = -1, pos = (60, 40), size = (200, 20))
        
        genres = ['action', 'comedy', 'drama', 'history', 'horror', 'musical', 'science fiction', 'war', 'westerns']
        self.genresCombo = wx.ComboBox(self, id = -1, pos = (60, 70), choices = genres, style = wx.CB_SORT)
        self.genresCombo.SetEditable(editable = False)
        self.genresCombo.SetValue(genres[0])
        
        self.okButton = wx.Button(self, id = wx.ID_OK, label = 'OK', pos = (110, 120))
        
        # Event Bindigs
        self.Bind(wx.EVT_BUTTON, self.OnOk, id = wx.ID_OK)
        
    def GetResponce(self):
        return tools.Movie(self.idBox.GetValue(), self.nameBox.GetValue(), self.genresCombo.GetValue())
        
    def OnOk (self, event):
        self.Close(True)
        
    def OnClose(self, event):
        self.Close(True)

```

How can I figure out which, button does the user press???

---

### Post by robots.jpg on 2010-08-05
Late reply here, but in case you're still stuck, it should work if you just remove the event binding and handler function for the OK button.  The stock button will take care of it.  

If you still want to handle the event yourself, have it close the dialog with self.EndModal(wx.ID_OK) instead of self.Close().

---


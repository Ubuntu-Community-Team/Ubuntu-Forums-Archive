---
title: "wxPython dialog problem"
date: 2010-07-30
forum: Programming Talk
---

### Post by Eremis on 2010-07-30
Hi everybody, 

I am working on a "Movie Catalog" program in python, and I am using wxPython toolkit for the gui. I stumbled upon a problem that I cant fix and need your help... 

My goal is to have a "Add movie dialog" that will ask for 3 things: movie id, movie name, and movie genre. 

movie id --> text box (wx.TextCtrl)
movie name --> text box (wx.TextCtrl)
movie genre --> combo box (wx.ComboBox)

I have several problems that I need fixing, which are:

1. Why cant i click and type on the text boxes? (I can only use TAB to go from one to the other)
2. The combo box does not show up
3. The button does not show up 
4. What will I have to override so when i click OK the dialog returns a "movie"(class that I have created, which has all 3 of the variables...)

My code for AddMovie dialog only:

```

class AddMovie(wx.Dialog):
    def __init__(self, parent, id, title):
        wx.Dialog.__init__(self, parent, id, title = 'Add Movie', size=(300, 200))
        
        wx.StaticText(self, -1, 'ID: ', (10, 10), size = (250, 230))
        wx.StaticText(self, -1, 'Name: ', (10, 40), size = (250, 230))
        wx.StaticText(self, -1, 'Genre: ', (10, 70), size = (250, 230))
        
        self.idBox = wx.TextCtrl(self, id = -1, pos = (60, 10), size = (100, 20))
        self.nameBox = wx.TextCtrl(self, id = -1, pos = (60, 40), size = (200, 20))
        
        # Does not show
        genres = ['action', 'comedy', 'drama', 'history', 'horror', 'musical', 'science fiction', 'war', 'westerns']
        self.genresCombo = wx.ComboBox(self, id = -1, pos = (60, 70), choices = genres)
        
        # Does not show eather...
        self.okButton = wx.Button(self, 1, 'Ok', pos = (80, 100))
        
        self.ShowModal()
        self.Destroy()
        
    def OnClose(self, event):
        self.Close(True)

```

Can anyone help me?

Thanks...

---

### Post by robots.jpg on 2010-07-30
> **Eremis said:**
> 
1. Why cant i click and type on the text boxes? (I can only use TAB to go from one to the other)
2. The combo box does not show up
3. The button does not show up 

Your StaticText widgets are huge, and overlapping everything else in the dialog.  Try removing the size argument for a temporary fix, and consider using sizers to control the layout instead of static coordinates.

> 
4. What will I have to override so when i click OK the dialog returns a "movie"(class that I have created, which has all 3 of the variables...)
As long as you're inherting wx.Dialog, the easiest way is probably to define a function within the AddMovie class that returns your movie class.  Something you could call like this (quick example):

```

dialog = AddMovie(self, wx.ID_ANY, "Movie")
action = dialog.ShowModal()
response = dialog.GetResponse()
dialog.Destroy()

```The variable 'action' would tell you how the form was closed (wx.ID_OK or whatever), and 'response' would contain the entered information.  That way you can still handle things differently if the user cancels the dialog.

---

### Post by Eremis on 2010-07-30
That fixed it!

Thank you so much, I dont know why I used such big size parameters myself...
(I think I copied it from a tutorial on wxPython...)

Anyway again, thanks for the help!

---


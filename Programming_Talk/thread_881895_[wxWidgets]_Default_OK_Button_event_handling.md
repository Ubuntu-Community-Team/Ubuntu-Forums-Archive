---
title: "[wxWidgets] Default OK Button event handling"
date: 2008-08-06
forum: Programming Talk
---

### Post by era86 on 2008-08-06
So I declare a button with the wxID_OK argument to create a deafult OK button on my dialog.  Now, before I return to the parent window, I want to check some variables and do some tasks.  What function can I modify to do this?

Any help appreciated.  Thanks

---

### Post by y-lee on 2008-08-06
Whatever function you have binded to that button

For example in some code I wrote:

```
wx.Button(self, 1, 'Ok', (92, 230), (60, -1))
       
self.Bind(wx.EVT_BUTTON, self.OnClose, id=1)
```

and in the OnClose method

```
def OnClose(self, event):
        self.parent.view['Center']['ink'] = self.center_ink_choice.GetStringSelection()
        self.parent.view['Vertices']['ink'] = self.vert_ink_choice.GetStringSelection()
        self.parent.view['Sides']['ink'] = self.sides_ink_choice.GetStringSelection()
        self.parent.view['Diagonals']['ink'] = self.diag_ink_choice.GetStringSelection()
        # bunch more of the same
        self.Close()
```

---


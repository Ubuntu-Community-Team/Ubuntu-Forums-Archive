---
title: "wxPython, Layout problem and sizers."
date: 2011-01-03
forum: Programming Talk
---

### Post by cgroza on 2011-01-03
Hello everyone.
I am working on a text editor right now wich I am planning to use as my IDE.

First, I create a Frame, then a panel in wich I put an Aui notebook, then I put a panel into the Aui tab.
In that panel I have a StyledTextCtrl, some buttons and thats it. Now I want to add a Source Browser on the left. I got the TreeCtrl and everthing but I can't add it proprely on the left. It shows up there but it covers a part of my STC: the line numbers and fold guides.

I am stuck and I tried everything. Maybe someone can suggest me how to fix it because I have almost 0 knowledge about sizers and all that. Here is my sizer code:


```

        button_sizer = wx.BoxSizer(wx.HORIZONTAL)
        button_sizer.Add(self.NewButton, 0)
        button_sizer.Add(self.OpenButton, 0)
        button_sizer.Add(self.SaveButton, 0)
        button_sizer.Add(self.SaveAsButton, 0)
        button_sizer.Add(self.ConfigButton, 0)
        button_sizer.Add(self.QuitButton, 0)
        button_sizer.Add(self.CloseTab, 0)
        button_sizer.Add(FontChoice, 0)
        button_sizer.Add(FontSizeChoice, 0)
        # Vertical sizer for the button sizer and text
        main_sizer = wx.BoxSizer(wx.VERTICAL)
        main_sizer.Add(button_sizer, 0, wx.EXPAND)
        main_sizer.Add(self.TextWidget, 1, wx.EXPAND)

        main_sizer.Add(src_br_panel, wx.EXPAND|wx.ALL, 3)  #THE SOURCE BROWSE PANEL
        # Assign the sizer to the panel, and resize it
        panel.SetSizer(main_sizer)
        main_sizer.Fit(panel)
```I hope someone could help me because this is the only thing that does not work in my editor. Thank you.

---

### Post by robots.jpg on 2011-01-03
Assuming you want the TreeCtrl to be the same height as the  StyledTextCtrl, just create another horizontal BoxSizer to hold the  two.  Add your TreeCtrl and StyledTextCtrl to the new sizer, and then  add *that* sizer to the main sizer instead of adding the StyledTextCtrl directly.

```

new_sizer = wx.BoxSizer(wx.HORIZONTAL)

new_sizer.Add(self.Tree, 1, wx.EXPAND)
new_sizer.Add(self.TextWidget, 4, wx.EXPAND)

main_sizer.Add(button_sizer, 0, wx.EXPAND)
main_sizer.Add(new_sizer, 1, wx.EXPAND)

```See the attachment in case it helps you understand what's happening there.  It's all just boxes within boxes.

If you wanted the TreeCtrl to be the full height of the panel, and the button sizer to match the width of the text area, you would make your main_sizer wx.HORIZONTAL, create a wx.VERTICAL to hold the button_sizer and text area, and then add the TreeCtrl and vertical sizer to the main_sizer with whatever proportions you want.

---

### Post by cgroza on 2011-01-03
Yes, just like in the image. I will implement your solution. I will post in a few minutes.

---

### Post by cgroza on 2011-01-03
It worked! Thank you very much, I appreciate it. I think I should start learning sizer seriously because I look around and almost every program has a bunch of those.

---


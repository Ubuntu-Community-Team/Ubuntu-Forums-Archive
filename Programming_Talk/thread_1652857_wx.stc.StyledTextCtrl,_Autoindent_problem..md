---
title: "wx.stc.StyledTextCtrl, Autoindent problem."
date: 2010-12-25
forum: Programming Talk
---

### Post by cgroza on 2010-12-25
Hello everyone!
I am trying to implement autoindenting with this piece of code:

```
 
   def AutoIdent(self,event,text_id):
        key = event.GetKeyCode()
        CurrentWidget = wx.FindWindowById(text_id)
        if key == wx.WXK_NUMPAD_ENTER or key == wx.WXK_RETURN:
            if CurrentWidget.GetCharAt(CurrentWidget.GetCurrentPos()-1) == 58:
                line = CurrentWidget.GetCurrentLine()+1
                CurrentWidget.SetLineIndentation(line, CurrentWidget.GetLineIndentation(line)+CurrentWidget.GetTabWidth())
        event.Skip()
```
I bind it with an EVT_KEY_DOWN event, but every time the wrong line gets indented.
Someone on an IRC chanel suggested:

> If you catch the enter event *before* wxSTC received it, the new line doesn't exist and of course you can't indent a line that doesn't yet exist

I tried to manipulate the line address in every way I could but every time an other line gets indented. Maybe someone is patient enough to help me?

---

### Post by cgroza on 2010-12-26
Ok guys, I solved id. Instead of binding to the EVT_KEY_DOWN, I binded to EVT_KEY_UP.
Thanks.

---


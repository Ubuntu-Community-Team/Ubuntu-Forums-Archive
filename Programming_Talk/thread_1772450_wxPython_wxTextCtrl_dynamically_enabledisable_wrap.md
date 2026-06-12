---
title: "wxPython wxTextCtrl dynamically enable/disable wrapping"
date: 2011-05-31
forum: Programming Talk
---

### Post by r-senior on 2011-05-31
Does anybody know how to dynamically enable/disable wrapping in a wx.TextCtrl?

I have this triggered from a check menu item ...

```

    def on_wrap_toggle(self, event):
        style = self.textctrl.GetDefaultStyle()
        if self.wrapToggle.IsChecked():
            print "Wrap"
            style.SetFlags(wx.TE_BESTWRAP)
        else:
            print "No Wrap"
            style.SetFlags(wx.TE_DONTWRAP)
        self.textctrl.SetDefaultStyle(style)

```

... but it doesn't work. Any ideas? The messages are printing as expected.

---

### Post by r-senior on 2011-06-01
Should anyone be interested in a solution for this, the key is that wxTextCtrl is a subclass of wxWindow. The code I was trying to use sets the default style of the text. The wrapping, i.e. the presence of a horizontal scrollbar is controlled by the style of the wxTextCtrl itself through methods inherited from wxWindow.

Care is needed in preserving the existing flags and, because the wrap/don't wrap settings are different constants, the "old" flag needs to be unset before the new one is set. As far as I can tell without more detailed documentation anyway - it didn't work both ways without doing so.

Anyway, not the most elegant piece of code ever written but this seems to do the trick:

```

    def set_wrapping(self, switch_on):
        '''Turn wrapping on or off in the text control'''
        ws = self.textctrl.GetWindowStyle()
        if switch_on:
            self.textctrl.SetWindowStyle(ws & ~wx.TE_DONTWRAP | wx.TE_BESTWRAP)
        else:
            self.textctrl.SetWindowStyle(ws & ~wx.TE_BESTWRAP | wx.TE_DONTWRAP)

```

Note that TE_BESTWRAP is not the only constant that means wrapping is on. If the control was created with TE_CHARWRAP for example, you'd presumably need to turn that off before switching TE_DONTWRAP on.

---


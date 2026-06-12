---
title: "[wx] Get Left or Right Shift/Alt/Ctrl Key Press"
date: 2011-08-28
forum: Programming Talk
---

### Post by dodle on 2011-08-28
Can wx differentiate between left and right Shift/Alt/Ctrl key presses? I thought there was a way, but maybe I'm wrong. Both left and right key presses produce the same key code. For example left and right Shift both produce 306.

```
int OnKeyDown(wxKeyEvent &event)
{
    cout << event.GetKeyCode() << endl;
}
```

```
def OnKeyDown(self, event)
    print event.GetKeyCode()
```

---

### Post by cgroza on 2011-08-28
Could you tell us what are you trying to accomplish?

---

### Post by dodle on 2011-08-28
Mapping keys for game controls.

**----- EDIT -----**
[quote="RainRat"]You can use wxKeyEvent::GetRawKeyCode or wxKeyEvent::GetRawKeyFlags, but these are platform specific. See [wxKeyEvent](http://docs.wxwidgets.org/trunk/classwx_key_event.html).[/quote]

---


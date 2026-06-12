---
title: "Triggering actions from dialog(1)?"
date: 2013-05-09
forum: Programming Talk
---

### Post by azzamite on 2013-05-09
Hello guys

Is it possible to trigger actions while making choices in dialog(1)?

For example, given a list, show a textbox when an item is chosen:

```
[ ] I had a drink
[ ] I ate international food
```

Choose I had a drink and show a textbox below it, at the side, a popup, or whatever.
```
[x] I had a drink
/----------------------\
| Describe your       |
| drink                 |
\----------------------/
[ ] I ate international food
```

Notice that I'd like to show the dialog *before* typing accept so we can easily show/hide dialogs.

Cheers

---


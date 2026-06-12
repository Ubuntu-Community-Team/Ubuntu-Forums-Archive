---
title: "Python &amp; glade: Statusbars"
date: 2009-11-06
forum: Programming Talk
---

### Post by Kruptein on 2009-11-06
I'm trying to get a statusbar to work..

I used glade to insert a statusbar into my gui,
it asks how many items I want to let the statusbar have. I say 2

but now everytime I change the statusbar text it always change the first item, never the second

```

def some_function(self):
    self.changestatus(1,"New game started")
    self.changestatus(2,"Turn: Player1")

def changestatus(self, number, text):
    self.wTree.get_widget("status").push(number,text)
```

How can I change the text of both items?

---


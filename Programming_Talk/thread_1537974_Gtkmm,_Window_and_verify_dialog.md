---
title: "Gtkmm, Window and verify dialog"
date: 2010-07-24
forum: Programming Talk
---

### Post by martingt89 on 2010-07-24
Hi. I make easy program in c++ and gtkmm. 
My problem:
If I click to X button in the window, window hide. But I need window not hide and show Dialog.
```

window->signal_hide().connect( sigc::mem_fun(*this, &Win::exit) );
.
.
.
void Win::exit(){ //window is hide
...
    dialog->show();
   int res = dialog->run();
...
}

```
Thx.

---


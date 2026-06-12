---
title: "function run one time at moment in python"
date: 2011-02-19
forum: Programming Talk
---

### Post by #Alwan on 2011-02-19
hi

I am using PYGTK, how I  make specific function run one time at moment if users try to run it again nothing happen.  The function like setting window so I don't user open many window by mistake.

can you help me?

---

### Post by slooksterpsv on 2011-02-19
> **#Alwan said:**
> hi

I am using PYGTK, how I  make specific function run one time at moment if users try to run it again nothing happen.  The function like setting window so I don't user open many window by mistake.

can you help me?

Do you mean like:

```

....
run_f1 = 0
....

def func1():
 if run_f1 != 1:
  do_some_stuff()
  run_f1 = 1
 else
  pass

```

---

### Post by #Alwan on 2011-02-20
thanks for response
i will try to explain more.

this is example ,  if you clicked the button there are another window show up and if you clicked the button multiple time there multiple window , i want one window show up only even when you clicked many times.
```
import gtk

def main() :
    window = gtk.Window()
    window.set_size_request(200,80)
    button = gtk.Button("Click")
    button.connect("clicked",anotherwindow)
    window.add(button)
    window.show_all()
    gtk.main()
    
def anotherwindow(*args):
    window = gtk.Window()
    window.show()

main()
```

---


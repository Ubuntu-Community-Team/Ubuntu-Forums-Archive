---
title: "Python multithreading"
date: 2014-04-09
forum: Programming Talk
---

### Post by brian8765 on 2014-04-09
Hi Can someone tell me why this python code is not working. Its supposed to be a counter thing, very simple.
Many Thanks

```
from Tkinter import *
from thread import *
from time import sleep

count=0

def docount():
    global count
    global label
    while 1:
        sleep(1)
        count+=1
        label.config(text=str(count))
        

root=Tk()
label=Label(root,text="0")
label.pack()
start_new_thread(docount())
button=Button(root,text="Close",command=root.destroy)
button.pack()
root.mainloop()



```

---

### Post by ofnuts on 2014-04-10
Not a Tk expert, but in all the GUI frameworks I have used, you cannot really update the GUI from any thread other than the one running the "event loop". But there are usually mechanisms to let the side threads signal things to the event loop one. Google for "tkinter multithreading".

---

### Post by brian8765 on 2014-04-15
Thanks for that ofnuts.

---


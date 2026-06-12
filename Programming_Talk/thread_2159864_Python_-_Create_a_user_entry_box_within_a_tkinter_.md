---
title: "Python - Create a user entry box within a tkinter canvas"
date: 2013-07-04
forum: Programming Talk
---

### Post by OmgItsPixelated on 2013-07-04
Hi there,
I am having some trouble getting a text entry box inside a canvas the code I have is currently giving me this error

```
IndexError: tuple index out of range
```

And the subroutine it occurs in is

```
def gamescreen():    photo = PhotoImage(file="gamescreen.gif")
    canvas.bind("<Button-1>", buttonclick_gamescreen)
    canvas.pack(expand = YES, fill = BOTH)
    canvas.create_image(1, 1, image = photo, anchor = NW)
    game1 = PhotoImage(file="1.gif")
    canvas.create_image(30, 65, image = game1, anchor = NW)
    e1 = Entry(canvas)
    e2 = Entry(canvas)
    canvas.create_window(window = e1, x=10, y=10)
    canvas.create_window(window = e2 , x=400, y=10)    
    canvas.update()
    window.mainloop()
```

The full code for my program is here

[http://pastebin.com/vemA7ZU6](http://pastebin.com/vemA7ZU6)

EDIT: Solved it myself.

---


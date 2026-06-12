---
title: "pyglet maximising"
date: 2011-11-04
forum: Programming Talk
---

### Post by gameguy on 2011-11-04
I have a pyglet application that I would like to make fullscreen. This is the (shortened) code for it
```

class Window(pyglet.window.Window):
    def __init__(self):
        # Call the superclass's constructor.
        super(Window, self).__init__()
        self.keys = key.KeyStateHandler()
        self.push_handlers(self.keys)
        pyglet.clock.schedule_interval(self.update, 0.02)
        #self.set_fullscreen()
    def update(self, dt):
        pass
    def on_draw(self):
        pass
    def on_mouse_motion(self, x, y, dx, dy):
        pass
win = Window()
pyglet.app.run()

```
Does anyone know how I could maximise this?
The code is basically just an edited form of a previous game I made - it works, although I haven't tested this code snippet.

---

### Post by Pazaz on 2011-11-05
> **gameguy said:**
> I have a pyglet application that I would like to make fullscreen. This is the (shortened) code for it
```

class Window(pyglet.window.Window):
    def __init__(self):
        # Call the superclass's constructor.
        super(Window, self).__init__()
        self.keys = key.KeyStateHandler()
        self.push_handlers(self.keys)
        pyglet.clock.schedule_interval(self.update, 0.02)
        #self.set_fullscreen()
    def update(self, dt):
        pass
    def on_draw(self):
        pass
    def on_mouse_motion(self, x, y, dx, dy):
        pass
win = Window()
pyglet.app.run()

```
Does anyone know how I could maximise this?
The code is basically just an edited form of a previous game I made - it works, although I haven't tested this code snippet.

Try to look at [http://pyglet.org/doc/api/pyglet.window.Window-class.html](http://pyglet.org/doc/api/pyglet.window.Window-class.html) for info about the API in Pyglet.

EDIT----
You will find Fullscreen AND Maxmizing code on that page.

---

### Post by gameguy on 2011-11-06
I know how to go into fullscreen - I got that code from my previous game.
```

self.set_fullscreen() #works
self.maximise() #doesn't work

```
Do you know why? They use the same syntax, by the looks of it.

---


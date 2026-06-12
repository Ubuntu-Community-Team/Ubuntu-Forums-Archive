---
title: "Python, gtk and timers"
date: 2012-11-02
forum: Programming Talk
---

### Post by ways on 2012-11-02
I'm not new with Python, but I am new with gtk and window programming in python.

I have an application that should show a window, then close it after given amount of time. Here's a part of the code:

```

      window = MyWindow()
      window.set_size_request(200, 200)
      #window.fullscreen()
      webview = webkit.WebView()
      window.add(webview)
      window.show_all()
      window.connect("delete-event", gtk.main_quit)

      webview.load_uri(username)
      gtk.main()

```

```

class MyWindow(gtk.Window):

    def __init__(self):
        gtk.Window.__init__(self)
        self.connect('destroy', lambda wid: gtk.main_quit())
        self.connect('delete_event', self.delete_event)
        gobject.timeout_add_seconds(3, self.callback)

    def callback(self):
      time.sleep(3)
      print "timer done"
      self.quit(self)
      return False

    def quit(self, data=None):
      gtk.main_quit()
      self.destroy()

```

Now the window doesn't close, and I'm unsure how to use the timer (that explains the sleep). Any tips?

---


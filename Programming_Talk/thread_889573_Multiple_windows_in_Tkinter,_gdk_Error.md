---
title: "Multiple windows in Tkinter, gdk Error"
date: 2008-08-14
forum: Programming Talk
---

### Post by chrisN_uk on 2008-08-14
Hello, I'm having some trouble with getting Tkinter to initiate other types of window. Here's a code sample:
```

import Tkinter as tk
import visual

class App1:
	def __init__(self,master):
		new = tk.Toplevel()
		a = App2(new)
		new.mainloop()

class App2:
	def __init__(self,master):
		self.b = tk.Button(master,text = "Box",command = visual.box)
		self.b.pack()

root = tk.Tk()
a = App1(root)
root.mainloop()

```

When I run it and close the window with the button, the following error occurs: 

```

Gdk-ERROR **: BadWindow (invalid Window parameter)
  serial 309 error_code 3 request_code 15 minor_code 0

```

Then moving focus to the 'visual' window either creates this error or a seg fault:
```

Gdk-ERROR **: Fatal IO error 11 (Resource temporarily unavailable) on X server &#65533;g&#65533;8.

```

I'm guessing the 'visual' window has some sort of reference to the tkinter one that created it and when this is closed, the reference isn't valid. Any ideas how I can get around this?

---

